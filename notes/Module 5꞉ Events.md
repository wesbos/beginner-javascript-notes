---
attachments: [Clipboard_2020-03-01-14-51-59.png, Clipboard_2020-03-01-15-04-15.png, Clipboard_2020-03-01-16-07-01.png, Clipboard_2020-03-01-16-09-14.png, Clipboard_2020-03-01-16-10-58.png, Clipboard_2020-03-01-16-17-35.png, Clipboard_2020-03-01-16-17-38.png, Clipboard_2020-03-01-16-21-03.png, Clipboard_2020-03-01-18-46-10.png, Clipboard_2020-03-01-18-48-58.png, Clipboard_2020-03-01-18-56-25.png, Clipboard_2020-03-01-18-56-26.png, Clipboard_2020-03-01-18-56-28.png]
title: 'Module 5: Events'
created: '2020-03-01T19:37:44.608Z'
modified: '2020-03-01T23:57:21.998Z'
---

# Module 5: Events

## 29 - Events - Event Listener

In this video we will learn about events, event listeners, how to listen to them and how to do stuff when things happen. 


DOM Elements, things that are on the page, they emit events for things like when they are clicked, hovered, dragged, they will fire off events when they are interacted with. 

We can use **event listeners** to listen for when these things happen and react to them. 

You can attach event listeners to all elements, and you can also attach them to the document as well as the window. 

Let's start with a button because that is probably the most common. Go into the `29 - Events` directory within the `/excercises` directory and open the `events.html` file. 

In the body, let's add a button with a class of "butts".

```html
 <button class="butts">Click Me!</button>
  <script src="./events.js"></script>
```

Create a file called `events.js` if it's not already there. 

If you open the html file, you should see the button and when you click it, nothing should happen. 

![](@attachment/Clipboard_2020-03-01-14-51-59.png) 1:32

In order to attach event listeners, you first need to select the element you want to attach it to.

```
const butts = document.querySelector('.butts');
```

Now we will call `addEventLisetner()` on the butt element. Event listeners will usually take two arguments: first, what the type of event is that you want to listen to, and then second, you need to pass a **callback function**. 

A callback function is just a regular function, it's just a word we use to describe when a pass a function to a method that will then be called at a later point in time. Instead of us calling the function, we provide the name, reference to a function to `addEventListener` and then the browser will take care of calling or runing that function for us when it needs to. 

The callback function is our way of saying to the browser, hey, when the butts button is clicked, can you please do me a favour and call this function? 

One of the more common ways to pass the callback function is as an anonymous function. 

For example: 

```
butts.addEventListener('click', function(){

});
```

`function(){}` is the second argument that we have passed to the event listener in the example above. 

Inside of that function, we can do whatever it is we want when the things gets clicked. We want to `console.log('IT GOT CLICKED!!!');`

Now, if you click the button, you will see that logged in the console each time you click. 

![](@attachment/Clipboard_2020-03-01-15-04-15.png) 4:24

NOTE: for the click event on a button, you don't have to worry about thinking about keyboard events, if the user hits enter to click the button instead of click it, because it's a standard button, the browser will still trigger the click event. 

There are three steps with event listeners:
1. Go get something
2. Listen for someting (click)
3. Do something

There is a lot more to event listeners, which we will dive into now. 

In our example above, we passed in an anonymous function (because there is no name to the function, no way for us to reference that function outside of the listener). 

However, we can also create a named function and pass it in a reference. What Wes often likes to do before creating the event listener is to make a function like

```
function handleClick(){
  console.log('IT GOT CLICKED!!!!!!!!');
}
```

Note: the naming of the function to use the word `handle` is not a best practice, but it's often something that Wes does. He will name the callbacks with 'handle', which tells him that it is a specific function that gets passed in to an event handler. 

Now we can do 

```
butts.addEventListener('click', handleClick);
```

We can still call `handleClick` from elsewhere in our code this way and also from within the console. 

You might notice that we are passing the reference the function using `butts.addEventListeners('click', handleClick);` rather than doing `butts.addEventListeners('click', handleClick());`. 

If you try to run the code with `handleClick()` instead of `handleClick` and refresh the page, you will see the message "IT GOT CLICKED" in the console before we ever click the button. That is because it s running on page load when we pass the function in using `handleClick()`. 

Unless the function were to return another function, which is something that can happen, you don't actually have to call the function yourself. Why? The browser will run the function for us. We simply pass it a reference so it knows what to run when the time comes. 

What benefit is there to having the function that we are passing to the event listener outside of the function?  There are a couple of things. 

Let's add another button to the HTML page. 

If we have another button, `<button class="cool">Click me also!</button>`, if we want to listen on the cool button, we can.

```
coolButton.addEventListener('click', handleClick);
```

Now it doesn't matter which button you click, both of them are referring to that same function.

If instead of re-using the `handleClick` function we wanted to create anonymous functions and pass it two both eventlisteners separately, that would still work ,but if you thnk of scaling that up to a whole bunch of buttons, then you have to make sure you reference every one of the buttons which is not very **DRY** (don't repeat yourself). 

So the first benefit is that it makes the code more DRY. 

The second benefit is if you want to remove an eventListener from an element, you must have reference to the function. 

`removeEventListener()` takes two arguents, the event, and then the function.  

It is not possile to remove the event listener from all the click events for example. You need to pass in the reference to the function you want to stop listening on. 

```
butts.removeEventListener('click', handleClick);
```

If you refresh the HTML page, you will see the event listener no longer works.

That is called **unbinding**. 

What does **binding** mean? A binding essentially means taking a function and listening for a specific click within an element. In our examples above, the `handleClick` function was bound to the `butts` element, the `coolButton` element is also bound to the `handleClick` function and when we take it off, we are **unbinding** that function from that element. 

So if you want to remove the event listener, you _must_ have reference to the original function. 

If we had done an anonymous function, we couldn't have removed the click handler. Even if you were to pass the exact same anonymous function to remove, like below, it still would not work. 

```
butts.addEventLisetner('click', function(){
  console.log("I am an anon!");
});
butts.removeEventListener("click", function(){
  console.log("I am an anon!");
});
```

It does not work. That is because there is no way to reference the actual function we wanted to remove. 

If you ever in the future need to remove an event listener, remember not to use an anonymous function. 

Here is how you would do it wiht an arrow function. 

```
const hooray = () => console.log("HOORAY!");
coolButton.addEventLIstener('click', hooray);
```

The `hooray` function is technically an anonymous function, but because we have stored it in a variable, it will infer the function from the variable name and we can still reference it because it's stuck in a variable. 

Those are the basics of event listeners. We are going to go into what are the other events that are out there as well and how we can create our own custom events. A really handy thing is the ability to emit a buy button or buy event, or you want to emit a success event or something. It's handy to be able to emit your own events and then listen to them like you're listening to regular clicks. 

### Listening to events on multiple items

This is a very common thing. Let's say you have 40 buttons on the page and anytime you come across a specific type of button or any time you come across a specific type of image, or anything like that, you want to listen for the event for all of the things that are on that page.     


In our HTML page, add the following: 

```html
    <button class="buy">Buy Item 1</button>
    <button class="buy">Buy Item 2</button>
    <button class="buy">Buy Item 3</button>
    <button class="buy">Buy Item 4</button>
    <button class="buy">Buy Item 5</button>
    <button class="buy">Buy Item 6</button>
    <button class="buy">Buy Item 7</button>
    <button class="buy">Buy Item 8</button>
    <button class="buy">Buy Item 9</button>
    <button class="buy">Buy Item 10</button>
```

Note: Wes used an Emmet shortcut to create this text by writing `button.buy{Buy Item $}*10` and then hitting tab to expand the HTML. 

Now how can you listen for a click on all of them? It doesn't make sense to have to select all 10 of them and then have to attach an event listener 10 times. That is actually what we are doing, but there is a much more efficent way. 

First we need to select all the buttons. 

```js
const buyButtons = document.querySelectorAll("button.buy");
```

This gives us a node list of all of the buttons. 

![](@attachment/Clipboard_2020-03-01-16-07-01.png) 41:48

You might think, why can't we just go ahead and take our buy buttons and add an event listener of click like so :

```
function buyItem(){
  console.log('BUYING ITEM');
}
buyButtons.addEventLIstener('click', buyItem);
```

So we have our elements, we listened for them, and then when that happens, we passed the function to run. You should see the following error when you reload the HTML page and look at the console. 

![](@attachment/Clipboard_2020-03-01-16-09-14.png) 15:41

The error is telling us taht the buy buttons does not have the method `addEventLisetner`. Let's take a look at the buyButtons by console logging them `console.log(buyButtons);`. 

If you ever want to see what all of the diferent methods are that are available on a variable you can look at the prototype. 

![](@attachment/Clipboard_2020-03-01-16-10-58.png) 16:05

You will notice that `addEventListener` is not there. If we were to `console.dir(butts);`, and you expand the prototype, you will see `addEventListener` somewhere in the giant list. 

So if you want to add the event listener to all the buy buttons, we have to loop over and for each element attach it individually. 

We haven't learned about loops just yet, but we should be able to do this. 

You may have noticed that in the `buyButtons` proptype, there was a metho called `forEach`. That is going to allow us to loop over each of the items. 

Note: Wes often takes all the selectors are the top of the file rather than anywhere in the code. For this example, we are going to keep it within the middle of the file. Both methods work, putting it at the top is just a personal preference of Wes'. 

We will take the buyButtons and call the `forEach()` method on them. `forEach` is a method that will run a function for each item in our node list. We can pass it an anonymous function, which is common when we are looping since we don't have the same limitations as we did in event listeners. 

`forEach` function will give you an argument that is the each of the individual buttons, and we can name it whatever we want. We will call it `buyButton`. That is just a parameter (aka a placeholder) and the browser will pass us a variable called buyButton when it runs it for us. 

```
buyButtons.forEach(function(buyButton)){
  console.log(buyButton);
}
```

If you run that, you should see all the buy buttons logged in the console. 

![](@attachment/Clipboard_2020-03-01-16-17-38.png) 18:42

Anything you put in our forEach loop will happen 10 times, once per button. 

Now that we have the individual elements that are on the page, we can use the `addEventListener()` method to add the event listener to each. 

```
buyButtons.forEach(function(buyButton) {
  console.log('Binding the buy button');
  buyButton.addEventListener("click", buyItem);
});
```

If you refresh the page, you will see the "Binding the buy button" text was triggered 10 times and if you click each of the buttons, you should see the text BUYING ITEM logged 10 times. 

![](@attachment/Clipboard_2020-03-01-16-21-03.png) 19:46

Similarly, if you want to remove the event listener from each of those, you have to loop over each of them as well.

Something to note, which is a big hurdle, is that the parameter `buyButton` inside of our forEach function can be named anything. 

Let's say we have a function called `handleBuyButtonClick` (NOTE: Wes mentions that this function was named misleadingly... it is not actually a handler, the handler is `buyItem`). 


What we can do is take the code out of the foreach anonymous function and move it to the `handleBuyButtonClick` function like so:

```js
function handleBuyButtonClick(buyButton){
  console.log('Binding the buy button');
  buyButton.addEventListener("click", buyItem);
}
buyButtons.forEach(handleBuyButtonClick);
```

We have made `handleBuyButtonClick` a named function,  which takes in a parameter of `buyButton` which we could have named anything that we want. It is a paremter or a placeholder that we are not supplying, the browser will run the forEach function and it knows that it will pass as the first argument, the element that got clicked. 

If you renamed the parameter to `oprah` it would still work, like so:

```js
function handleBuyButtonClick(oprah){
  console.log('Binding the buy button');
  oprah.addEventListener("click", buyItem);
}
```

Other things is that you will often see that people use arrow functions as well for the handlers. 

For example:

```
buyButtons.forEach((button)=>{
  button.addEventListener('click', ()=>{
    console.log("You clicked it!")
  })
})
```

That will work just as well. Arrow functions work fine. The only downside for using the arrow function for your event listener like we  did in the example above is that you cannot unbind it because it's an anonymous function in this case. 

---

## 30 - Events - targets, bubbling, propagation and capture. 

The **event object** is a gold mine of information about what happens when an event fires. Remove everything in the `events.js` file after the `buyButtons` variable declaration.

We are going to loop over every single buy button and attach a handler to it. 

Create a new function, `handleByButtonClick` and console log "You are buying it". We will pass this function to each button's click event listener. 

```
buyButtons.forEach(function(buyButton) {
  buyButton.addEventListener("click", handleBuyButtonClick);
});
```

Now the question is: when a user clicks one of the buttons, how do I get informatino about what button is being clicked? 

If I have one function that is being called by 10 different button event listeners, how do I know which of the 10 triggered the function?

That information is hidden inside of the event object. The event object is filled with all sorts of information and methods to work with your event. 

To access the event object, we modify our callback function (our handler), to accept a param that is the event. Refresher from earlier: parameters are placeholders. So we can add the following parameter, `event` to `handleBuyButtonClick()`:

```
function handleBuyButtonClick(event ){
  console.log('You are buying it');
}
```

We could call the `event` parameter anything, as long as it's the first param in our callback function. Why? Because when the browser runs the `handleBuyButtonClick` function for us when someone clicks it, it will run the function and pass to us a number of arguments, the first of which is the event object. 

 Within the `handleBuyBackButtonClick()`, add `console.log(event)` and refresh the HTML page. Now when you click on a button you should see the following in the console:

 ![](@attachment/Clipboard_2020-03-01-18-46-10.png) 3:49

 What we have there is a pointer event, which we will get into more detail about later, but essentialy we have clicks, and touches and mouse movements and they are all consolidated into one event called a pointer event.  

![](@attachment/Clipboard_2020-03-01-18-48-58.png) 4:!8

If you expand the event, you will see all sorts of things. 

**isTrusted**: this is a boolean that will tell you if the click was actually coming from someone's mouse (because it is possible to fake event clicks). If you are making a game, you probably won't want someone to programmatically click on items. 

**pressure**: on newer iPads and other devices, there is pressure sensitivity. 

It tells us `screenX`, `screenY`, `clientX`, `clientY`, `pageX` and `pageY`. Those are details as to where in the screen and where in the page the person has clicked, as well as a bunch of other information like what element was clicked on. 

The one we are interested in is `target` and `currentTarget`. 

Within `handleBuyBackButtonClick`, add `console.log(event.target);`. Now when you refresh and click on different buttons, it will show you which button the user has clicked on. 

![](@attachment/Clipboard_2020-03-01-18-56-28.png) 5:43

That is very useful because we could do something like add a data attribute, such as `data-price=""`.

6:01


