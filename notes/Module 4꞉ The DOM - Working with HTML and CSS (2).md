---
attachments: [Clipboard_2020-02-06-07-17-14.png, Clipboard_2020-02-06-07-18-07.png, Clipboard_2020-02-06-07-20-49.png, Clipboard_2020-02-06-19-10-10.png, Clipboard_2020-02-06-19-11-24.png, Clipboard_2020-02-10-21-17-14.png, Clipboard_2020-02-10-21-20-05.png, Clipboard_2020-02-10-21-22-12.png, Clipboard_2020-02-10-21-30-10.png, Clipboard_2020-02-19-07-40-26.png, Clipboard_2020-02-19-07-42-02.png, Clipboard_2020-02-19-07-42-42.png, Clipboard_2020-02-19-15-49-31.png, Clipboard_2020-02-19-15-50-11.png, Clipboard_2020-02-19-15-51-27.png, Clipboard_2020-02-19-15-54-21.png, Clipboard_2020-02-19-16-03-58.png, Clipboard_2020-02-19-16-04-54.png, Clipboard_2020-02-19-16-05-33.png, Clipboard_2020-02-19-16-06-03.png, Clipboard_2020-02-20-08-35-45.png, Clipboard_2020-02-20-08-37-54.png, Clipboard_2020-02-20-09-01-29.png, Clipboard_2020-02-24-19-07-41.png, Clipboard_2020-02-24-19-08-05.png, Clipboard_2020-02-24-19-35-04.png, Clipboard_2020-02-24-19-40-52.png, Clipboard_2020-02-24-19-43-41.png, Clipboard_2020-02-24-19-45-17.png, Clipboard_2020-02-24-19-47-27.png, Clipboard_2020-02-24-19-54-55.png, Clipboard_2020-02-24-19-57-21.png, Clipboard_2020-02-24-20-00-35.png, Clipboard_2020-02-24-20-07-18.png, Clipboard_2020-02-24-20-08-24.png, Clipboard_2020-02-24-20-09-22.png, Clipboard_2020-02-24-20-12-08.png, Clipboard_2020-02-24-20-18-37.png, Clipboard_2020-02-24-20-21-06.png, Clipboard_2020-02-24-20-22-51.png, Clipboard_2020-02-24-20-28-04.png, Clipboard_2020-02-24-20-37-23.png, Clipboard_2020-02-26-07-08-24.png, Clipboard_2020-02-26-07-09-00.png, Clipboard_2020-02-26-07-10-08.png, Clipboard_2020-02-26-07-24-01.png, Clipboard_2020-02-26-19-06-05.png, Clipboard_2020-02-26-19-13-49.png, Clipboard_2020-02-26-19-16-40.png, Clipboard_2020-02-26-19-20-03.png, Clipboard_2020-02-26-19-22-18.png, Clipboard_2020-02-26-20-10-05.png, Clipboard_2020-02-26-20-12-07.png, Clipboard_2020-02-26-20-12-38.png, Clipboard_2020-02-26-20-23-23.png, Clipboard_2020-02-27-07-11-07.png, Clipboard_2020-02-27-07-12-08.png, Clipboard_2020-02-27-07-13-17.png, Clipboard_2020-02-27-07-14-33.png, Clipboard_2020-02-27-07-16-14.png, Clipboard_2020-02-27-07-16-38.png, Clipboard_2020-02-27-07-18-49.png, Clipboard_2020-02-27-07-23-24.png, Clipboard_2020-02-27-07-26-02.png, Clipboard_2020-02-27-07-28-43.png, Clipboard_2020-02-27-07-29-28.png, Clipboard_2020-02-27-07-29-30.png, Clipboard_2020-02-27-07-32-11.png, Clipboard_2020-02-27-08-11-29.png, Clipboard_2020-02-27-08-13-15.png, Clipboard_2020-02-27-19-03-44 (2).png, Clipboard_2020-02-27-19-03-47 (2).png, Clipboard_2020-02-27-19-40-50.png, Clipboard_2020-02-27-19-46-29.png, Clipboard_2020-03-01-11-44-41.png, Clipboard_2020-03-01-11-52-10.png, Clipboard_2020-03-01-12-01-58.png, Clipboard_2020-03-01-12-18-46.png, Clipboard_2020-03-01-12-20-19.png, Clipboard_2020-03-01-12-43-10.png, Clipboard_2020-03-01-12-50-50.png, Clipboard_2020-03-01-12-52-47.png, Clipboard_2020-03-01-12-56-16.png, Clipboard_2020-03-01-13-04-07.png, Clipboard_2020-03-01-13-12-37.png, Clipboard_2020-03-01-13-20-11.png, Clipboard_2020-03-01-13-29-03.png, Clipboard_2020-03-01-13-30-11.png, Clipboard_2020-03-01-13-46-47.png, Clipboard_2020-03-01-13-48-16.png, Clipboard_2020-03-01-13-50-20.png, Clipboard_2020-03-01-13-51-26.png, Clipboard_2020-03-01-13-54-50.png]
title: 'Module 4: The DOM - Working with HTML and CSS'
created: '2020-02-06T12:06:57.469Z'
modified: '2020-07-29T22:36:42.176Z'
---

# Module 4: The DOM - Working with HTML and CSS

## 20 - The DOM - Introduction to the document

So far, everything we have been learning has been javascript as part of the core languages. 

Although Javascript can be run in many environments (browser, server, robots), a lot of places use javascript as a scripting environment. 

The most popular way to run javascript is through the web browser, and a big part of that is interacting with elements on a page. 

When you write HTML and view it in the browser, the browser turns your HTML into something that is called the **Document Object Model** or **the DOM**. 

That is what you see when you go to the elements panel in the developers tools on any website. 

It is not actually just the HTML that you have written, it takes that, converts it to the **Document Object Model**, and it allows us to interface with the DOM via javascript. 

We can do things like listen for clicks and scrolls. 
We can add, move, remove elements from that page or things like text, images, etc. 
We can add and remove CSS classes from elements which can trigger animations.
We can fetch new data. 
We can play music and video.
We can add any type of interaction to the page.
... and that is done by writing javascript that interfaces with the DOM (the things that are on the page, the elements on the page).

The DOM is represented in a tree that looks very much like HTML. 

Even if you are using a framework like React, Angular or Vue, it's very helpful to understand that core concepts of the DOM like events, elements and classes, because they transcend all of the different framesworsk. 

Even if the frameworks help you do these things, you still need to know how it works under the hood. 

### `window` Refresher 

A quick refreshed on the Window. 

In the scope video, we learned that the global scope in the browser is called the `window`. 

The window is where are our global variables are stored, as well as helpful properties like `window.location`. 

![](@attachment/window-location.gif)

_👆 Aside: if you go to any website and in the console type in `window.location` or `location` it will return to you the websites url and a whole bunch of information, as demonstrated above._

It returns an object full of information like the current page you're on, the host name, what hthete protocol is, if we are on a specifc port it would be showing us that info. 

We can also find things like `innerWidth`, which will tell us how wide the browser is if you type it in the console. 

![](@attachment/Clipboard_2020-02-06-07-18-07.png)

You can think of the `window` as everything about the currently opened window.

That includes:
- the browser bar
- the tabs 
- the scroll bar
- basically all of the things about your browser window are generally stored inside of the window object 

### `document` Introduction

The document is responsible for everything from the opening HTML tag `<html`>, the doc type as well, to the closing HTML tag(</html>). 

The difference is the document is not concerned with tabs, and outside, it's just concerned with the entire `DOM`. The entire document will be available to us with the `document` keyword. 

If you type `document` into the console and hover over what it returns, you will see that it highlights the entire page

![](@attachment/document.gif)

### The `navigator` 

There is also something called the `navigator`. 

The `navigator` is sort of just a higher level thing than the window that gives you information not just about the browser, but the device itself, the device that it is on. Think about things like web cam and audio access, battery levle, GPS coordinates.

Things that are device specific will live on the navigator. 

Right now you just need to know that there is the `window` which contains a lot of information about the browser but the `document` is going to contain everything about the current web page from the opening HTML to the closing HTML tag. 

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

## 24 - The DOM - Build in and Custom Data Attributes

When you are working with HTML elements, those elements have something called attributes. Attributes are anything provided to an element as additional information. Things like classes, src, alt attributes. 

Attributes work the same way as the other properties that we have been working with so we will go over it quickly before getting into custom attributes and data attributes. 

Here is how we would add an alt attribute to the image element we were using in the previous video. 

`pic.alt = "cute pup";`

TIP: When adding alt attributes to images, the value of the alt text should describe the image. You do not need to include in the text that it is a photo, because screen readers will specify that. 

Although we did not add the alt attribute when we authored the element, when we added it via javascript, you can now see it on the element. 

![](@attachment/Clipboard_2020-02-20-09-01-29.png)

We could also do something like setting the width. 

```js
pic.width = 200;
```

Most attributes are both **getters** and **setters**, meaning we could do both of the following:

```js
pic.alt = 'Cute pup'; //setter
console.log(pic.alt); //getter
```

Some attributes however are only getters, such as `naturalWidth`. If you add 

```js
console.log(pic.naturalWidth);
```

![](@attachment/Clipboard_2020-02-24-19-07-41.png)

We get zero! Why is that? If you try running it from your console like so, you get a value of 600 back. Why?

![](@attachment/Clipboard_2020-02-24-19-08-05.png)

It is zero when we console log it in the javascript file, but in the terminal it is 600. This is a problem that you frequently run into, which is that we have to wait for the image to actually be downloaded for us to know how large it is. This is a big problem when people were building slideshows. SO how to overcome this? One option is to add an event listener on the load event.

What this should do is wait for all the images, resources, CSS, Javascript, anything that needs to be loaded to load before calling the function. 

```js
window.addEventListener('load', function(){
  console.log(pic.naturalWidth);
});
```

Now, a split second after you refresh your html page, you should see the naturalwidth value logged in the console. 

You can also use the eventlistener specifically on an image. So we could modify the event listener code we added like so:

```js
pic.addEventListener('load', function(){
  console.log(pic.naturalWidth);
});
```

Now that will work as well, once the image is loaded, the event listener will fire.  All of that eventListener stuff is a bit ahead of ourselves but it's good to know some of the gotchas that you may encounter. 

You might be asking yourself "we added our javascript script src tag at the end of the html file, doesn't that mean that is waits for everything to be loaded?". Yes, putting the script at the bottom of the html page waits for all the HTML to be loaded, but if the HTML goes ahead and makes additional requests like downloading images, it doesn't wait for those. 
 

Getting back on track, we were discussing how `naturalWidth` is only a getter. If try to set it in the code:

```js
pic.naturalWidth = 200;
```

It won't error out, but it won't do anthing, and that is because it is not an attribute that you can change. 


All of the attributes you can think of on any element are all done via getters and setters. You just use the dot notation to access them. 

You may have run into these `getAttribute`, `setAttribute` and `hasAttribute` methods:

```js
pic.setAttribute('alt', 'REALLY CUTE PUP');
console.log(pic.getAttribute('alt'));
console.log(pic.hasAttribute('alt'));
```

`hasAttribute()` returns true or false depending on whether an attribute is set on an element. 

However, what is the difference between using `getAttribute` and using the dot notation to grab the attribute? The answer to that is that `setAttribute()` will also work for things that are non-standard. We have HTML as a spec, and you have all of your standard attributes in the spec like `alt`, `title`, `width`, `src`, and all of those things. But if you want to set an attribute that is non standard (which you shouldn't do, more to come regarding that), you can use setAttribute to make something. For example

```js
pic.setAttribute('wes-is-cool', 'REALLY CUTE PUP');
```

![](@attachment/Clipboard_2020-02-24-19-35-04.png) 7:07

You should not go making your own attributes whenever you want because what if in the future HTML introduces an attribute with the same name as one of your custom attributes. You will have legacy code that is clashing with the standards which will lead to bugs. 

**Data Attributes**

If you do want your own custom attributes, you want to use **data attributes**. To demonstrate what data attributes are, go to our html page and duplicate an image 3 times and add a `data-name` attribute to each:

```html
<img class="custom" data-name="wes" src="https://picsum.photos/200" />
<img data-name="kait" src="https://picsum.photos/200" />
<img data-name="lux" src="https://picsum.photos/200" />
```

In this example, we just wanted to attach a piece of metadata to each of the images. If you want to attach metadata or something to an element that does not have any sort of standard attribute like a name attribute, then you can use `data-` anything. For example: `data-dog`, `data-name`, `data-description` are all valid data attributes. That will allow you to attach metadata to an element. 

![](@attachment/Clipboard_2020-02-24-19-40-52.png) 9:12

Let's say we want to grab the image with the custom class and access the data attributes on that image. You might think we do something liek this 

```js
const custom = document.querySelector('.custom');
console.log(custom.data);
```

However, that will give us undefined. If you want to access the data attributes on the element you would call `dataset` like so:

```js
const custom = document.querySelector('.custom');
console.log(custom.dataset);
```

![](@attachment/Clipboard_2020-02-24-19-43-41.png)

That gives us an object that is full of all the property values that you have. `data-name` shows up as "name" in our object, and if we had multiple data attributes on the same image like so:

```html
<img class="custom" data-name="wes" data-last="bos" src="https://picsum.photos/200" />
```

![](@attachment/Clipboard_2020-02-24-19-45-17.png) 10:15

Why would this be useful? We can do things like listen for a click, and when someone clicks on it, we can alert them. 

```js
custom.addEventListener('click', function(){
  alert(`Welcome ${custom.dataset.name} ${custom.dataset.last} `);
});
```

Now if you were to click on that image, you would get an alert, like so:

![](@attachment/Clipboard_2020-02-24-19-47-27.png)

Wes loves using data attributes when you are coding vanilla javascript.

To recap: anytime you need some sort of  custom attribute, when you need to associate some sort of information, some sort of text etc, use the custom data attribute. 

---

## 25 - The DOM - Creating HTML

Now we are going to learn about creating elements. 

Create a javascript file within the `20 - The DOM` folder called `creating.js`. In the `index.html` file we have been using so far, replace the script src from `the-dom.js` to `creating.js` like so:

```html
<script src="./creating.js"></script>
```

If you want to create HTML in javascript, it can be done in a few different ways. The main way is with document.createElement() so let's go look that up. 

![](@attachment/Clipboard_2020-02-24-19-54-55.png) 00:54

You give it a tagName and then there are optional options (you can tell it's optional because of the square brackets, which we won't be using. 
We will go ahead and try to make a paragraph tag.    

```js
const myParagraph = document.createElement('p');
console.log(myParagraph);
```

If you load the html file, you will see the paragraph in the console but it is not on the page. That is because we haven't actually put it on the page yet, we just created it and its in what we call memory right now. 

![](@attachment/Clipboard_2020-02-24-19-57-21.png) 2:05

There is no shortcut to create an element with a class or with a set attribute like so:

```js
const myParagraph = document.createElement('p.special[title="hey"]');
```

If you want to add or get attributes from it, you must instead do it the way we have learned.   
 
```js
const myParagraph = document.createElement('p');
myParagraph.textContent = 'I am a p!';
myParagraph.classList.add('special');
console.log(myParagraph);
```

![](@attachment/Clipboard_2020-02-24-20-00-35.png) 2:57

We now have that paragraph with a class of `.special` and the text content that we supplied it with. 

We will create a new more elements before we go over how to actually insert them into the DOM. 

```js
const myImage = document.createElement('img');
myImage.src = "https://picsum.photos/500";
myImage.alt = "Nice photo";
console.log(myImage);
```

Next we will create a div 

```js
const myDiv = document.createElement('div');
myDiv.classList.add('wrapper');
console.log(myDiv);
```

Now we have a paragraph, an image and a div. 

How do we add it to the page? We use another API called **appendChild**. So you need to go off and grab some sort of element to call `.appendChild()` against. 

If you want to dump it straight into the body, you can grab the document.body and insert it. `document.body` is available to us because the `document` element gives us access to the body element quickly via a property. Not every element is as easily accessible to us like body is. 

Let's look up `appendChild()` in MDN. It takens in one param, which is a child. 

![](@attachment/Clipboard_2020-02-24-20-07-18.png) 5:54

```js
document.body.appendChild(myParagraph);
```

![](@attachment/Clipboard_2020-02-24-20-08-24.png)

This gives us a p tag right before the closing body tag. 

`appendChild()` can be called against any node, so we can do something like this:

```js
document.body.appendChild(myDiv);
myDiv.appendChild(myParagraph);
myDiv.appendChild(myImage);
```

![](@attachment/Clipboard_2020-02-24-20-12-08.png) 7:02

It is probaby better to do that in reverse order. Why? Because everytime you call `appendChild()` you are modifying the DOM and that causes in the browser something called a 're-flow" which tells the browser that something has been changed, that new elements have been added, and tells the browser to repaint the html. This means that if you call `appendChild()` three times in a row, you are causing the browser to re-render three times in a row. That can start to eat into other things on the page and degrade the user experience. 

What you could do instead is:

```
myDiv.appendChild(myParagraph);
myDiv.appendChild(myImage);
document.body.appendChild(myDiv);
```

What we are doing here is we are creating the elements and inserting the paragraph inside of the div, and the image inside of the div as well, but we are only modifying the DOM once in the last `document.body.appendChild(myDiv)`. That will cause the browser to re-paint only once as opposed to three times in the earlier example. 

Technically, the browser is doing two repaints, once when you dump the div in and the second time when the image loads, that's not the end of the world, that is how the browser works. 

That is one way to go ahead and create elements, using the `createElement()` API. 

**append()**

You may come across in your searches that there is `.append()` however it doesn't seem to be fully supported in internet explorer so I would hold off on using it but it works very similarly to `createElement`.

![](@attachment/Clipboard_2020-02-24-20-18-37.png)

**insertAdjacentElement()**

There is another API that Wes is fond of which is `Element.insertAdjacentElement()`. Earlier we looked at `insertAdjacentText()` to before, after and inside elements. Pretty much the same API works with elements. 

![](@attachment/Clipboard_2020-02-24-20-21-06.png) 10:41

This is handy because let's say we have the div with paragraph, but we need to insert something infront of the pargaph.

```
const heading = document.createElement('h2');
heading.textContent = 'Cool things';
myDiv.appendChild(heading);
```

![](@attachment/Clipboard_2020-02-24-20-22-51.png)

If you do the above, you will see that the heading is inserted after the image which is not what we want. 

`insertAdjacentElement()` takes two things, first the position of where you want it to do, and then the element you want to insert.

```js
myDiv.insertAdjacentElement('afterbegin', heading);
```

That will put the heading before the paragraph and image tag. 

![](@attachment/Clipboard_2020-02-24-20-28-04.png)

If you were to use `beforebegin`, it will isert the header before the div tag, as a sibling to the wrapper. That may be something you will need to use. Let's say you have a few cards and you need to add something after the first card. You can grab the second card and use beforebegin to insert an element before it. 

Let's do one more example. We will create an unodered list with 5 items in it, and we will do that entirely with all the APIs we have learned so far. 

It should look like 

```html
 <ul>
    <li>one</li>
    <li>two</li>
    <li>three</li>
    <li>four</li>
    <li>five</li>
  </ul>
```

Start with the middle one and then try to insert one before.. however you can make use of all the APIs that we have gone over. 

Pause the video here and try to create that and inject it into the DOM. 

First we will create the unordered list. Then we will make the third list item and append it to the list. 

NOTE: If this seems like a lot of code to make an unordered list, well it is, we will go over in the next section how we can write a bit of html in a string and inject it in. 


```js
const list = document.createElement('ul');
const li = document.createElement('li');
li.textContent = 'three';
list.appendChild(li);

document.body.insertAdjacentElement('afterbegin', list);
```

Now let's create the other list item which we will use `append()` to add:

```js
const li5 = document.createElement('li');
li5.textContent = 'Five';
list.append(li5);
```

There is the ability to clone a node which we could do like so:

```js
const li1 = li5.cloneNode();
list.insertAdjacentElement('afterbegin', li1);
```

What this will do is take a clone of the li5 node , and then we are going to insert it adjacently. 

![](@attachment/Clipboard_2020-02-24-20-37-23.png) 16:03

If you reload the page, you will see that we added the element but it is empty. That is because if we look at the docs for `cloneNode()`, it accepts a param of "deep" which specifies whether to clone the child nodes or not. You may be wondering "well isn't text part of the element?", and no, it is a child of the element. Just because it is not wrapped in a separate element like a `<span>` or something, makes it just a regular node. So we need to pass `true` when doing `cloneNode()`. 

```js
const li1 = li5.cloneNode(true);
li1.textContent = 'One';
list.insertAdjacentElement('afterbegin', li1);
```

In this instance `cloneNode()` wasn't much more efficient to use, but it generally is if you are trying to clone an element that has a lot of attributes set on it, and want to copy those over as well.

Now that we have one, three and five, how do we inject two and four? 

```js
const li4 = document.createElement('li');
li4.textContent = 'Four';
li5.insertAdjacentElement('beforebegin', li4); 
```
We will use `beforebegin` because we want it to go beside the 5th one. 

```js
const li2 = document.createElement("li");
li2.textContent = "Two";
li1.insertAdjacentElement("afterend", li2); 
```

That was a good practice of using all the different APIs available to us to create elements, set the contents and insert them in different ways. 
In the next video, we will look at how we can use backticks and strings to generate the HTML for us. 

--- 

## 26 - The DOM - HTML from Strings and XSS

We are going to learn about creating HTML with strings, using the **backtick strings** Wes showed us earlier. 

This approach is Wes' favourite, but make sure to watch the video all the way through, because at the end Wes will show a potential security hole that comes up when using this method. The main security flaw with this method is something called **XSS** which stands for **cross-site scripting**.

Create a new javascritp file `creating-with-strings.js` and change the script src in the `index.html` file to point to our new file. 

There is a property `innerHTML`, which is similar to `innerText` which we can grab off an element. We will grab the element with the class of item and console log it. 

```js
const item = document.querySelector('.item');
console.log('item.innerHTML');
```

![](@attachment/Clipboard_2020-02-26-07-09-00.png) 2:13 

You can see that `innerHTML` is a string of all the HTML that makes up what is inside of it. That is a getter. What if we use it as a setter?

```
innerHTML = `<h1>Hey How are you?</h1>`;
console.log(innerHTML);
```

![](@attachment/Clipboard_2020-02-26-07-10-08.png) 2:39

The inside of the `div.item` has been updated with some HTML. 

That works because if you set the innerHTML of an element with just a string instead of a regular document.createElement, document.cloneElement like we did in the previous video, it will take the text and dump that HTML into the item. If it is valid HTML, the browser will take it and parse it and turn it into all the items. 

TIP: You may have noticed that in Wes code editor, he has the ability to type the first few letters of something and then expand it. He is using an extension called Emmet to get those expansions and using a command called Expand Abbreviation to expand them. It lets you write things like `div.item.iteme` which will expand out to `<div class="item iteme"></div>`. 

One benefit of using backticks for single or double is that you can have multiple lines. 

```
item.innerHTML = `
  <div>
    <h1>Hey How are you?</h1>;
  </div>
`
```

IT doesn't matter if you indent or put it all on one line, but it makes it easier for you to read it when you code. 

So to recap: setting innerHTML into your element is one way to dump your string in and have the browser create all the elements for us. 

Why is that useful other than the fact that we don't have to do all the document.createElement and appending steps? Because, when you use backticks, you can **interpolate values** very easily. 

For example:

```
const src = `https://picsum.photos/200`;
const desc = "Cute pup";
const myHTML = `
  <div class="wrapper">
    <h2>Cute ${desc}</h2>
    <img src="${src}" alt="${desc}"/>
  </div>
`;
```

We are able to use the syntax `${variable}` it allows us to pop variables right into the template that we have. This is similar to template that exists in almost every programming language, although they all look a little different. It all works the same way.

Now, when we set the innerHTML of an element, all the vairables will have been populated. 

```html
item.innerHTML = myHTML;
console.log(item.innerHTML);
```

![](@attachment/Clipboard_2020-02-26-07-24-01.png) 6:45

We could go a step further with the following code, notice the `width` variable and how we are interpolating the width variable in the `src` declaration. 

```
const width = 500;
const src = `https://picsum.photos/${width}`;
const desc = "Cute pup";
const myHTML = `
  <div class="wrapper">
    <h2>Cute ${desc}</h2>
    <img src="${src}" alt="${desc}"/>
  </div>
`;
```

Now the image link will return a much larger photo of 500px. 

Besides security, one of the other downsides to using this method to insert HTML is that the contents of the `myHTML` variable are not elements, they are just strings. 

You can see that in two ways. First, you can `console.log(myHTML);` and you can also check and log he type of the variable like so: `console.log(typeof myHTML);`. 

![](@attachment/Clipboard_2020-02-26-19-06-05.png) 7:37

That means we cannot do things like `myHTML.classList.add('special');` If you try to do that, it will give you an error similar to

> Cannot read property 'add' of undefined at ...

Similarly, if you try to do `console.log(myHTML.classList);` you will see that it is also undefined. Why? Because it is only a string. 

It only becomes an element once we dump it into the DOM by setting the `innerHTML`. If you want to do things like add event listeners, add to the classList, dynamically change any attributes, like title or alt or src of any of those elements, it is not doable until you first dump it into the DOM. 

Once you dump it into the DOM, you have to go ahead and pull it out.  Here is an example. 

Let's say we wanted to add a class to the image within `myHTML`. We would have to do that like so:

```js
const itemImage = document.querySelector('.wrapper img');
itemImage.classLIst.add('round');
```

![](@attachment/Clipboard_2020-02-26-19-13-49.png) 9:59

There are a few ways you can get around that and do the best of both worlds which is using document.createRange and document.createFragment. 

Remove everything below the `myHTML` declaration within `creating-with-strings.js`. Let's now turn the string into a DOM element. 

```
const myFragment = document.createRange();
console.log(myFragment);
```

![](@attachment/Clipboard_2020-02-26-19-16-40.png) 11:19

This code creates something called a range. A range is essentially a collection of elements or part of HTML that we can then work with. That is exactly what we want, we want to take the `myHTML` string and create a couple of fragments. 

We can call another method directly on `document.createRange()` called `.createContextualFragment();` which takes in a string as a parameter. 

```
const myFragment = document.createRange().createContextualFragment(myHTML);
console.log(myFragment);
```

If you open the page in a browser and view the console, you will see that we can this thing called a **document fragment** (which is just a way of saying some HTML). 

![](@attachment/Clipboard_2020-02-26-19-20-03.png) 11:46

Now, from within this fragment, we are able to access all of the elements that live inside of it. We turned our HTML into true elements which are still not on the page anywhere but we have them as DOM elements and now can do things like `myFragment.querySelector('img');` and look for an image inside of the fragment. 

![](@attachment/Clipboard_2020-02-26-19-22-18.png) 12:29

Let's now try to append the fragment to the document. Let's try `appendChild()` 
```
document.body.appendChild(myFragment);
```

That works! You could also do 

```
document.body.appendChild(myFragment);
```

You could also use `insertAdjacent` which we learned previous. 

To recap: when you want to create HTML from a string, you can dump it into the document using `innerHTML`, OR when you need to do things with the elements in javascript, you can turn it into DOM nodes before it is dumped into the document with `createContextualFragment()`. 


### Security and Santization

We will have an entire video on security later in the course, but for now, we want to talk about the potential pitfalls of inserting HTML using strings. 

One scenario you might run into you have an application with a profile and people can edit their profile, change their name, change their description etc. Now if someone puts HTML into that, what can happen is that the HTML can then be rendered on to the page. 

Let's do an example. 

![](@attachment/Clipboard_2020-02-26-20-10-05.png) 15:00


Let's say we are taking this description variable from somebody. 

They could put `const desc = \`Cute pup <h1>LOVE THIS GUY</h1>\`;`

If you refresh the HTML page, you will now see that there is actually an H1 tag that wasn't created from us.  

![](@attachment/Clipboard_2020-02-26-20-12-38.png) 15:17

Remember, in this example scenario, the description value would be coming from a database, from someone's editor when they typed it in. They just started to put some HTML. 

They could also something like:

```
const desc = `Cute pup <h1>LOVE THIS GUY</h1><style>*{display:none;}</style>`;
```

If you refresh the HTML page, you will see all the content is gone. 

ASIDE: This is what MySpace allowed you to do. You used to be able to put in your own style tags 

In this scenario, we were just expecting the user to enter in text but they hijacked it and added whichever HTML they wanted to. 

That is all fun and games until you get into **XSS** which is shortform for **cross-site scripting**. 

XSS is where people try to insert script tags using a method like entering an HTML string in a text input such as your profile name. The browser will then run the script tag, and you can do anything you want with that, like drain someone's bank account. 

Imagine you were signing in to your online banking and your bank asked you to enter your name, and you included a script tag. You could do anything you want outside of that including deleting things, sending money, any type of malicious acting. 

A very simple example of that is let's say you want to allow someone to include an image in the description of the picture from the example above. Something like:

```js
const desc = `Cute Pup <img src="https://picsum.photos/50"/>`;
```
That is okay, but let's say someone hijackts the `onload` event that is accessible via an attribute on the img element, and will run whatever javascript is supplied to it when the image loads. 

```
const desc = `Cute Pup <img onload="alert('hacked');" src="https://picsum.photos/50"/>`;
```

If you refresh the HTML page, you will see an alert. 

![](@attachment/Clipboard_2020-02-26-20-23-23.png) 17:48

What happened there is you took data from the user and allowed them to run any javascript that they want on your website, which is a potential security hole. 

Imagine that on facebook you allowed someone to run any javascript, you could have your friends unfriend eveyrone, send malicious messages etc. Anytime you allow a third party to run Javascript on your page, that is a huge security hole. 

The only javascript that should be running on your page is Javascript that you, the developer, authored, and from approved parties like Google Analytics. 

To recap: Cross Site scripting is when a third party injects a script tag through a security hole like this. 

In the security video, we will go over how to scrub your HTML of any potential security vulnerabilities like this before you dump it. 


---

## 27 - The DOM - Traversing and Removing Nodes

In this video, we will learn about traversing through our DOM element and removing elements from the DOM. 

Create a file called `traversing.js` and go into the html and modify the script src to point to the new javsascript file. 

**Traversing** means going up, down, over etc. When you have an element, you often need to select an element based on it's position. For example, let's say you are working on a button and you need to grab its parent div. Or maybe you need to look inside of the button element for all the elements inside of it. 

There are lots of properties for that, and they all revolve around node and elements. 

### The difference between and node and an element

We will do an example to demonstrnate the difference. In the `index.html` file, create a p tag with the class of Wes. We are going to put a few elements within the p tag now. 

```html
<p class="wes">I am Wes, I <em>love</em> to bbq</p>
```

Now in the javaascript we will select that p tag. 

```
const wes = document.querySelector('.wes');
console.log(wes);
```

![](@attachment/Clipboard_2020-02-27-07-11-07.png) 2:04

If instead you log the children of the wes element using `console.log(wes.children)`, you will see that in the console we get a collection of one thing, which is the em tag. 

![](@attachment/Clipboard_2020-02-27-07-12-08.png) 2:25

If instead we were to `console.log(wes.childNodes);`, you would see that we get three things: text, em and text. In the HTML collection, only the `em` element was returned. 

![](@attachment/Clipboard_2020-02-27-07-13-17.png) 2:30ish?

If you hover over the nodes in the console one at a time, you will see it highlighting the corresponding node on the HTML page. 

This is the first text node. 

![](@attachment/Clipboard_2020-02-27-07-14-33.png) 2:41

Then the emphasis node. 

![](@attachment/Clipboard_2020-02-27-07-16-14.png)

Then the rest of the text.

![](@attachment/Clipboard_2020-02-27-07-16-38.png) 2:46

Everything in our NodeList in the console is a node, and if it is wrapped in a tag, it is also an element, but it doesn't work the other way around. If you only select elements, you won't have nodes returned. But if you select the nodes, you get all of the three different pieces. 

![](@attachment/Clipboard_2020-02-27-07-18-49.png) 3:12

TIP: You can do multi-cursor in VS Code. The way you use that is you hold down command or control and click wherever you want the cursors to go. In this video Wes used multicursor by selecting an element and then doing command + D to grab other occurences


### Properties to work with nodes and elements

We already looked at children, which gives you child elements or child nodes. 

Let's add a few more elements to work with. 

```js
console.log(wes.firstElementChild);
console.log(wes.lastElementChild);
console.log(wes.previousElementSibling);
console.log(wes.nextElementSibling);
console.log(wes.parenteElement);
console.log(wes.childNode);
```

Here is the result when you refresh the index.html page. 

![](@attachment/Clipboard_2020-02-27-07-23-24.png) 3:59

`children` gives you the children. 

Let's add a few more elements inside of the p tag. 

```HTML
<p class="wes">
  I am Wes, I <em>love</em> to bbq and <strong>Make websites!</strong>
</p>
```

That returns ![](@attachment/Clipboard_2020-02-27-07-26-02.png) 4:22

`firstChildElement` returns the emphasis element and the `lastChildElement` returns the strong element. 

`previousElementSibling` is null. Why? If you look at our html page, you will see that we have a few elements with the class of `item` that are next to each other. 

![](@attachment/Clipboard_2020-02-27-07-29-30.png) 4:45

If we were to grab the second item by clicking it in our developer tools and then using `$0` to reference it in the console, we can take it and run  `$0.childrenElementCount` which will tell us the number of children elements. `$0.children` will return a collection of three elements. `$0.previousElementSibling` will give you the item that is before it. 

![](@attachment/Clipboard_2020-02-27-07-32-11.png) 5:30

We were on item 2, and the previous element sibling is the first item. 

JQuery used to make this easy with syntax like `.prev()` `.next()`. All of that is still doable with these properties. They are not named the nicest things but they work and you can figure it out. 


There is `nextElementSibling` which will grab the sibling element after the currently selected element. 

And then there is `parentElement` which will go up and give you the parent element of the currently selected element. 

If you take an element that is really low in the document like one of our image elements, you can chain calls to `.parentElement` like so:

![](@attachment/Clipboard_2020-02-27-08-11-29.png) 6:19 

How high can we go? If you add one more `.parentElement` it returns html, and if you add one more, it returns null. That means we have reached the top most element. 

Now let's say we were to select a span inside of `.item2`, and you do $0, it will give us the span. `$0.parentElement` gives us the h2, and one more parentElement chain gives us item 2. Now we can call `nextElementSibling` which gives us the first item, and then you can do down again using `.children[1]` to select the paragraph with the class of pizza. We will talk about the [] notation shortly, but essentially that is how you reference items that are indexed. 

![](@attachment/Clipboard_2020-02-27-19-03-47.png) 7:20

By starting with the span in item 2, we went up, up, over down and selected the second element. That is probably not something you would do because assuming that the structure of the HTML is the best way to move aorund elements is probably not a good idea because if someone adds an extra div, then everything is ruined. Using querySelector is better to use to search for what we want. There is also another method `.closest()` which will allow us to search.
 
We also have a bunch of different properties for Nodes as well. 


```
el.childNodes
el.firstChild
el.lastElementChild
el.previousElementSibling
el.nextSibling
el.parentNode
```

Unlike the element properties, these will not ignore text nodes, so it's important to know the difference. In most cases, you probably want the element selectors but in some instances you want the node selectors. 

### Removing Elements

There is a method on every single element on every single node which is the ability to remove something. Let's do it from the dev tools. Grab the h2 tag by clicking the element in the element pane and then in the console write `$0.remove()`.
 
 ![](@attachment/Clipboard_2020-02-27-19-40-50.png)

 That removes the element completely from the DOM. 
 
 The only kinda gotcha is what happens if you were to create an element, add it to the DOM and call `.remove()`? 

Let's try it. 

 ```
const p = document.createElement("p");
p.textContent = "I will be removed";
document.body.appendChild(p);
p.remove()
 
 ```

 If you open the index file in the browser, you won't see the p tag because we added it and then immediately removed it. The question now is what if you console.log `p` after you call `remove()`, will it be null, undefined? 

 ![](@attachment/Clipboard_2020-02-27-19-46-29.png) 10:33

 It is still there! The fact that we had created that element and it exists in our javascript memory means that we do still have access to that paragraph element and we could add it back in to the DOM. If you have reference to that element in javascript, and you've craeted it in your javascript, you can add it again. 

 ---

## 28 - The DOM - CARDIO
  
This video will all be "cardio" which is what Wes likes to call excercises that are all realted to one another. The purpose of these excercises is to practice the material we have learned by puttng yourself through the excercises and hopefully improving. We want to nail down the fundamentals before we start building real stuff with interfaces etc. 

What you should do now is pause the video and go through all the excercises in the `DOM-CARDIO.js` file and try to do as much as you can. There is no right answer, there is a bunch of different ways that you could solve it. Then come back and watch the video to see how Wes would approach it. 

The `DOM-Cardio.html` file has no HTML in the body at all, and `DOM-Cardio.js` is just a blank javascript file with comments explaining the different excercises. 


First we need to make a div: 
```
const div = document.createElement('div');
```

Then we add a class of wrapper to it 
```
div.classList.add('wrapper');
``` 

Next, append it to the body
```
document.body.appendChild(div);
```

That works!

![](@attachment/Clipboard_2020-03-01-11-44-41.png) 1:35


Next we will make an unordered list, which should be familiar to you since we have gone over how to do it together already. 

```
const ul = `
<ul>
</ul>
`;
```

To add the three list items with the words one two and thre we will modify our `ul` variable declaration like so:

 ```
const ul = `
<ul>
  <li>one</li>
  <li>two</li>
  <li>three</li>
</ul>
`;
// add three list items with the words "one, two three" in them
```

Next we need to put the list in the above wrapper. There are a few ways you could approach this. 

```js
div.innerHTML = ul;
console.log(div);
```

![](@attachment/Clipboard_2020-03-01-11-52-10.png) 2:21

That works well. We could have add it as a fragment, but because there was nothing in the body already, it was simple to use innerHTML. 

Next we need to create an image:

```
const img = document.createElement('img'
```

Next we need to set the image source.

```
img.src = 'https://picsum.photos/500';
```

Next we need to set the image width to 250. 

```
img.width = 250;
```

Then we need to give the image a class of cute

```
img.classList.add('cute');
```

Now we need to add an alt of cute puppy. 

```
img.alt = "Cute Puppy!";
```

Next we need to append it to the wrapper. We will take our div and call appendChild on the image. We do not need to call `insertAdjacent` because it will go to the bottom of it. 

```
div.appendChild(img);
```

![](@attachment/Clipboard_2020-03-01-12-01-58.png) 3:35

You may notice that everytime you refresh the image, the image is sort of jumping. If we were to add `img.height = 250;` to the javascript code as well and then refresh, you will see that it is not jumping anymore. That is because if you give it a width and height attribute, it will maintain it's spot while it loads the image, which is great. 

Next, we need to use HTML strings to make a div with two paragraphs inside of it. 


```
const myHTML = `
  <div>
    <p>Paragraph One</p>
    <p>Paragraph Two</p>
  </div>
`;
```

Next we have to insert the div above the unordered list that we created earlier.
To do this, we want to grab that `ul` which we may still have reference to. We can check by doing `console.log(ul);`. 

![](@attachment/Clipboard_2020-03-01-12-18-46.png) 5:19

Wes was wrong -- it does not look like we already have access to the `ul` element because it shows up in the console as a string, rather then an element object. So we need to somehow grab that. 

Since we already have the div element, we can look within it to grab the ul element like so:

```
const ulElement = div.querySelector('ul');
console.log(ulElement);
```

![](@attachment/Clipboard_2020-03-01-12-20-19.png) 5:40

Next we need to add this div to the unordered list from above. Let's try:

```
ulElement.insertAdjacentElement('beforebegin', myHTML)
```

If you refresh the html page, you will see an error that says
>Uncaught TypeError: Failed to execute 'insertAdjacentElement' on 'Element': parameter 2 is not of type 'Element'.

![](@attachment/Clipboard_2020-03-01-12-43-10.png) 6:23

So because we have created it as a string, how do we insert it adjacently? 

We could try using `insertAdjacentHTML()`.

```
ulElement.insertAdjacentHTML("beforebegin", myHTML);
```

![](@attachment/Clipboard_2020-03-01-12-50-50.png) 6:48 

That works great! We could have also done create range and then added it as a document fragment. 

Next, we need to add a class to the second paragraph called warning. We need to somehow select that paragraph. 

If we look at the HTML in the dev tools

![](@attachment/Clipboard_2020-03-01-12-52-47.png) 7:15

We have a wrapper and then it's the first div that shows up. We could select it using querySelector like so:
```
const myDiv = div.querySelector('div');
```

Or we could use `firstElementChild`. 

```
const myDiv = div.firstElementChild; 
console.log(myDiv);
```

![](@attachment/Clipboard_2020-03-01-12-56-16.png) 8:00

THat is working, however, let's not use that because if we insert anything else, the div could no longer be the first element child so it's pretty unstable. 

What we are going to do is go into the `myHTML` variable declaration from above and add a class to the div that we inserted called `myDiv`. 

```
const myHTML = `
  <div class="myDiv">
    <p>Paragraph One</p>
    <p>Paragraph Two</p>
  </div>
`;
```

And then we will select the div using the class name. This makes the code more resilient. 

```
const myDiv = document.querySelector('.myDiv');
```

Next we need to add a class to the second paragraph called `warning`. 

Let's try using `myDiv.children`. First we will console.log to see what we are working with: 

```
console.log(myDiv.children);
```

![](@attachment/Clipboard_2020-03-01-13-04-07.png) 9:09

We have both of them. We want the second pararaph so we can reference it using `myDiv.children[1]`. 

`myDiv.children[0]` would be the first p tag and `myDiv.children[1]` is the second one.  Now we can do the following:

```
myDiv.children[1].classList.add('warning');
```

Now we want to remove the first paragraph: 

```
myDiv.firstElementChild.remove();
```

![](@attachment/Clipboard_2020-03-01-13-12-37.png) 9:40

Next we need to create a function called `generatePlayerCard` that takes in three arguments: name, age and height. The function should return HTML that looks like: 

```html
 <div class="playerCard">
   <h2>NAME — AGE</h2>
   <p>They are HEIGHT and AGE years old. In Dog years this person would be AGEINDOGYEARS. That would be a tall dog!</p>
 </div>
```


So first, we create the function that takes in those three parameters:

```
function generatePlayerCard(name, age, height){
  
}
```

Next we eed to have that function return a div with the structure mentioned above. We could do this in two ways: return the HTML directly or stick it in a variable and then return it. 


```
function generatePlayerCard(name, age, height) {
  return `
    <div class="playerCard">
    </div>
  `;
}
```
or

```
function generatePlayerCard(name, age, height) {
  const html = `
    <div class="playerCard">
    </div>
  `;
  return html;
}
```

We will go with the second way for now. 
Now we need to build out the rest of the HTML string and interpolate the parameters variables that have been passed to the function.

```js
function generatePlayerCard(name, age, height) {
  const html = `
    <div class="playerCard">
      <h2>${name} - ${age}</h2>
      <p>They are ${height} and ${age} years old. In Dog years this person would be ${age * 7}. That would be a tall dog!</p>
    </div>
  `;
  return html;
}
```

Refresh the HTML page and let's try calling the function from the console. 

![](@attachment/Clipboard_2020-03-01-13-20-11.png) 12:01

It works! The text doesn't make the most sense but that is okay. If you want an extra challenge, you could take the height value that was passed in centimeteres and if you're from America, you could convert it to feet and inches. You could write a little function that takes in a parameter of centimeters, converts it to feet and inches and returns the value. 

Next step in the excercise is to make a new div with a class of cards. 

```
const cards = document.createElement();
cards.classList.add('cards');
```

Next we need to have that function make 4 cards and append those cards to the div. 

There are a few ways we could do this. Because the function returns a string, we could loop over it four times and create four cards of HTML. Let's demonstrate a few differnt ways to do this. 

We will declare a variable and have it generate the first card's HTML

```
const cardsHTML = generatePlayerCard('wes',12,150);
console.log(cardsHTML);
```

If you refresh the HTML page, you will see an error:
![](@attachment/Clipboard_2020-03-01-13-29-03.png)

That error is being thrown because when we called `document.createElement()` abvoe, we forgot to specify what kind of element we want to create. Modify that code to `document.createElement('div');`. 


![](@attachment/Clipboard_2020-03-01-13-30-11.png) 14:25

Now it works. But how do we keep tacking onto that? We could change `const cardsHTML` to `let cardsHTML` and then do something like:

```
const cardsHTML = gerneratePlayerCards('wes', 12, 150);
cardsHTML = cardsHTML + generatePlayerCard('scott', 12, 150);
cardsHTML = cardsHTML + generatePlayerCard('kait', 12, 150);
cardsHTML = cardsHTML + generatePlayerCard('snickers', 12, 150);
console.log(cardsHTML);
```

NOTE, if you save the code above, prettier might re-format that to use the shorthand code below which is fine because the two ways of typing it out are equivalent.

```
const cardsHTML = gerneratePlayerCards("wes", 12, 150);
cardsHTML += generatePlayerCard("scott", 12, 150);
cardsHTML += generatePlayerCard("kait", 12, 150);
cardsHTML += generatePlayerCard("snickers", 12, 150);
console.log(cardsHTML);
```

Another way would be to create four separate variabels for each of those. Another way would be you could create an array of names and loop over them. We don't know about arrays just yet but we will doing lots of examples with those in the near future. That is the way Wes would probably go about approaching this. 

Another way is we could take the cardsDiv and call

```
cards.insertAdjacentHTML('afterbegin', generatePlayerCard("snickers", 12, 150));
```

And then just call that multiple times , but passing different arguments to generatePlayerCard. 

We will stick with the method we already have. Now we have to append those cards to the div. We will do that using: 

```html
cards.innerHTML = cardsHTML;
```

Next we need to the put the div into the DOM just before the wrapper element. 

We are going to use `insertAdjacentElement` because cards is a proper elements. 

```
div.insertAdjacentElement('beforebegin', cards);
```

If you refresh the HTML page you should see:

![](@attachment/Clipboard_2020-03-01-13-46-47.png) 16:40

Really quickkly, we will add some styles in the HTML page. Add the following: 

```html
<body>
  <script src="./DOM-Cardio.js"></script>

  <style>
    .cards {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 20px;
      padding: 20px;
    }

    .playerCard {
      background: white;
      padding: 20px;
    }

    .playerCard h2 {
      color: black;
    }
  </style>
</body>
```

![](@attachment/Clipboard_2020-03-01-13-48-16.png) 17:35 

The bonus step in the excercise involves putting a delete button on each card so when you click it, it is removed. We haven't gone over how to do this yet, but let's give it a try. 

We will go to where we generate the card and add a button:

```js
  const html = `
    <div class="playerCard">
      <h2>${name} - ${age}</h2>
      <p>Their height is ${height} and  they are ${age} years old. In Dog years this person would be ${age *
    7}. That would be a tall dog!</p>
    <button class="delete" type="button">&times Delete</button>
    </div>
  `;
```

![](@attachment/Clipboard_2020-03-01-13-50-20.png) 18:31

When we click the button, we want to delete the card. To achieve that, we will select all the buttons:

```
const buttons = document.querySelectorAll('.delete');
console.log(buttons)
```

![](@attachment/Clipboard_2020-03-01-13-51-26.png) 19:00

We need to make our delete function. 

```
function deleteCard() {
  console.log("DELETE CARD! TODO");
}
```

Now we can loop over them and attach a click event listener which will call deleteCard

```
buttons.forEach(button => button.addEventListener("click", deleteCard));
```

Now in the `deleteCard()` function, we will pass the event, and let's console.log the events current target.

NOTE: we haven't gone over how to do some of this but it's just bonus! We will go over this in future videos. 

```

function deleteCard(event) {
  console.log(event.currentTarget);
  console.log("DELETE CARD! TODO");
}
```

![](@attachment/Clipboard_2020-03-01-13-54-50.png) 20:09

Inside of `deleteCard` we can assign the button that is the event's current target to a variable 

```
  const buttonThatGotClicked = event.currentTarget;
```

Now we need to grab the parent element. There is a few ways we can do this. 

```
buttonThatGotClicked.parentElement.remove();
```

```
function deleteCard(event) {
  const buttonThatGotClicked = event.currentTarget;
  buttonThatGotClicked.parentElement.remove();
}
```

If you refresh the HTML page and click one of the delete buttons, you will see that is removed. Another way we could have done it is using:

```
  buttonThatGotClicked.closest(".playerCard").remove();

```

What does `closest()` do? It will look at an element and move itself up the tree until it finds something that matches the parameter we pass. That is cool because right now, both of those work, but let's say we change here the button goes. Let's say we put it inside of the paragraph rather than directly inside of the div. If we did that, only the second method would work because the first method would delete the paragraph, not the div. 

The second method will search for the div or any element with a `playerCard` class and remove that. Even though the button has moved, it still works. 


