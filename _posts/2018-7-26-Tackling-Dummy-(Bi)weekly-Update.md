---
layout: post
-date:   2018-7-26
categories: Tackling_Dummy
tags: CAD Machining
excerpt: Hello and welcome to another (bi?)weekly update! This week there wasn't a lot of hardware progress, some software progress, and a _change of direction_. First, the goals from the last update:

That's all the progress I have for now! My plans for the upcoming weeks are as such:
- [x] Set up all effect controlled motors
- [ ] Work on localization by configuring IMU and GPS
- [x] Configure XBee communication between arduinos
- [ ] Drive motors with arduino
- [ ] Finish mold and cast the body
- [ ] Order the custom vinyl wrap for the drivetrain, along with the inflated top.

Wow! It seems like I didn't really get that much done, and that's kind of true. A lot of time was me being stuck on trying to iron out all the bugs of the XBee communication. There was just this endless stream of dumb problems, one after another. 
mathjax: true
---

Hello and welcome to another (bi?)weekly update! This week there wasn't a lot of hardware progress, some software progress, and a _change of direction_. First, the goals from the last update:

That's all the progress I have for now! My plans for the upcoming weeks are as such:
- [x] Set up all effect controlled motors
- [ ] Work on localization by configuring IMU and GPS
- [x] Configure XBee communication between arduinos
- [ ] Drive motors with arduino
- [ ] Finish mold and cast the body
- [ ] Order the custom vinyl wrap for the drivetrain, along with the inflated top.

Wow! It seems like I didn't really get that much done, and that's kind of true. A lot of time was me being stuck on trying to iron out all the bugs of the XBee communication. There was just this endless stream of dumb problems, one after another. 

## XBee:

>![alt-text](https://lh3.googleusercontent.com/Y-uDplOldSQcQDKdIJa_SuVr76OEyL25892dos60N4vnU1XaQUbu9_w2ZCVO_dOxvyRKZwWUtr0buluORhaqanQcO8sOHXP4svGyEtKaAQpvtvEF9lNU892KQ6xDKzmKRCsLL97Et1zh2jTwxGGYzmVdJOzUn9oysLEkGi2Mulu9yk2oB3YuQXc3u3b3h0Ytfdud_7vSnVjSSUdLZz1XsRL19ywzUUcLfZeApgRyenkxKD-jPgurkcWIriwqkwDouYgiFf2rsz7tAq8bGuR2zBJ0aUpPo-aa56ryWohF7q3bVZGj51k0seBUJ8FlP91ipOYXu6RzH1-RUK84iPvKlEwQEyg3s1RT49hbfovnC_g7GhXRZ3BtvPlZnNICzd2Ds6YC5zwzPVkCQVsK6WR3zwySnx2sE4eOHzhe9gG6NLGjTXa7Y1hC8idTN1jEH_xmg3eXm-bqrqGqGMPRs7P1hHpWV_t3mDRLRyBG-drK2LAX9nwb4ljNVTvhh42mmKvm3SEi9UToVJuSwJHC1MGCrJ6Ac5XfdWgc_5cuC9oP3HmjrLbbfPM-d58xD_YQnK57Qtt5DIyy6nb0MxP_fohR9yfYE8kX6wDYQ0UniZw=w1286-h964-no)
Since I was already on the topic of the XBee, why don't I start my talk of progress here. I ran into a ton of problems on my way here, too many to recount, in fact, so I won't go over all of them. Some of the the problems included:


- XBee's not pairing
- Arduino won't read the data
- Arduino's main loop randomly stops

Of these problems, I still haven't been able to fix the last one. For the set up, I had one arduino set up to receive PWMdata from a hobby RC receiver. That arduino (let's call it the TX arduino), then transmitts that PWM data to the receiving (RX) arduino. The problem with this was that while the TX arduino was trying to constantly transmit data, it would randomly stop, around once every twenty seconds. I set up an LED blink program in the background, and the LED would also freeze for a second or two. It's very strange and I still haven't been able to fix it yet.

## Driving Motors With Arduinos:
Another part of the control system is for me to drive the motors via a signal outputted from the arduino, instead of straight from the radio receiver. I initially planned to simply output a PWM signal from the adruino, straight to the analog input of the ESC's. However, upon doing some research, it seemed like most users of this ESC instead favored using the UART connector. They found that not only does this give better resolution, but you can also query more data from the arduino, such as motor rpm. The library that I used was [RollingGecko's VescUartControl](https://github.com/RollingGecko/VescUartControl). While the documentation  was fairly poor, I was able to figure out how to use the library by going through [one of his projects that used this library.](https://github.com/RollingGecko/ArduBoardControler) By the end, I was able to read data from the motor controller.

Reading the ESC data:
>![alt-text](https://thumbs.gfycat.com/SatisfiedAbsoluteItalianbrownbear-size_restricted.gif)

 However, I am still unable to write a desired RPM to the motor controller. I incorporated [this pull request](https://github.com/RollingGecko/VescUartControl/pull/9) that actually built a function for setting rpm's, and it was supposedly tested to work without problems, so I really don't know what I'm doing wrong. 

## The Motor Itself:
When I wrote the last update, the motor couldn't be controlled at low speeds while under load, due to the weak back-EMF signal. To remedy that, I ordered a pack of 6 pin JST connectors, so that I could hook up the hall sensors on the motor to the ESC.
>![alt-text](https://image.ibb.co/g4v5W8/We_Chat_Image_20180726170916.jpg)
Connected to the rainbow colored ribbon cable is the set of hall sensor connectors.

After I hooked up the hall sensor and configured it in BLDC-Tool, the drive became perfectly smooth at low speeds! Here's a comparision between hall-less and with-hall control:
>![alt-text](https://cdn.discordapp.com/attachments/371419363728687107/468616574710972419/unknown.png)
Left is hall-less and right is with-hall. 

## The Mold and Foam:
The nylon slabs arrived, and *man*, these things are **huge**!
>![alt-text](https://lh3.googleusercontent.com/s5dAbYM00rLgvkpFIRwWHdKW6VkMk7w7j_cvXn_6hV1N2JmbhcsLlUig2gBDvQokg1otgKInWZSUZKABRhQ2GreeEbMzGWvtL8kdesb1B05Li6Ef5e93htHusLM3IvfH4YV5-5gIzbTb50p4EXpIeyrM1YAtxT0oCdwlfCy7cM0zFHNL5DuYsjqd3OI0YjlWjcSirVWpcgPd3WZZ9Oxhu-qeox6-bEUABkCv08JRlliadO64Kv0zkQ1xFn7tUWdcuTflhcwbI-kD_zdstZpTh4oLmaN8nxBgccCZkYvW4ZReIqhrvGhJKRASuHTKOjAhZc3ktJTQrwdQRMarihTXiCTHyQhOdndfs_ElpU6DinKeyjCthzI-w9WJd5gOt1UdL4vUT7LFgQ90rfJN6aC_XafOlMzHunkwzvRRwv2YH-OV_iu_7OCgQk1u7jYlwYm3Gjyq2c0oqXv290VCi1sYHB_gatEw0Wp8zwapAhEuqSLIN74zSoQKmSJ4T3lXI7gKFz8s640NqpTDlWqHHC78GBT1tbGaIw9kM1LSSe_joDUhrMHXd9bFFG7UVAeMFIdXd2zQzxDKPHBgYKxhAq1lejuP0BIt88LHLHOtybM=w1287-h965-no)

They're still being machined, and the machining is set to finish next week. In the mean time, a sample of the molding foam arrived, and I decided to experiment with it by casting it in the lunch box. However, that did *not* end well:
>![alt-text](https://preview.ibb.co/hKuojT/We_Chat_Image_20180726173022.jpg)

The fact that I used *way* too much foam aside, I also didn't stir it very well. Normally, you're supposed to stir liquid A and liquid B together in a third cup, and then pour it into the mold. I tried to stir it directly inside the mold (the lunchbox), which was a lot harder. Thus, before I finished even stirring, the foam began to rise, and well, you know the rest... Because of this, I asked the manufacturer of the foam for the density after expansion, which he said is 40kg/m^3, which is equal to ~2.5pcf (pound per cubic foot). I then also measured the volume of the foam body in NX, which came out to be ~50L. 
>![alt-text](https://i.imgur.com/fvpr7J6.png)
Using all this, I was able to use SmoothOn's online foam calculator to calculate the amount of foam I'll need to cast the whole body, which came out to be ~6lbs. 

During my research, I also found that I could use an epoxy coating to harden the foam, which would make it more impact resistant.

## The "New Direction"
While reflecting on my progress for the past two weeks, I realized that I had spent way too much time on something that should have been very basic (smooth wireless communication between two arduinos). If I needed two weeks to get two arduinos to talk to each other somewhat successfully, it would probably take months for me to achieve the coordinate control (with motion profiling and spline fitting) that I wanted to have by the end of summer. Even though I was learning a lot, I simply do not have the time. Thus, I decided that I was going to put most of the arduino control stuff on the back burner, while I instead focus on less technical things like polish, aesthetics, the business side, and things like this blog :). This way, I can ensure that the product I deliver by the end of the summer is *polished* instead of rushed and unfinished, even if it means a sacrifice in usability.

## Conclusion:
That'll be all for what happened these past two weeks. As for my goals for the next:
- Set up UART *control* of motors, not just receiving telemetry
- Order the vinyl outer wrap and inflated top
- Cast the foam body