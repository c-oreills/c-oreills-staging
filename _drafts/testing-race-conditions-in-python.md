---
layout: post
---

You're working on a hot new startup, Incrmnt, which does one thing and does it well.

You display a global counter and a plus sign. Users can click the plus sign and the counter increases by one. It's so simple! It's so addictive! It's the next big thing for sure!

Investors are tripping over themselves to get on board but you have a problem.

## The race condition

During your private beta, Abraham and Belinda were so super excited that they each clicked the plus button 100 times each. Your server logs show 200 requests, but the counter only shows 173. Something doesn't add up.

Trying to push the headline "Incrmnt turns out to be Excrmnt" to the back of your mind, you inspect the code (all code used for this post can be found on [Github](https://github.com/c-oreills/c-oreills.github.io/blob/master/code/race_conditions)).

{% highlight python %}
# incrmnt.py
import db

def increment():
    count = db.get_count()

    new_count = count + 1
    db.set_count(new_count)

    return new_count
{% endhighlight %}

Your web server uses multiple processes to increase throughput, so this function can be running simultaneously in two different threads. If you're unlucky with the timing, this occurs:

{% highlight python %}
# Thread 1                          # Thread 2
def increment():
                                    def increment():
    # get_count returns 0
    count = db.get_count()
                                        # get_count returns 0 again
                                        count = db.get_count()
    new_count = count + 1
    # set_count called with 1
    db.set_count(new_count)
                                        new_count = count + 1
                                        # set_count called with 1 again
                                        db.set_count(new_count)
{% endhighlight %}

So although count should have been incremented twice, it's only gone up by 1.

You know you can fix this code to be thread safe, but before you do, you want to write a test to prove the race exists.

## Reproducing the race

Ideally our test should reproduce the scenario above as closely as possible. The key ingredient of the race is:

* Both get_count calls must be executed before both set_count calls, so that count has the same value in both threads.

It doesn't matter when the set_count calls are made, as long as they are both after the get_count calls.

For simplicity, let's try and reproduce this nested situation, where the entirety of Thread 2 is executed just after the first get_count call in Thread 1:

{% highlight python %}
# Thread 1                          # Thread 2
def increment():
    # get_count returns 0
    count = db.get_count()
                                    def increment():
                                        # get_count returns 0 again
                                        count = db.get_count()

                                        # set_count called with 1
                                        new_count = count + 1
                                        db.set_count(new_count)
    # set_count called with 1 again
    new_count = count + 1
    db.set_count(new_count)
{% endhighlight %}

before_after is a library that provides utilities to help reproduce this situation. It can insert arbitrary code before or after a function.

before_after relies on the [mock](https://pypi.python.org/pypi/mock) library to patch functions. If you're not familiar with mock then I suggest reading the [excellent docs](http://www.voidspace.org.uk/python/mock/). Of particular importance is [Where To Patch](http://www.voidspace.org.uk/python/mock/patch.html#where-to-patch).

We want to wait until just after Thread 1 has called get_count, then execute Thread 2 in its entirety, then resume execution of Thread 1

We can write the following test:

{% highlight python %}
# test_incrmnt.py

import unittest

import before_after

import db
import incrmnt

class TestIncrmnt(unittest.TestCase):
    def setUp(self):
        db.reset_db()

    def test_increment_race(self):
        # after a call to get_count, call increment
        with before_after.after('incrmnt.db.get_count', incrmnt.increment):
            # start off the race with a call to increment
            incrmnt.increment()

        count = db.get_count()
        self.assertEqual(count, 2)
{% endhighlight %}

We've used before_after's `after` context manager to insert another call to `increment` after the first `get_count` call.

By default, before_after only calls the after function once. This is useful in this particular situation, since otherwise we'd blow the stack (`increment` would call `get_count` which would chain a call to `increment` which would call `get_count`...).

This test fails, since `count` is equal to 1, not 2. Now we have a red test that reproduces our race condition, so let's work on fixing it.

## Preventing the race

We're going to mitigate the race using a simple lock. This is obviously not the ideal solution - we'd be better offloading the problem to our data store using atomic updates - but this approach allows better demonstration of before_after and its usefulness for testing multithreaded applications.

We add a new function to incrmnt.py:

{% highlight python %}
# incrmnt.py

def locking_increment():
    with db.get_lock():
        return increment()
{% endhighlight %}

This ensures that only one thread can read from and write to the counter at once. If one thread tries to get the lock while it's held by another, a CouldNotLock exception will be raised.

We can now add this test:

{% highlight python %}
# test_incrmnt.py

def test_locking_increment_race(self):
    def erroring_locking_increment():
        # Trying to get a lock when the other thread has it will cause a
        # CouldNotLock exception - catch it here or the test will fail
        with self.assertRaises(db.CouldNotLock):
            incrmnt.locking_increment()

    with before_after.after('incrmnt.db.get_count', erroring_locking_increment):
        incrmnt.locking_increment()

    count = db.get_count()
    self.assertEqual(count, 1)
{% endhighlight %}

Now only one thread can increment the counter at a time.

## Mitigating the race

We still have a problem here, in that if two requests collide in this way, one will not be registered. In order to mitigate this, we can retry the increment (using something like [funcy retry](http://funcy.readthedocs.org/en/stable/flow.html#retry) is a concise way of doing so):

{% highlight python %}
# incrmnt.py

def retrying_locking_increment():
    @retry(tries=5, errors=db.CouldNotLock)
    def _increment():
        return locking_increment()

    return _increment()
{% endhighlight %}

When we need more scale than this method provides, we can move the increment into our database as an atomic update or transaction, taking the responsibility away from our application.

## Conclusion

Incrmnt is now race free, and people can happily click all day long without worrying about not being counted.

This was a simple example, but before_after can be used in more complicated races to ensure that functions deal with the situation properly. Being able to test and reproduce in a single threaded environment is key to being more confident that you're handling your races properly.
