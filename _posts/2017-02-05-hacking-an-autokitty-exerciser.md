---
layout: post
title: "Hacking an AutoKitty Exerciser"
image: /images/autokitty/sagamouse.jpg
---

This is a guide on setting up an automatic cat exerciser to stimulate your kitties while you're out at work. Overall costs should not exceed £30/$40.

Jump to a section:

* TOC
{:toc}

## Background
Recently our cats, Saga and Boo, have been causing havoc by bringing mice in from the garden:

![Abbie was traumatised by finding a mouse in her slipper](/images/autokitty/mousetrauma.png)

This morning I found Saga scampering around the kitchen with a live mouse in her jaws (luckily Abbie's away for the day!). He was tiny and cute and I rescued and released him at the end of the garden. He was in a state of shock but unmauled and I have high hopes that he'll survive.

Dammit, hours later, halfway through writing this post they've retrieved him from the garden! Poor little guy! =( I've named him Timmy. More on his fate at [the end of the post](#timmy).

![The Lion and the Mouse](/images/autokitty/sagamouse.jpg)
*The Lion and the Mouse* 
{:.caption}

I looked up [how to stop this happening](https://www.pet-happy.com/why-is-your-cat-bringing-mice-home/) and, not really wanting to get collars with bells, decided our cats need more stimulation of their hunting instincts. They're both extremely lazy and spend all day sitting around, so the exercise will do them good.

![Saga and Boo are lazy](/images/autokitty/catyinyang.jpg)
*Saga and Boo spend most days living life at a breakneck pace*
{:.caption}

Both Abbie and I are out all day at work, so I decided to automate!

## Equipment
![Saga loves the wand](/images/autokitty/sagawand.5fps.gif)
{:.caption}

*We had already had a motorised cat wand which Saga and Boo love.*
{:.caption}

* **Motorised Cat Wand** - [UK](https://www.amazon.co.uk/gp/product/B01EH6RDR0/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B01EH6RDR0&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/B01EH6RDR0/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B01EH6RDR0&linkId=8875599c24e3af0ab4c8a5f5c7e9afe1) *Full disclosure: affiliate links, [our version](https://www.amazon.co.uk/gp/product/B01A4QI5AG/ref=od_aui_detailpages00?ie=UTF8&psc=1) only has "random" setting*
* [**Battery Eliminator** - 3xAA](https://www.amazon.co.uk/gp/product/B01MAWHOPM/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B01MAWHOPM&linkCode=as2&tag=oreills-21) (UK) *or* **4.5V DC Power Supply** ([UK](https://www.amazon.co.uk/gp/product/B0012Y2NMG/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B0012Y2NMG&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/B00KCPBEUI/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B00KCPBEUI&linkId=978ed505ef4cc11a047ff024a3b21271))
* **Mechanical Timer Plug** - [UK](https://www.amazon.co.uk/gp/product/B00GP1RQVY/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B00GP1RQVY&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/B006LYHED0/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B006LYHED0&linkId=14abb99efafdf0bad4e9cf09c92b40d5)
* **Small Screwdriver**
* **Scissors**
* **Sturdy Cardboard** (I used my Amazon parcel packaging)
* **Sharp knife/saw/drill** (for cutting hole in battery compartment)

## The Hack
There are three main parts to this hack:

* [Making the Wand Activate on Power](#activate-on-power)
* [Controlling the Power via Timer](#power-on-timer)
* [Making the Wire Cat Safe](#wire-cat-safe)

### Making the Wand Activate on Power {#activate-on-power}
![Stripped wand](/images/autokitty/start.jpg)
*A naked wand* 
{:.caption}
Start with your wand stripped of the skirt. Remove the batteries.

![Push button](/images/autokitty/pushbutton.jpg)
*Do not push* 
{:.caption}

Once you remove the top circle (twist it off firmly: it's not a screw but it's tight) you'll find a push button switch.

The button activates the wand for about 15 minutes by shorting the red and white wires soldered underneath it.

![Strip and twist the wires together to permanently short them](/images/autokitty/wiresshorted.jpg)
*Strip and twist the wires together to permanently short them*
{:.caption}

Unscrew the button, cut and strip the wires and twist them together to permanently short them.

*Disclaimer: I'm in no way qualified in electronics. My knowledge comes from physics at school a decade ago (I got an A!), skimming one awesome book (Practical Electronics for Inventors: [UK](https://www.amazon.co.uk/gp/product/1259587541/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=1259587541&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/1259587541/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=1259587541&linkId=c3fbf1d7cd20eb660066fc3eba0d6cda)), tinkering and Google. I'm fairly sure that nothing is going to go horribly wrong by modifying a 4.5V device in this way. **You are wholly responsible for any modifications you make!** UPDATE: My electrically savvy friends say this is fine.*

In retrospect, you can simplify this by just jamming something into the gray case such that the push button is always depressed. I started this hack with the idea of bypassing a capacitor to override the 15 minute timer - but altering to activate upon power on makes that unnecessary.

### Controlling the Power via Timer {#power-on-timer}

If you're playing along from the UK, this is simple, since you can buy [battery eliminators](https://www.amazon.co.uk/gp/product/B01MAWHOPM/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B01MAWHOPM&linkCode=as2&tag=oreills-21) for cheap.

If you're in the US, for some reason, battery eliminators are [10 times more expensive](http://www.batteryeliminatorstore.com/index.php?id_product=40&controller=product) than the [4.5V DC Power Supply](https://www.amazon.com/gp/product/B00KCPBEUI/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B00KCPBEUI&linkId=978ed505ef4cc11a047ff024a3b21271) above. So, I'd suggest buying the Power Supply, cutting the end off, stripping the wires and attaching them to the first and last battery terminals. If the wand doesn't power on, swap the wires around.

*I've actually ordered a similar power supply so I can be absolutely sure this works, so I'll update this when it arrives. In essence, my battery eliminator is doing exactly this, just with a battery shaped plug at the end.*

*Note: if you're using a Power Supply that is not linked above you'll need a **minimum 0.4 Amp DC Power Supply to be safe**. I measured my wand using batteries and a multimeter and it required ~0.3A to run. So, to be safe, buy a power supply that can output at least 0.4A. **Not doing so may make your power supply overheat and cause a fire**. The linked Power Supplies both output at least 0.5A.*

![Battery Eliminators](/images/autokitty/batteryeliminator.jpg)

*Eliminate your batteries!*
{:.caption}

Either way, set up your preferred method of eliminating batteries. I put my fake AA batteries into the compartment - technically I should be using C sized battery sheaths but the springs hold them fine.

![Timer plug](/images/autokitty/timerplug.jpg)
*Set your timer to come on several times for 15 minutes*
{:.caption}

With that done, you just have to program and connect your timer plug. Remember that the wand will automatically turn on when it gets power but will time out after ~15 mins - so there's no point in putting timer slots for more than 15 consecutive minutes.

I set my timer to come on once an hour for 15 minute intervals while we were out in the day. In the evening, we want the cats on our laps, so there will be no automatic wand distracting them. =)

### Making the Wire Cat Safe {#wire-cat-safe}

![Wire hole and cardboard cover](/images/autokitty/drillholeandcardboard.jpg)
*Cut a small hole for the wire, and cut and slip cardboard over the feet*
{:.caption}

Since your cats are going to be crazily clawing at the fake mouse on this magical device, you need to ensure the wire is cat-proof. This amount of electricity won't harm them if they slash the wire in two, but that may short the wires, potentially making your power supply overheat and causing a fire.

I cut a small slot in the battery shield with a hacksaw to allow the wire to pass through. I then cut sturdy cardboard to the right shape to fit around the feet and battery compartment and slotted it over. You may want to tape it to secure it further.

![Saga and Boo playing with the finished wand](/images/autokitty/sagabooplaying.jpg)
*Saga and Boo are keen to play with the now cat-proof auto-wand*
{:.caption}

My cardboard cover was long enough that it cleared the chief clawing area: the radius of the wand's skirt, where the fake mouse runs. I cut a little slot in the far end to hold the wire securely while the cats play with the wand.

That's it! You now have an automatically activated cat wand that will satisfy your cats' hunting instincts while you're out at work and hopefully give them some exercise in the process. =)

## Timmy the Mouse {#timmy}
![Timmy's tiny!](/images/autokitty/tinytimmy.jpg)
*Timmy is tiny! 50 pence piece both for scale and as a payoff to prevent any lawsuits*
{:.caption}

Back to the little guy who I rescued from our crazy huntress.

When I rescued Timmy he was fairly shaken up. He was also extremely tiny and scruffy. He trundled around the tupperware box I put him in in a state of shock.

![Timmy's free!](/images/autokitty/timmyfree.jpg)
*Be free!*
{:.caption}

I drove him to a river a couple miles away and set him free. I now wish I'd given him some food, but by this point he'd perked up a bit of his own accord. He hid under some clumps of grass. I hope he's doing ok and that the Saga trauma wasn't too much for him!

Hopefully the cats now get all their hunting urges out in a way that causes less mouse-trauma and Abbie-trauma in future.

<style>
.caption {
    text-align:center;
}
</style>
