---
attachments: [Clipboard_2020-02-06-07-17-14.png, Clipboard_2020-02-06-07-18-07.png, Clipboard_2020-02-06-07-20-49.png, Clipboard_2020-02-06-19-10-10.png, Clipboard_2020-02-06-19-11-24.png, Clipboard_2020-02-10-21-17-14.png, Clipboard_2020-02-10-21-20-05.png, Clipboard_2020-02-10-21-22-12.png, Clipboard_2020-02-10-21-30-10.png, Clipboard_2020-02-19-07-40-26.png, Clipboard_2020-02-19-07-42-02.png, Clipboard_2020-02-19-07-42-42.png, Clipboard_2020-02-19-15-49-31.png, Clipboard_2020-02-19-15-50-11.png, Clipboard_2020-02-19-15-51-27.png, Clipboard_2020-02-19-15-54-21.png, Clipboard_2020-02-19-16-03-58.png, Clipboard_2020-02-19-16-04-54.png, Clipboard_2020-02-19-16-05-33.png, Clipboard_2020-02-19-16-06-03.png, Clipboard_2020-02-20-08-35-45.png, Clipboard_2020-02-20-08-37-54.png]
title: 'Module 4: The DOM - Working with HTML and CSS'
created: '2020-02-06T12:06:57.469Z'
modified: '2020-02-20T13:55:47.233Z'
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

# 22 - The DOM - Element Properties and Methods 

Now that we have learned how to grab/select an element, let's discuss what you can do with it. 

Let's select an h2 element from the page and console log it. 

![](@attachment/Clipboard_2020-02-13-19-04-56.png)

Although in the console it looks like the `heading` variable is the actual element, in reality it is an object that has a lot of properties and methods inside of it. If we change the `console.log()` to a `console.dir()`, that will show us the object properties instead of the actual element itself. 

![](@attachment/Clipboard_2020-02-13-19-07-45.png)

It's still the same h2 tag, but you can see all the properties on it. One example of that is `parentElement` which shows you what the parent element is. There is `outerText` `textContent` `outerHTML`, and many other properties. 

![](@attachment/Clipboard_2020-02-13-19-08-37.png)

We can use those properties as getters to get the data from the element that we need, or we can use them as setters. We will demontsrate this using `textContent`. 

```
const heading = document.querySelector('h2');
console.dir(heading.textContent);
```

![](@attachment/Clipboard_2020-02-13-19-11-38.png) 

That is an example of a getter. 

A setter is when you update the property. An example of that would be `heading.textContent = 'Wes is cool';`. Now when you reload the page, you will see Wes is cool in the console.

`textContent` and `innerText` are very similar properties, `textContent` is the newer one. The only difference is that innerText returns only the human readable content whereas textContent will get the contents of all of the elements, including script and style elements. 

So if your h2 looked like the following for some reason:

```
<h2>
I am a heading
<style>
  h2 {
    color:red;
  }
</style>
</h2>
```

If you log both the `heading.textContent` and `heading.innerText`, you will see that textContent includes the content within the style tag whereas innerText only returns the text `I am a heading`. 

![](@attachment/Clipboard_2020-02-13-19-20-42.png)

Content returns every element in the node whereas innerText is aware of styling and won't return text of hidden elements. 


Let's say you have the following code: 

```
<h2>
I am a heading!
<span>I am hiddden!</span>
</h2>
<style>
  h2 span {
    display: none
  }
</style>

```

`textContent` will return the "I am hidden!" text, however `innerText` will not. 

![](@attachment/Clipboard_2020-02-19-07-40-26.png)

We have a set of properties whne working with HTML. If we were to console.log the `innerHTML` of `heading`, you would see 

![](@attachment/Clipboard_2020-02-19-07-42-02.png)

There is also `outerHTML`, which should include the h2 tag and whitespace that goes inside of it. 

![](@attachment/Clipboard_2020-02-19-07-42-42.png)

If you ever want to add text onto something is another useful thing to lean. Go to `index.html` and modify the code like so:

 ```
 
  <article class="item">
      <h2>Im an article</h2>
      <p class="pizza">This is how many pizzas I ate! 🍕</p>
    </article>
 ```

 What we are going to do is build something to add more pizza emojis to the end of it. 

 First we need to select it, so 
 
 ```
 const pizzaList = document.querySelector('.pizza');
 console.log(pizzaList.textContent);
```

If we wanted to update textContent we could do something like

```
pizzaList.textContent = `${pizzaList.textContent} 🍕`;
```

So that takes what was already there and it adds an emoji to the end. 

That method can be slow in some applications that have lots of text and html. That causes the browser to re-render the entire list so we what you can do is tack text onto the end using another method called insert adjacent element or insert adjacent text. That will give us the ability to add stuff to the front or back of it. 

```
pizzaList.insertAdjacentText()
```

If you go to mdn and search for `insertAdjacentText()` you will see that it is not a property, it is a method, meaning it is a  function that we run against the element (much like querySelector and querySelectorAll). It takes two arguments: the position (beforebegin, afterbegin, beforeend, afterend), and the text that you want to pass it. Mdn says the second argument is element but it's actually just the raw text you want to add. 

add the following:

```
pizzaList.insertAdjacentText('beforeend','🍕');
```

If you refresh index.html you will see two pizza emojis now. 

It works the same as the other way we tried earlier, however you should know that this is the best way to attach text to the end of something. 

If you were to try 

```
pizzaList.insertAdjacentText('beforebegin','🍕');
```

![](@attachment/Clipboard_2020-02-19-15-49-31.png)

That will put the pizza emoji before the paragraph entirely, it's not inside of that element. We would want `afterbegin` to add the pizza in front of the text

![](@attachment/Clipboard_2020-02-19-15-50-11.png)

The browser actually knows that the pizza emoji was added later, because the text is split up between what we used to have an what we inserted:
![](@attachment/Clipboard_2020-02-19-15-51-27.png)

That is actually the difference between elements and nodes. Nodes can be anything, but an actual element is something that is wrapped in a tag. It is a little bit confusing because everything is a node, and it only upgrade sitself to an element if you have wrapped it in a tag. 

If you are wondering what all the possible ones are, we can stumble upon different properties and methods as we build out our excercises. You can go to the MDN docs and go to element, it will tell us what all the properties are of elements. 

![](@attachment/Clipboard_2020-02-19-15-54-21.png)

That is elements, both how to get properties from an element, how to set properties on an element and how to use more powerful methods on each of our elements or nodes. 

---

## 23 - The DOM - Working with Classes

Another thing that is commonly done in javascript is the adding or removing of classes. That is done a little different than  using properties like we have used so far. 

Comment out everything in `the-dom.js`. 

When you select an element in javascript, there is a `classList` attribute on it and on that there are some methods for getting all the classes and removing and adding multiple classes.

We will do an example with animation. Copy one of the image tags and add it to right after the body tag. Give it a class of `nice`. 

```
  <img class="nice" src="https://picsum.photos/500" />
```

Now in the javascript file, we will select the element with a class of nice and console log the class list. 

```
const pic = document.querySelector('.nice');
console.log(pic.classList)
```

![](@attachment/Clipboard_2020-02-19-16-03-58.png)

In the console we get a DOMTokenlist which is kind of like an array of all the classes that are on that image. Now if in our html file we add another class like "cool" to the image, you will see that we get both of them as well as a value of all of the classes.  

![](@attachment/Clipboard_2020-02-19-16-04-54.png)

If you look into the prototype (we haven't learned what that is yet), you are often able to see what are the methods you are able to call against the thing we have. 

classList has many methods. There is `add`, `remove`, `contains`, `foreach`. A lot of those are methods for working with classes which is exactly what we are going to do.

![](@attachment/Clipboard_2020-02-19-16-06-03.png)

![](@attachment/Clipboard_2020-02-19-16-05-33.png)

 You might notice as you type in VSCode, you get a dropdown of methods available to you:
![](@attachment/Clipboard_2020-02-20-08-35-45.png)


We are going to use `pic.classList.add()` to add a class of 'open'.

```
const pic = document.querySelector(".nice");
pic.classList.add("open");
console.log(pic.classList);
```

If you refresh the page in the browesr, you will see that image now has a class of open. Now let's say we want to remove the class of 'cool' which already exists on the element. We would simple do `pic.classList.remove('cool');`

![](@attachment/Clipboard_2020-02-20-08-37-54.png)

There is also `toggle` which is pretty cool. Let's write a bit of css so we can visually see what is going on.

In our `index.html` add a style tag somehwere on the page. 

```
<style>
  .round {
      border-radius: 50%;
    }
  </style>
```

Now in javascript, we will add a class of `round`, 

```
pic.classList.add('round');
```

Now the element has the class of round. We can add and remove that class either by pasting it into the console or on click. We will go over both.

Replace the 'add' method used above with `toggle()`. Toggle will add the class if it is not there, and remove it if it is. 

```
pic.classList.toggle('round');
```

Now, if we copy and paste that line of code into the console, you will see that the class is being added and then removed. 

Now if we go into our css and add a transition all for .2 seconds, that will give us an animation when the class is toggled. 

```
 img {
      transition: all 0.2s;
    }

    .round {
      border-radius: 50%;
      transform: rotate(1turn) scale(2);
      box-shadow: 0 0 10px black;
    }
```

Quick peak ahead (we will be learning about events later), you can do:

```
function toggleRound(){
  pic.classList.toggle('round');
}

pic.addEventListener('click', toggleRound);
```

What we are doing there is saying when the pic element is clicked, we want to the trigger the function called `toggleRound()` which should toggle the `.round` class on and off for our image element. 

You can add the following style to the `.round` class also for a rotation transition: `transform: rotate(1turn) scale(2);`

It is pretty cool that a lot of javascript interaction is just adding and removing classes at different points in time which then allows us to use css to add and remove transitions. This is common with modals and navs which open and close. We will be going over lots of examples of that throughtout the class.

There is also the `contains()` method, which you would use like so:

```
pic.classList.contains('open');
```
That will return true or false based on whether that element has the class or not.  That is useful when you want to check the current state of an element by looking at it's class list. 

In the next video we will go over regular attributes. Even though `class` is an attribute, classList gives us some utility methods for working with it. Whenever Wes need sto work with classes, he uses `classList` which is a few years old but fairly newer. 

---
