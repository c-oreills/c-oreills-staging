---
layout: post
title: "How to break into Software Development without a CompSci degree (part 1)"
---


I've had a couple of questions about this recently so rather than send the same email repeatedly I thought I'd lay out my thoughts here.

This advice is based on both my own personal experience as someone who started commercial Software Development without formal Computer Science training, as well as my professional opinions and experience of what to look for as a hiring manager.

This advice is fairly generalisable and encapsulates what I think is important regardless of degree (or lack of one) or previous work experience (including previous Software Development experience).

This is a fairly meaty topic so I’ve split into two posts:

* Part 1 - Build Something (this post)
* Part 2 - Interviewing (coming soon)

This post covers:

* TOC
{:toc}

# My Background

To start with, a brief overview of my background. If you're not interested, please [skip to the next section](#build-something) for the advice. I'm not advocating this as The Way to Break Into Software, I'm merely providing context. Let me be clear: these are not criteria to match or a set of steps to follow, they are simply my personal path.

I'm a Mathematics grad. I started playing with programming age 14<a id="footnote1-ref" href="#footnote1"><sup>1</sup></a>, mainly trying (and failing) to make games. I never got serious about programming until my last year of university, where I selected a software based final year project so that I had a sink or swim incentive to teach myself to code (it worked!).

I always knew programming was what I wanted to do, but picked a Maths degree because the subject interested me. I read (and re-read) [ESR's How to Become a Hacker](http://www.catb.org/esr/faqs/hacker-howto.html). I tried (and failed) to install Debian several times. I bemoaned my lack of a mentor<a id="footnote2-ref" href="#footnote2"><sup>2</sup></a> but didn't do anything to seek help or feedback.

After university I got a job in E-Learning in my old school. My remit was essentially "Do anything to enable teachers and students to use technology to aid learning". I did a huge array of things, including some programming in Flash/Actionscript (hint: don't do this).

My boss was really encouraging and awesome (thank you! =) and I convinced her it was a good idea to pay me extra to develop a web app on the side. I picked up Ruby on Rails and created an app our teachers could use to book IT rooms<a id="footnote3-ref" href="#footnote3"><sup>3</sup></a>. I managed to install and learn Ubuntu and deployed my app to a managed service.

Around this time I started getting serious at applying for programming jobs. After several failed attempts I started getting equally serious about interview prep. I took [Yegge's excellent advice](http://steve-yegge.blogspot.co.uk/2008/03/get-that-job-at-google.html), bought an algorithms textbook (Algorithm Design Manual ([UK](https://www.amazon.co.uk/gp/product/1848000693/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=1848000693&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/1848000693/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=1848000693&linkId=9abf45d0ecd1c1f34fe8d82a98e251d7))) and digested it over a few weeks of the summer holidays. I eventually managed to land a job at a small startup as the third engineer. Finally I was programming for a living! =)

Enough about me, herein begins the advice.

# Build Something

This is the single most important piece of advice. Maybe moreso for startups, but this will probably help you with BigCorp as well. You need to show that you are a self-starter, capable of learning things on your own, and don't need to sit and wait to be taught. Demonstrate that and any employer won't (or *shouldn't*, IMO) care about your credentials, previous experience, or when you started.

Don't get hung up on tools to start with. People will rave about Vim vs Emacs vs Sublime, Ubuntu vs Mac vs Windows, whatever. Programming using all of these things is possible<a id="footnote4-ref" href="#footnote4"><sup>4</sup></a>. You're going to have a steep learning curve just getting up to speed with programming. Do not try to optimise your tooling and environment too much (yet!).

There are plenty of excellent tutorials out there on getting started with programming. I'd recommend [Learn Python the Hard Way](https://learnpythonthehardway.org/) You can read the whole thing online for free, but if you find it useful/get a job because of it please consider buying a copy: Zed's put a lot of work into it. It will walk you through getting set up on Mac/Windows/Linux because - remember - it doesn't matter which one you're using (yet!). Python is a decent language that you can use professionally, is easy to learn due to its small vocabulary and most importantly has an interactive REPL which makes learning much easier since your feedback cycles are shorter ([ESR has more to say on this](http://www.catb.org/esr/faqs/hacker-howto.html#skills1)).

Once you've worked your way through that, choose a personal project and build it. You've learned how to accomplish some basic programming tasks, now learn how to translate a spec (albeit one that you're making up in your head) into working software.

## Choosing a Project

A common complaint is that people can't think of ideas. I know, cool ideas are hard. The thing is is, this is just something for your portfolio. It doesn't need to be the next Uber. If you really can't think of anything and are desperate, try to reimplement something you use (but go simple - you're not necessarily best placed to appreciate the technical complexity of something you're trying to copy just yet).

Depending on what interests you long term, you may want to pick a project that aligns with the tech your desired job will be using. I don't mean go look up companies and copy exactly what tech they're using (though that's not a completely terrible idea), I mean, if you want to work in the web space, make a web app. If you don't know where you want to work, web apps are a safe bet: most companies have *some* web component to them.

So, just pick something. Make a simple web app to track some aspect of your life or job. If you're using Python, don't start with Django, [start with Flask](http://flask.pocoo.org/docs/0.12/tutorial/) - it's simpler to get up and running and there's less of it to understand. [Django will give you lots for free](https://docs.djangoproject.com/en/1.10/py-modindex/), in Flask you'll have to work out how to build bells and whistles yourself - this is all good learning.

You can also contribute to others' projects - more on that [later](#get-feedback-optional)

It's a good idea to put your work online so that people can see the code you've written. Get yourself a [Github](https://www.github.com/) account and put your projects there. This has the advantage that you'll have to learn version control, which is really useful to know (see [later for why and learning tips](#version-control)).

## Deploy It (Optional)

This is not strictly necessary but it can be great to have a demoable version of your software online. For this you'll probably need two things - a platform and version control.

### Platform

OpenShift has a free option and a Flask [beginner's guide](https://blog.openshift.com/beginners-guide-to-writing-flask-apps-on-openshift/) and [tutorial](https://developers.openshift.com/languages/python/flask.html) that should get you up and running with deploying a Flask application. There are links at the end of the Tutorial around adding a database if your app requires one, or you can look at a [more involved blog guide](https://blog.openshift.com/build-your-app-on-openshift-using-flask-sqlalchemy-and-postgresql-92/). Note that the platform is based on RedHat, rather than Ubuntu/Debian, so ensure any Linux instructions you use are for RedHat.

Heroku is fairly easy to start with and has a decent free tier. Getting started with Flask is a little more involved (see [this project](https://github.com/zachwill/flask_heroku), be wary that the commands are only for Mac so you'll probably have to do more legwork for Linux/Windows), but the [Heroku Getting Started with Python article](https://devcenter.heroku.com/articles/getting-started-with-python#introduction) will walk you through getting a Django app set up if you chose to go that way.

### Version Control

Most platforms are going to want you to set up version control. Version control is a way of recording changes to a set of files, such that you can easily see what's changed between different iterations of software and go back to an old version if you need to. If you're going to be working on a software team, they'll be using version control (if they don't, run [run away very fast](https://www.steve.codes/blog/2016/7/22/an-updated-joel-test)). You can find some [basic git workflows here](http://git.huit.harvard.edu/guide/) with some links to further resources at the end. Git [mystifies a lot of people](https://xkcd.com/1597/) because it's essentially a [graph manipulation tool](http://think-like-a-git.net/sections/graphs-and-git.html) that stores files - but don't worry about that (yet!). You should be able to get along fine with the [above guide](http://git.huit.harvard.edu/guide/), the links at the end of it and/or some Googling of "[how do I x with git](https://www.google.co.uk/search?q=how+do+i+go+back+to+a+previous+version+using+git)" when you get stuck.

## Get Feedback (Optional)

Another optional step, but one that if employed successfully will accelerate your learning. Having other people critique your code will help you improve by exposing you to new ideas and having potential problems pointed out which you would never have noticed on your own.

The catch is, in order for someone to give you feedback, you're going to have to be giving back something in return. Ok, that's not strictly true, and if you go to a meetup I'm sure you'll be able to convince someone to review your code. But their generosity is only going to go so far.

Probably the easiest way of getting feedback is to try contributing to somebody's open source code. Most (sane) people will want to review any code you contribute before accepting it into their project. If your code doesn't make the cut, they're likely to tell you why and offer advice on what to change so they will accept it.

This can be a great exchange of value: you spend time [improving their project](https://jeffknupp.com/blog/2013/08/16/open-sourcing-a-python-project-the-right-way/), they spend time giving you feedback on what's acceptable and how you should improve, everybody wins. A particularly easy win can be adding tests to a project - lots of people don't like to spend time on tests for their pet projects since they make them feel too much like their day job.

Lots of mature open source projects (e.g. Django) may not have low hanging fruit left and can be large complex codebases which are hard to navigate for a beginner. If in doubt, try to join a project's forum or group chat and ask if there's anything simple which can be done by a beginner. Someone will probably oblige and point you in the right direction. If you can’t find where to ask, look for a "Contributing" section on the project homepage. If you're using GitHub, message the author and ask.

Another good idea can be going to meetups. [meetup.com](https://meetup.com/) should have a list of programming meetups in your area. Ask people what they're working on, ask if you can get involved. Pairing with someone in person can be an effective way of learning, and if you apply sustained effort to working on a project week after week, you're more likely to gain experience of different aspects of software development and project owners are more likely to invest time helping you out.

If you don't want to get into open source or go to meetups, you can also critique yourself. Doing exercises like [code katas](http://codekata.com/) will provide you what are essentially guided meditations on small code tasks, with the idea of improving your coding style and making you appreciate more concepts. These exercises are small enough to accomplish in one sitting and can be repeated multiple times so you can try different styles or ideas.

# Summary
The most important part of breaking into software is, IMO, being able to prove that you can build something. Hiring is always a risk for employers - we're making a decision based on a lot of unknowns, even with the best interview process in the world. So, be mindful of your potential employers and do everything you can to dispel that feeling of risk by showing what you're capable of.

Next time I'll talk more about choosing what companies to apply for, applying and interviewing. If you'd like to be informed when I post that update, you can [sign up for my mailing list below](#mc_embed_signup_scroll).

In the meantime, if you can build things and think you want to work for a London-based Python startup, [Conversocial is hiring](https://www.conversocial.com/careers/). Talk to me about what you've built! =)

# Footnotes
<a id="footnote1" href="#footnote1-ref">1</a>: There’s a romantic idea that all the best programmers [start young](https://xkcd.com/447/), but some of the best, most thoughtful programmers I know started long after university. Don’t worry that you’re too old to start. [Put in the hours](http://norvig.com/21-days.html) and you’ll be just as good as anyone else. [Age Discrimination](http://www.inc.com/suzanne-lucas/how-to-get-a-tech-job-when-youre-really-old-like-35.html) is unfortunately a real thing, but there’s also a [healthy backlash against it](https://qz.com/784118/someone-created-a-tech-job-board-for-people-over-30/) which is really encouraging.

<a id="footnote2" href="#footnote2-ref">2</a>: Don't do this: mentors, while extremely valuable, are few and far between - probably 9 in 10 people don't have one and get along fine, *you* are the biggest factor in your own success.

<a id="footnote3" href="#footnote3-ref">3</a>: I assume (read: really hope) that this system is long gone now. I handed it off to one of the IT staff who intended on learning how to program when I left: the only thing worse than being handed a system as a means to learn how to program is being handed a system created as a means of learning how to program as a means to learn how to program.

<a id="footnote4" href="#footnote4-ref">4</a>: Contrary to [ESR's advice](http://www.catb.org/esr/faqs/hacker-howto.html#skills2), programming on Windows isn't that bad - I started there, but I'm glad I eventually moved on. In Windows there's more effort getting a programming environment working and a lot of tools/tutorials assume you're using Mac or Linux.
