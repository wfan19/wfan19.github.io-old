---
layout: post
title:  "Mobile Tackling Dummy - The Story so Far"
date:   2018-4-21
categories: Tackling_Dummy
tags: CAD
excerpt: A review of what I've done so far on the Mobile Tackling Dummy project. Part one of a two part series where I also look at my plan in the future.
mathjax: false
---

So far this blog/website has almost exclusively been about my Chrome extension project, which is actually kind of funny, since I originally made this site for my two main projects: my tackling dummy and CNC router. However, those two projects had been previously on hold, since my dummy's parts were missing, and I'm not sure if I even will be pursuing the router project, as it depends on if I will win a grant from my school or not.

Anyways, enough rambling. When spring break ended, I finally got my hub motors and ESC's, so now, after the giant brick of a 36v battery has been sitting in my room for two months, I can finally get to testing!

I did this whole job with soldering on bullet connectors today, and I was about to post this write-up here: 

>Originally, the connectors on my ESC and my motor were incompatible. The ESC uses 3.5mm bullet connectors, those standard on almost all RC ESC's. I don't know what the hub motor used. Today, I soldered on the bullet connectors. It was quite a learning experience, I had never soldered wires before - only PCB's.
>
>Here's a picture of the soldered connectors: ![alt-text](https://lh3.googleusercontent.com/HCnlAZbzZX3dk4xfdJnZdsmbAlsSjoK__8h5ob4dwFDSU_VrKPV8EpnItFR_kETkWbQqOg9ATxkaeXOZA76bVZGxyK7MZD4UXIA9u_E00nyMDNp4DMI5Ntyr_wAIByOfxf5zGcTvJE-CMoNTYnl46ulxZNhpPIgmXq6XGCl5IkirFSin8sikpBnwKhrO06YDaHD7GWfK7Zgt4V8Figf74ftJkAOFz7WV5-CZhGHatFZoIT96m_LCEzONZ9EmO77Ai4IgoIjfEtR2Z3bNm-_l2LSL_XQCgpMrZMRsjmolxiMuz26ULkX703c90fEM_tmFjKJEdNM0noYa4zOH9ISA7yHQizDAl-O0_58dNhNn_IYVRr1b80vbHoG-gLsf0gkmvw74Sw2Q0n-0zIDvyzO_hSkuYoZCGFzh0W7dIPodQW8Fbh6wlTql5Hm0IkqfZRr8GHaQttBPzRzUmmK_LibPxLbotFuyjAetqP-Zx7Gs0bvru-orvhiOpn6z8nmSuok10zcqBUYbqdUGVPik9K93ryP7k3wvlDpCJRq4D919L4h_WQxJbN15tMWznsNDqKt673UMuw0qgSD2bWRVJNmIFB6kVreWRuQ7-D87UP8=w949-h713-no)

But then I realized: Nobody reading this would have any context! "What is this hub motor for?" "Why are you using a 36v battery?" "What even *is* this mobile tackling dummy project?". So I think I'm going to give a little background on the project.

At the beginning of the 2016-2017 school year, our school asked the robotics club if we could make them a Mobile Tacking dummy, much like [the one Dartmouth made.](https://youtu.be/91vgE_ujVHM). Our robotics program manager put together a team of rookies to work on the project, but after putting together an extremely basic drivetrain that was way too big, they lost interest. After my robotics season ended, looking for something to work on, I picked up the project.

# V1

First, I had to figure out how to get the dummy to self balance

My initial idea was to improve upon the Dartmouth version by making it omnidirectional. I planned to do this by implementing what is known in competition robotics as a "Swerve Drive", where you can pivot the direction of each wheel.

>![alt-text](https://www.chiefdelphi.com/media/img/f4b/f4bab1ed34d518a739e64f81ce1613aa_l.jpg)
>Swerve drive

Competition robots usually use four of these "modules", although three is also ok (148 won worlds in 2009 with three module swerve). I planned to use just one module paired with idler omnidirectional-wheels, as that would minimize complexity. Usually, using just one module isn't ok, as then the robot wouldn't be able to rotate, but since the tackling dummy doesn't have a definitive "front", it was fine.

That proved to be too complex, and so I decided to move to something simpler. Instead, I decided to just use the most basic six wheel "west coast" drive, where the center two wheels are driven, and the four wheels in the "corners" are idling. I eventually settled on driving the 8 inch wheels each with a 24v dc motor.

As for the frame, I decided to use something similar to an aircraft's space-frame, with interlocking rings and ribs. I thought it'd work perfectly for the hemispherical-frustum shape. This ultimately lead to something like this:

insert pic here

As summer was about to end, I finalized my CAD model and got the pieces laser cut with acrylic as a prototype. This is what it looked like:

insert pic here

At the end of the design cycle, it was clear that the design had much to be desired for. The design was excessively large, hard to manufacture, ridiculously heavy, somewhat dangerous, and space-inefficient. The frame was to be made entirely of 1/4" Aluminum cutouts, and because of the placement of the DC motors, the radius of the bot also had to be very large. That was why I decided to redesign completely.

# V2
V2 goals:
- Have an easily attached soft outer shell
- Have minimal metal framing
- Use hub motors
- Easy to prototype and manufacture

At first, this set of goals left me scratching my head. However, while doing my research, I stumbled across this picture:

![alt-text](https://media.consumeraffairs.com/files/cache/news/Dartmouth_mobile_tackling_dummy_biggreenblogalert.blogspot_large.jpg)
Pardon the low quality...

The picture showcased the original version of the Mobile Virtual Player, the one by Dartmouth, when they still wanted to use a ball drive, also to achieve Omni-directional movement. What really sparked my idea was the fact that it seemed like this design had its minimalistic frame embedded *into* the foam. This meant that the frame itself did not need to have the round shape needed for self-balancing.

It was this revelation that eventually lead to my current design, with an aluminum extrusion frame and foam outer shell.

[insert picture of current CAD]

I can't wait to put this thing together once school ends!        