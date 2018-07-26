---
layout: post
title:  "Figuring Out Options and Saving"
date:   2018-4-9
categories: Chrome_Extension
tags: HTML JavaScript
excerpt: Implementing a basic blocking  filter, and figuring out how option pages and saving options works.
mathjax: false
---

Since it's both a long weekend and the end of a quarter, I decided to get some work done on the extension today.
## Overall Tasks/roadmap for Pre-Alpha:
- [x] Block website by denying connection
- [ ] Block website by removing the whole page's ```<body>```
- [ ] Block website only at certain times
- [ ] Be able to whitelist websites
- [ ] Be able to remove parts of the website (recomendation bar, etc)

Alright, alright. So I didn't quitee follow my roadmap. What I should have done today was work on fully implementing the website blocking  code,but so far, all I have to show for that is some half-assed copy-pasted code from stack overflow...  
([This is the thread by the way](https://stackoverflow.com/questions/43889727/how-do-i-block-certain-websites-with-my-chrome-extension))  
Hey, at least I did get *some* work done though,  so it's better than usual.

Here's the blocking  in action: ![Alt Text](https://thumbs.gfycat.com/MedicalMajorBlackbuck-size_restricted.gif)

As you can see, even though I typed  in www.facebook.com, the browser would not take me there. While this is not quite the functionality I'm going for, it's a nice starting  point for someone who doesn't know Javascript.

While  I didn't quite follow the planned roadmap, what I did do was find out how setting pages worked with scripts, and how saving settings worked. I followed through Google's sample settings page, and after playing around with it a bit, figured out how the whole thing worked. After that, using what I had learned, I added a "Reset Settings" button. Here's the  thing in action:

![Alt Text](https://thumbs.gfycat.com/AgileWarpedBuffalo-size_restricted.gif)

As s you can see, I first changed color to blue and unchecked "I like colors". When I refresh the page,  the settings remain that way.  I then reset the settings, and after the page refreshed itself, the settings were restored to default.

My setting page isn't quite polished. For example, after I reset the settings, instead of forcing a page reset, what the page should do is just select the default  values on its own, without having  to refresh the page. Right now, it just looks clunky as hell.