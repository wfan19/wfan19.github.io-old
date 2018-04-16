---
layout: post
title:  "I'm Going to Make a Chrome Extension!"
date:   2018-4-5
categories: Chrome_Extension Programming
tags: Chrome_Extension Programming
excerpt: The Chrome extension quest begins...
mathjax: true
---

I'm a borderline Youtube addict; The site's like a drug to me. I waste hours of time on it, mindlessly absorbing the videos. I blame Youtube's fantastic recommendation algorithm, and my choice of music. Whenever I'm supposed to be studying, I want to put on my study music, which is on Youtube. I open <https://www.youtube.com>, and before I can look up the music, I see something that interests me on the home page, and down the rabbit hole we go...

I tried a bunch of things to solve this problem, but I was always defeated by a combination of my weak willpower and just the inaptness of the solutions. One of the ideas that I tried was a website blocker. I wanted to be able to:

* Blacklist domains, but whitelist subdomains
	* Block Youtube, but allow for music
* Block websites on a schedule
* Restrict me from lifting the block early
* Hide Youtube recommendations

Unfortunately, no pre-existing website blocking extension had all the features I was looking for. For example, the most popular <http://blocksite.co> does not allow for whitelisting sub-domains. No blocking software had all for features. So then I thought to myself:

#### Why not write my own extension?

Some research and learning later, here I am. I've gone halfway through Google's introductory tutorial to extensions, but to be honest, it is a very crappy tutorial. It basically just goes "Here's the code. You write it and it does this thing. Then you add this code" ad infinitum. However, after playing around with the code they gave, and some html tutorials, I have learned quite a lot already.

## The Roadmap:
Currently, I plan to develop the extension in a few phases.
#### Pre-Alpha
The plan for the pre-alpha is to have the basic functionality down, without much UI. Most of my settings will probably be hard-coded in.

What I would need to learn:
* Chrome extension API
* JavaScript

I want to get all the functionality in ASAP since once this is done I should be much more productive, and so all the other versions, along with my other projects and schoolwork, will come along much faster.

#### Alpha
For the alpha version, I want to have the basic UI working, but without the CSS. Just the HTML.

What I would have to learn:
* HTML
* More of Chrome's API

Since the HTML and CSS components of the extension are fairly separate, I want to tackle them one at a time.

#### Beta
For the beta version, the goal is to have all the basics finished - JS, HTML, CSS. At the end of the Beta I want the extension to look like an unpolished product, but with all of its functionality built in. 

What I would have to learn:
* CSS

#### Version 1.0
1.0 will be the official release of the extension onto the Google extension store. Throughout 1.0 I hope to continually polish the extension, but overall the functionality shouldn't vary that much. 

## Overall Tasks/roadmap for Pre-Alpha:
- [ ] Block website by denying connection
- [ ] Block website by removing the whole page's ```<body>```
- [ ] Block website only at certain times
- [ ] Be able to whitelist websites
- [ ] Be able to remove parts of the website (recomendation bar, etc)