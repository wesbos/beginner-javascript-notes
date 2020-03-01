---
attachments: [Clipboard_2020-03-01-14-51-59.png, Clipboard_2020-03-01-15-04-15.png]
title: 'Module 5: Events'
created: '2020-03-01T19:37:44.608Z'
modified: '2020-03-01T20:27:01.853Z'
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

The second benefit is if you want to remove an eventListener from an element, you must have reference to the function. `removeEventListener()` takes two arguents, the event, and then the function.  It is not possile to remove the event listener from all the click events for example. You need to pass in the reference to the function you want to stop listening on. 

```
butts.removeEventListener('click',          )
```

stopped at 9:22
