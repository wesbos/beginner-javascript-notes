---
attachments: [Clipboard_2020-02-06-07-17-14.png, Clipboard_2020-02-06-07-18-07.png, Clipboard_2020-02-06-07-20-49.png]
title: 'Module 4: The DOM - Working with HTML and CSS'
created: '2020-02-06T12:06:57.469Z'
modified: '2020-02-06T12:27:05.107Z'
---

# Module 4: The DOM - Working with HTML and CSS

## 20 - The DOM - Introduction to the document

So far, everything we have been learning has been javascript as part of hte core languages. Although Javascript can be run in many environments (browser, server, robots), a lot of places use javascript as a scripting environment. 

The most popular way to run javascript is through the web browser. A big part of working with javascript in the web browser is interacting with elements on a page. 

When you write html and view it in the browser, the browser turns your html into something that is called the **Document Object Model or the DOM**. 

That is what you see when you go to the elements panel in the developers tools on any webiste. It is not actually just the HTML that you have written, it takes that, converts it to the Document Object Model, and it allows us to interface with the DOM via javascript. 

We can do things like listen for clicks and scrolls. We can add, move, remove elements from that page or things like text, images, etc. 

we can add and remove css classes from elements which can trigger animations, we can fetch new data, we can play music and video, we can add any typoe of interaction to the page and that is done by writing javascript that interfaces with te DOM (the things that are on the page, the elements on the page).

The DOM is represented in a tree that looks veyr much like HTML. Even if you are using a framework like React, Angular or Vue, it's very helpful to undertsand that concepts of the DOM because the core concepts of the DOM like events, elements and classes, they transcend all of the different framesworsk. Even if the frameworks help you do these things, you still need to know how it works under the hood. 

Now, a quick refreshed on the window. In the scope video, we learned that the global scope in the browser is called the window. The window is where are our global variables are stored, as well as helpful properties like `window.location`. 

Aside: if you go to any website and in the console type in `window.location` or `location` it will return to you the websites url and a whole bunch of information. 

![](@attachment/Clipboard_2020-02-06-07-17-14.png)

There is an object full of information like the current page you're on, the host name, what hte protocol is, if we are on a specifc port it would be showing us that info. 

We can also find things like `innerWidth`, which will tell us how wide the browser is if you type it in the console. ![](@attachment/Clipboard_2020-02-06-07-18-07.png)

You can think of the window as everything about the currently opened window, including the browser bar, the tabs, the scroll bar, all of the things about your browser window is generally stored inside of the window object. 

Now we are going to introduce you to the Document.  The document is responsible for eveyrthing from the opening html tag, the doc type as well, to the closing html tag. The difference is the document is not concerned with tabs, and outside, it's just concerned with the entire DOM. The entire document will be available to us with the `document` keyword. 

If you type `document` into the console and hover over what it returns, you will see that it highlights the entire page: 

![](@attachment/Clipboard_2020-02-06-07-20-49.png) 

There is also something called the `navigator`. The `navigator` is sort of just a higher level thing than the window that gives you information not just about the browser, but the device itself, the device that it is on. Think about things like web cam and audio access, battery levle, GPS coordinates. Things that are device specific will live on the navigator. 

Right now you just need to know that there is the `window` which contains a lot of information about the browser but the document is going to contain everything about the current web page from the opening HTML to the closing HTML tag. 

In the next video we will get into selecting elements on the page. 

---
