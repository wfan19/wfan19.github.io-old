---
layout: post
title:  "Implementing an Improved Blocking"
date:   2018-4-15
categories: Chrome_Extension Programming
tags: Chrome_Extension Programming HTML JavaScript
excerpt: Going from a basic "blocking through denying connection" to "'blocking' by turning the page blank".
mathjax: false
---

## Overall Tasks/roadmap for Pre-Alpha:
- [x] Block website by denying connection
- [x] Block website by removing the whole page's ```<body>```
- [ ] Block website only at certain times
- [ ] Be able to whitelist websites
- [ ] Be able to remove parts of the website (recomendation bar, etc)

I ended the last post with me implementing a very basic blocking that worked by straight up denying my connection to the blocked page. That sort of blocking was fairly far from my end goal of being able to remove *parts* of a page, however, so it wasn't very satisfactory. It also just didn't give much control to me as the developer. ***Also***, the code wasn't even mine...

Time for a new approach.

Since my plan is to be able to remove parts of the website by the end of the Pre-Alpha, the better way for me to approach website-blocking is for me to turn the page blank rather than just deny acces.

After some research on JS DOM,  it turns out that turning  the page blank, or even adding a sentence, is *really* easy. Like, three-lines-done-in-one-minute easy. Here's the code, what I had originally in ```content_script.js```:
``` javascript
window.addEventListener ("load", myMain, true);

function myMain(evt)
{
    document.body.innerHTML = "Go do your homework!";
}

```
And this code worked fine! Here it is in action:

![alt-text](https://thumbs.gfycat.com/BlandGrimyBackswimmer-size_restricted.gif)

This original stuff wasn't very satisfactory though... The font was tiny, and the words were backed into a corner. Overall, I just had no control over the text displayed.

Some more research later, I changed the JS injection to this:
``` javascript
window.addEventListener ("load", myMain, true);

function myMain(evt)
{
    document.body.innerHTML = "";
    var text = document.createElement("h");
    var tNode  = document.createTextNode("GO WORK"); //text will eventually be customizable
    text.appendChild(tNode);
    document.body.appendChild(text);
    text.style.fontSize = "60px";
    text.style.fontFamily = "Sans Serif"
}
```
Now, I was finally able to stylize the words displaye:

![alt-text](https://i.imgur.com/MtiHTnY.png)

What I did was that instead of simply altering the innerHTML of the ```<body>```, I appended a text node object. Now I can edit its style.

However, a problem that I still need to fix is to have the javascript injected at the **start** of the page load, rather than towards the end, like how it is right now. Using ```"run_at": "document_start",``` should have done it, but for some reason it's not working. I read through Google's documentation on the thing and it's not much help. I might have to resort to Stack Overflow.

