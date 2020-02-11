---
attachments: [Clipboard_2020-02-06-07-17-14.png, Clipboard_2020-02-06-07-18-07.png, Clipboard_2020-02-06-07-20-49.png, Clipboard_2020-02-06-19-10-10.png, Clipboard_2020-02-06-19-11-24.png, Clipboard_2020-02-10-21-17-14.png, Clipboard_2020-02-10-21-20-05.png, Clipboard_2020-02-10-21-22-12.png, Clipboard_2020-02-10-21-30-10.png]
title: 'Module 4: The DOM - Working with HTML and CSS'
created: '2020-02-06T12:06:57.469Z'
modified: '2020-02-11T02:43:02.342Z'
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

## 21 - The DOM - Selecting Elements

 For this excercise, go into the `/excercises` folder, and you will see folder named `20 - The-DOM` which Wes has already created for us. Within that folder there are two files: an `index.html` and `the-dom.js` (the javascript file should be empty). You can open up `index.html` in the browser. 

First thing we need to talk about is where to load our javascript if we are selecting elements. 

To demonstrate this, we are going to jump ahead of ourselves briefly and grab an element from the page. 

Add the following the the javascript file: 

```js
const p = document.querySelector('p');
console.log(p);
```

If you wanted to load this javascript into the `index.html`, you might think you want to add it inside of the head tag, like so:

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <title>The DOM</title>
  <link rel="stylesheet" href="../../base.css">
  <script src="./the-dom.js"></script>
</head>
```

If we reload the page, when the page runs, it will run the Javascript for us. Open up dev tools and you will see null returned. 

![](@attachment/Clipboard_2020-02-06-19-10-10.png)

We are trying to select something on the page and then `console.log()` it. If you try to run `document.querySelector('p')` in the console, it will return an element like so: 


![](@attachment/Clipboard_2020-02-06-19-11-24.png)

Why does it work in the console, but not when we loaded it via javascript?
Because the javascript is being loaded before our html is created and what is happening is the javascript is downloaded and run before the actual elements have bene created on the page. 

There are ways to get around like (such as async and defer attributes), but it's better to just put the script tag right before the closing body tag. What that will do is ensure that all your HTML is first downloaded and parsed to the page before the javascript is run.   

If you move your script tag to right before the closing body tag and refresh the page, you will see the exact same code works.

There are ways around it, like putting all the javascript code inside of a function and then adding an event listener that listens for the DOM content loaded event and runs the `init()` function we created when that happens:

```
function init(){
  const p = document.querySelector('p');
  console.log(p);
}
document.addEventListener('DOMContentLoaded', init);
 ```

Move the script src back inside the `<head>` tag. 

This is getting ahead of ourselves but if you refresh the page, you will see that it works now even though the script is in the head. What we are doing is delaying the code that actually runs until all of the DOM content has been loaded to the page. 

If you move the script src back to right before the closing body tag, you will see that it still works. 


It's easier to not need to use an event listener like that and just include the script tag before the closing body tag so that is what we will be doing!

**Selecting DOM Elements**

Before you actually work with elements on the page, you will need to go get them, which we call selecting hem. You need to be able to access the specific element on the page (whether an h2 tag, div, button, image) and then once we have it we can do things like listen for clicks, change the content, add content to it. 

There are sort of two main ways of selecting elements, and these are the only two that Wes uses, and those are `querySelector()` and `querySelectorAll()`. Generally you are using them on the `document.` although that is not always the case.

```
const p = document.querySelector("p");
console.log(p);
```

In this example we have selected something with a p. 

`querySelector()` and `querySelectorAll()` take one argument and that is the CSS selector. Those are almost the exact same selectors that you know and love from CSS will be moved over to Javascript selector. 

![](@attachment/Clipboard_2020-02-10-21-17-14.png)

If you open up the `index.html` page, you will see we have grabbed a paragraph tag. When we console.log it, you will see we have the item there. 

`querySelectorAll()` will give you multiple elements, where `querySelector()` will give you the first matching one. 

If we make another variable called divs like so:

```
const p = document.querySelector("p");
const divs = document.querySelectorAll("div");
console.log(p);
console.log(divs);
```

If you reload `index.html` you will see that we get something in the console called a NodeList. 

![](@attachment/Clipboard_2020-02-10-21-20-05.png)

We will be learning about arrays in the future and NodeLists look a lot like arrays. This is kind of like an interview question that you might hear that a node list is not an array. It is a list of things, but there are a few differences which we will go through the differences. The short and skinny is that it does not have all the methods that an array does like map, filter and reduce built into it. 

If you hover over the NodeList in the console, you will see that it is grabbing everything that matches the selector (div). 

![](@attachment/Clipboard_2020-02-10-21-22-12.png)

You can get more specifc than using elements as selectors. You could say give me anything with a class of `.item` : `document.querySelectorAll('.item');`. Let's say you only wanted divs with a class of item, you would use `document.querySelectorAll("div.item");`.

You can do parent child selectors. Let's say we only wanted to grab an image inside of an `item` div. You would do that like so `const divs = document.querySelectorALl('.item img');` 

Let's say you wanted to just select the first item and then the image inside of it, you could do `document.querySelector('.item img')` instead. That will return the first match. 

Or let's say the other item div also has a class of item2.  You could do `const item2 = document.querySeletor('.item2');` Now if you want to search inside of an element that you already have, you can use querySelector on any other element like so:

```
const item2Image = item2.querySelector('img');
```

![](@attachment/Clipboard_2020-02-10-21-30-10.png)

If you ever need to narrow down your focus as to where you are searching, you can do that in your selector, but you can also run `querySelector()` and `querySelectorAll()` on any other elemen and only search within it to limit the scope. 

If you have an element with an id such as `<h2 id="wes">Sub Div</h1>`, you would be able to grab it using `document.getElementById('wes');`. Notice how you don't put the `#` sign before wes? That is because if you're using anything that's not query selector, you don't have to pass `.` or `#`. The same works with `document.getElementsByClassName()`, but you don't pass the `.` from the classname. 

You can get all the work done with `document.querySelector()` and `document.querySelectorAll()` however and they are much more flexible. 
---


