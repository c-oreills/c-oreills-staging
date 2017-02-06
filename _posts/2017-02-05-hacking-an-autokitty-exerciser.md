---
layout: post
title: "Hacking an AutoKitty Exerciser"
---

***This post is still a Work In Progress***

This is a guide on setting up an automatic cat exerciser to exercise your kitties while you're out at work. Overall costs should not exceed £30/$40.

Jump to a section:

* TOC
{:toc}

## Background
Recently, our cats, Saga and Boo, have been causing a bit of havoc by bringing mice in from the garden:

![Abbie was traumatised by finding a mouse in her slipper](/images/autokitty/mousetrauma.png)

This morning I found Saga scampering around the kitchen with a live mouse in her jaws (luckily Abbie's away for the day!). He was tiny and cute and I rescued and released him at the end of the garden. He was in a state of shock but unmauled I have high hopes that he'll survive.

Dammit, halfway through writing this post it seems that hours later they've retrieved him from the garden! Poor little guy! =( I've named him Timmy. More on his fate at [the end of the post](#timmy).

![The Lion and the Mouse](/images/autokitty/sagamouse.jpg)
*The Lion and the Mouse* 
{:.caption}

I looked up [how to stop this happening](https://www.pet-happy.com/why-is-your-cat-bringing-mice-home/) and, not really wanting to get collars with bells, decided our cats need to get more exercise. They are very lazy and spend all day sitting on our bed or sofa.

Both Abbie and I are out all day at work, so I decided to automate!

## Equipment
![Sagawand]()
*We had already had a Motorised Cat Wand which Saga and Boo love.*
{:.caption}

* Motorised Cat Wand - [UK](https://www.amazon.co.uk/gp/product/B01EH6RDR0/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B01EH6RDR0&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/B01EH6RDR0/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B01EH6RDR0&linkId=8875599c24e3af0ab4c8a5f5c7e9afe1) *Full disclosure: affiliate links, [our version](https://www.amazon.co.uk/gp/product/B01A4QI5AG/ref=od_aui_detailpages00?ie=UTF8&psc=1) only has "random"*
* [Battery Eliminator - 3xAA](https://www.amazon.co.uk/gp/product/B01MAWHOPM/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B01MAWHOPM&linkCode=as2&tag=oreills-21) (UK) or [4.5V DC Power Supply](https://www.amazon.com/gp/product/B00KCPBEUI/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B00KCPBEUI&linkId=978ed505ef4cc11a047ff024a3b21271) (US)
* Mechanical Timer Plug - [UK](https://www.amazon.co.uk/gp/product/B00GP1RQVY/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B00GP1RQVY&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/B006LYHED0/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B006LYHED0&linkId=14abb99efafdf0bad4e9cf09c92b40d5)
* Small Screwdriver
* Scissors

## The Hack
There are two main parts to this hack:

* [Making the Wand Activate on Power](#activate-on-power)
* [Controlling the Power via Timer](#power-on-timer)

### Making the Wand Activate on Power {#activate-on-power}
![Stripped wand](/images/autokitty/start.jpg)
*A Naked Wand* 
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

*Disclaimer: I'm in no way qualified in electronics. My knowledge comes from physics at school 10 years ago, skimming one awesome book (Practical Electronics for Inventors: [UK](https://www.amazon.co.uk/gp/product/1259587541/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=1259587541&linkCode=as2&tag=oreills-21), [US](https://www.amazon.com/gp/product/1259587541/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=1259587541&linkId=c3fbf1d7cd20eb660066fc3eba0d6cda)), tinkering and Google. I'm fairly sure that nothing is going to go horribly wrong by modifying a 4.5V device in this way. **You are wholly responsible for any modifications you make!** UPDATE: My electrically savvy friend says this is probably fine.*

In retrospect, you can simplify this by just jamming something into the gray case such that the push button is always depressed. I started this hack with the idea of bypassing a capacitor to override the 15 minute timer - but altering to activate upon power on makes that unnecessary.

### Controlling the Power via Timer {#power-on-timer}
***I'm still waiting for my stuff to arrive, but here's my plans***

If you're playing along from the UK, this is simple, since you can buy [battery eliminators](https://www.amazon.co.uk/gp/product/B01MAWHOPM/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=B01MAWHOPM&linkCode=as2&tag=oreills-21) for cheap.

If you're in the US, for some reason, battery eliminators are [10 times more expensive](http://www.batteryeliminatorstore.com/index.php?id_product=40&controller=product) than the [4.5V DC Power Supply](https://www.amazon.com/gp/product/B00KCPBEUI/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=oreillsus-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B00KCPBEUI&linkId=978ed505ef4cc11a047ff024a3b21271) above. So, I'd suggest buying the Power Supply, cutting the end off, stripping the wires and attaching them to the first and last battery terminals. If the Wand doesn't power on, swap the wires around.

![Battery Eliminators](/images/autokitty/batteryeliminator.jpg)

*Eliminate your batteries and drill a cable hole*
{:.caption}

Either way, set up your preferred method of eliminating batteries. I made cardboard cutouts to turn my AA batteries into C sized batteries. I also drilled a hole in the bottom of my battery compartment so the cable could run out.

![Timer plug](/images/autokitty/timerplug.jpg)
*Set your timer to come on several times for 15 minutes*
{:.caption}

With that done, you just have to program and connect your timer plug. Remember that the Wand will automatically turn on when it gets power but will time out after ~15 mins - so there's no point in putting timer slots for more than 15 mins.


## Timmy the Mouse {#timmy}
![Timmy's tiny!](/images/autokitty/tinytimmy.jpg)
*Timmy is Tiny!*
{:.caption}

When I rescued Timmy he was fairly shaken up. He was also extremely tiny and scruffy. He trundled around the tupperware I put him in in a state of shock.

![Timmy's free!](/images/autokitty/timmyfree.jpg)
*Be free!*
{:.caption}

I drove him to a river a couple miles away and let him go in the grass. I now wish I'd giving him some food, but by this point he'd perked up a bit of his own accord. He hid under some clumps of grass. I hope he's doing ok and that the Saga trauma wasn't too much for him!

<!--
## TODO
* Gif of kitty wand
* Compress start jpg (and others?)
* Measure amperage draw
-->

<style>
.caption {
    text-align:center;
}
</style>
