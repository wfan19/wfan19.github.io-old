---
layout: post
date:   2018-5-21
categories: Website
tags: HTML
excerpt: Updating the introduction on my home page.
mathjax: false
---
So, it's been a while since I've written something here. It's actually been more than a month since I've written anything about programming. Wow. Part of it has been AP season, which fortunately just ended. The other part of it was just me kinda forgetting about this website existed, while I still worked on my projects. Either way, I've built up some progress that I could write about, so here I am to write about them.

I've decided to start off with a post about the website, which I've updated recently.

The original jekyll theme that I got from HyG did not have any header info at all. After the top navigation bar, the front page went straight to the recent posts. 

>![alt-text](https://i.imgur.com/X2cIrch.png)

I didn't really like that, as it didn't offer much context to the projects that I was working on, so I decided to dig through the code to find the HTML file for the front page, which turned out to be ```index.html```. After playing around with it a little, I figured out how to put in a ```<div>``` with a placeholder header. [see image] <= the code for the lorem ipsum header.

Recently, I finally got around to replacing that placeholder header. I didn't want the header to be just a block of text like my placeholder was, so I went to a markdown to HTML convertor. I typed in my formatted text in the form of markdown, took the HTML, and replaced the placeholder text with it.

After running into some problems with the new HTML not being enclosed in a ```<div>```, I finally got it working. Here's the end result:
>![alt-text](https://i.imgur.com/3b42Ojj.png)

However, even though this works, there are huge gaps between the sections, and I'm not quite sure of how to fix that. I will look into it in the future.

