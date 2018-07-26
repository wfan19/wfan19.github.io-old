---
layout: post
-date:   2018-7-13
categories: Tackling_Dummy
tags: CAD Machining
excerpt: Progress on tackling dummy from 6/8 to 7/13
mathjax: false
---

It's been quite a while since I last posted here, and that was partly because I have been working on the tackling dummy full time (nine to five) since school ended. 

Recently my dad suggested to me that I should write weekly progress reports to keep track of my, well, progress. I had been wanting to write something here about my progress for a while now anyways, so I went "well, why don't I write my weekly reports on my website/blog?", and so here we are. 

Anyways, at the end of school, this was the latest version of the CAD model I had: 
>![alt-text](https://image.ibb.co/kinLnT/2018_01_18_09_52_22_NX_11_MTD3_Asmbl_prt.png)

The main chassis:
>![alt-text](https://image.ibb.co/n5qUgo/2018_01_18_09_55_20_NX_11_MTD3_Asmbl_prt.png)

The side attachments:
>![alt-text](https://image.ibb.co/meCaMo/2018_01_18_09_55_37_NX_11_MTD3_Asmbl_prt.png)

This version of the model had a few problems. First of all, I did not have a solid plan for manufacturing the mounting brackets for the supporting idler wheels, seen in the picture at the bottom right of the chassis. Also, my plan for connecting the side attachments to the main chassis was hard to execute, as it involved drilling through holes in all the estrusions, and buying very long quick release pins.

After roughly a month of work, I am proud to say that I have alleviated all of those issues. For the supporting wheels, instead of attaching supporting brackets to the front/back, I have instead attached plates to the side, which support long axles that go from one side of the chassis to the other. This is what it looks like:
>![alt-text](https://i.imgur.com/3KWfFUe.png)
The purpose of the strange shape of the side brackets is to have four mounting holes while still making room for the vertical extrusion on the side attachments. This solution proved to work quite well during my testing.

## The Chassis

As the parts began to arrive for the dummy, I started to actually put it together. This was the dummy after all the hardware for the main chassis had arrived:

>![alt-text](https://lh3.googleusercontent.com/sDXLfZhaeV15UVADQSRgFr75OPyVKJbmhiQwKwkNK0PXsEqV9-lw8CFgTzu1Kp1nnhg6lPeIQNQxC2x5NHEcVZSzNAamTVGJBsM-bSsvXNVuLvJHuzirpzIel0dZPNE9lDdqQeWCzmwCoI_q47GuPOrcyajJJBlIz4858YLjiOS-ProJonYLIJw_HVfvVsT8GjoJo5tYjiLVNmdfdKkV0KoeUxugAjYKZCx6tr27q9EgtrFkKOpKciLgC5u3a_yHKremQsKEZ1MqRpr6lJLSpYQdPX908WHNlGqjb7AMXdDH7R5anjlXKkw-kmJT0_112nHEmTZu5T1MVC6liLw-ygNBI2MdBrH4Qyj9QeS7tUyeh4-HWFID90yvC7qdsJWD9cO0TlxQ61js4M2n9XxKy4zH5tyI3x-o9ysKVgu_KKIr6oAiq-3LHOjD3pg4DqcFLoMkhm5hVBVc0lLoMYA-38RBknqKWhwRxGx7kA_LEWMhPRAiynyyh2kWkiSvWij0Yvj_edFiug4PjNihWI3Lzur7kb0FaVsORSF1n30eYS4q6_CBdIV3_1UFmw5gFHSFRoMUR79uqnxZklkt_Qva9dIBCbKo5MRvX7NPCJY=w1286-h964-no)
The front and back supporting rollers initially had three rollers on each axle (two in the picture because I forgot one during assembly). However, the outer wheels would skid during turning, at least on the hard rubbery floor of the office. Thus, those wheels were removed, and turning was now much smoother.

After some more of the electronics hardware had arrived, I was finally able to test drive the chassis. However, I ran into a problem: at low speeds, the drive train would shake/jitter so much that it couldn't move. However, at high speeds, it drove very well. [See this video.](https://photos.app.goo.gl/9YuGBBc6BGeoNG7eA)

Since the chassis wasn't moving at low speeds, I hooked it up to my PC to test its rpms and such. This was the motor's RPM at a low speed:
>![alt-text](https://cdn.discordapp.com/attachments/434611927587487744/466075433331326986/unknown.png)
You can see that the motor was clearly jerking forward very roughly.

Because this was only a problem at low speeds, I figured that this had to be because of the hall-less control of the drive motors. BLDC motors can be controlled with or without hall sensors. When controlled without hall sensors, the controller relies on the back EMF of the motor to determine it's rpm. However, this back EMF signal is very weak when the motor is at low speeds. To solve this, I had to connect the motors' hall sensors to their respective controllers, and then configure the hall sensors in software.

>![alt-text](https://i.imgur.com/46GOQmC.png)
The configuration panel of the motor controllers.
 
## The Shell
Between working on the chassis of the dummy, I often had to wait for parts, such as Y cables or JST connectors. During that time, I worked on polishing the shell, or body, of the dummy. 

To begin with, I redesigned the shape.
>![alt-text](https://i.imgur.com/szMNbNH.png)
The redesigned outer shell is shorter, and its maximum radius is also lower. 

I also began to test my plan for making the body. My original plan was to have the body be cut out of foam. The foam had to be close cell, strong, but also rebounding. Thus, this narrowed my search down to pretty much just high density EPE - expanded polyethylene. Unfortunately, when I obtained a sample of said EPE, I found that it was not strong enough. Under medium pressures, the curved foam surface would flatten, which would greatly mess up the self righting capabilities of the dummy. 

Aside from the material, my original plan with EPE was also impossible to machine. The entire foam body is too big for most lathes to machine in one go. so it woudl have had to be made in two pieces. The center square hole would have then also required a mill. I originally planned to use a custom hot wire bent into the shape of the outter curvature. However, this solution was too janky. All this combined meant that I had to think of a different way. 

After much research, I stumbeled across [casting foam](https://www.youtube.com/watch?v=Dk1oN0y5Xiw&t=137s). Not only did casting foam alleviate the machining problem, as I could machine the mold piece by piece, but it also seemed like casting foam is very hard. Thus, I proceeded to CAD a mold:
>![alt-text](https://i.imgur.com/9dNCErd.png)
The green slabs are the main outer shell of the mold, to be machined out of nylon or delrin, or some other hard plastic. The red pieces are within the mold, there to form the cutout that would house the drive. The blue rods are axles used to hold the slabs together. I originally had a male-female sort of connection between the slabs, but those proved to be too much of a pain to machine. The slabs would also be held together by ratcheting straps.

## Conclusion:
That's all the progress I have for now! My plans for the upcoming weeks are as such:
- Set up hall effect controlled motors
- Work on localization by configuring IMU and GPS
- Configure XBee communication between arduinos
- Drive motors with arduino
- Finish mold and cast the body
- Order the custom vinyl wrap for the drivetrain, along with the inflated top.

:)

-Bill