---
attachments: [Clipboard_2020-05-07-19-46-46.png, Clipboard_2020-05-07-20-30-57.png, Clipboard_2020-05-08-06-15-54.png, Clipboard_2020-05-08-06-19-08.png, Clipboard_2020-05-08-06-21-56.png, Clipboard_2020-05-08-06-21-58.png, Clipboard_2020-05-08-06-25-50.png, Clipboard_2020-05-08-06-26-29.png, Clipboard_2020-05-08-06-26-44.png, Clipboard_2020-05-08-06-28-04.png, Clipboard_2020-05-08-06-29-13.png, Clipboard_2020-05-08-06-29-54.png, Clipboard_2020-05-08-06-30-45.png, Clipboard_2020-05-08-06-31-37.png, Clipboard_2020-05-08-06-37-41.png, Clipboard_2020-05-08-06-38-21.png, Clipboard_2020-05-08-06-39-09.png, Clipboard_2020-05-08-06-39-23.png, Clipboard_2020-05-08-06-40-00.png, Clipboard_2020-05-08-06-43-54.png, Clipboard_2020-05-08-06-55-27.png, Clipboard_2020-05-08-06-59-35.png, loupe-0-timer.gif, loupe-gif.gif, loupe-interval.gif, loupe-multi.gif]
title: 'Module 12: Advanced Flow Control'
created: '2020-05-07T23:18:40.737Z'
modified: '2020-05-08T11:38:05.457Z'
---

# Module 12: Advanced Flow Control 

## 66 - The Event Loop and Callback Hell 

Before we get into promises, we need to talk about how Javascript is asynchronous and how the event loop works. 

You may often hear that almost everything in Javascript is non-blocking (asynchronous). What does that mean?

For us to understand that, we need to first talk about how Javascript events work.

Javascript is a single threaded language, meaning that only one thing can be run at a time. Some other languages are multi-threaded, which means they can run multiple processes at once. Because Javascript is single threaded, which means we can only run one thing at a time. 

Let's visualize that with some examples. Open up the `event-loop.html` file within the `exercises/` directory. 

Let's add two logs witin our script tag and then refresh the page to check them. 

```
console.log('Starting');
console.log('ending');
```

![](@attachment/Clipboard_2020-05-07-19-46-46.png) 00:58

No one is surprised by that.

Let's add some code in between the two logs. In this demo we want to wait for two seconds, which we could do with a timeout. 

```
console.log('Starting');
setTimeout(function(){
  console.log('Running');
}, 2000);
console.log('ending');
```

Now if you refresh the page, what will you see? 

You might expet to see starting, running, ending, but instead we get Starting, ending, and then running. 

![](@attachment/Clipboard_2020-05-07-20-30-57.png) 1:20

Why is that not in the order that we coded it in? Shouldn't the timeout cause the code to pause for two seconds, log running and then log ending?

It doesn't work that way. 

The way that Javascript works is it will parse the first line and log Starting. 

Next, it will parse the next few lines which is the `setTimeout()` function. It will say okay I won't do anything yet but after two seconds I will come back to this code. It moves on and logs "ending". 2 seconds later, the callback that the `setTimeout` function queued up comes back and is executed.  That is what is referred to as the **call stack**. 

The call stack and event loop is a pretty complicated thing to understand. Instead of Wes trying to explain it, he has some homework for us. Philip Roberts has an amazing talk where he expxlains the event loop. You do not have to watch it before continuing with the course but it's probably one of the most popular Javascript talks ever given and he does an excellent job of explaining the event loop.

https://www.youtube.com/watch?v=8aGhZQkoFbQ 

Philip Roverts also built this cool little tool called loupe which will help us visualize the callstack.

![](@attachment/Clipboard_2020-05-08-06-15-54.png) 3:23 

We have already looked at the callstack in Javascript and we have seen when you click something, it gives you a trail of what functions were called up to then. 

However we know that the call stack can only ever run one function at a time. So what happens in a scenario like our example where you have two logs between a setTImeout. 

![](@attachment/Clipboard_2020-05-08-06-19-08.png) 3:48

Javascript is asynchronous. What that means is that Javascript won't stop running that code, instead if will put it off in what we call the web API, and when that comes back after two seconds, it is going to stick it in the callback queue. 

When the call stack has a free second, when it's not currently running anything, it is going to reach into the callback queue, grab the callback and run it for us. 

Let's go ahead and take the code and paste it into the loupe page. 

Note: at the time Wes is recording the video, the tool is a bit outdated and does not handle arrow functions, or back ticks so just use regular function declarations.

Wes is going to modify his timeout to 7 seconds instead of 4 so we can talk to us. 

![](@attachment/Clipboard_2020-05-08-06-21-58.png) 4:34

Once you have done that click save and run. 

![](@attachment/loupe-gif.gif)

The first thing that it runs our log. 

![](@attachment/Clipboard_2020-05-08-06-29-13.png) 4:51

Next it runs our time out function. 

![](@attachment/Clipboard_2020-05-08-06-29-54.png) 4:53

It seems that there is a callback so it puts that in our Web Apis. 

![](@attachment/Clipboard_2020-05-08-06-30-45.png) 4:54

When the callback is done waiting, it will stick it into the callback queue. 

![](@attachment/Clipboard_2020-05-08-06-31-37.png) 5:00

If the call stack has nothing else to do at the time, it will reach into the queue and grab the next thing.

So the callstack is what Javascript itself is doing. 

The Web Apis are things that are waiting or things that we are listening for like event handlers (if we were listening for a click on a button, that would go in our web apis). 

When something happens in the Web Api (like the click of a button or a timer that has finished), it will stick the callback into the callback queue which the call stack will reach into when it has nothing left to do.

Let's say after our `setTimeout` we wanted to add an interval that logs BOOP every 100 miliseconds.

Let's name the function `boop` so we can visualize it more easily. 

![](@attachment/Clipboard_2020-05-08-06-37-41.png) 6:07

The first log and setTimeout behave just like they did before. When it gets to `setInterval`, we already have a callback for setTimeout in the web apis.

![](@attachment/Clipboard_2020-05-08-06-38-21.png) 6:12

Then it logs ending. 

![](@attachment/Clipboard_2020-05-08-06-39-09.png) 6:12

Next `setInterval` runs. 

![](@attachment/Clipboard_2020-05-08-06-39-23.png) 6:13

Now every second you can see that it keeps going back to our boop function. 

![](@attachment/Clipboard_2020-05-08-06-40-00.png) 6:18


![](@attachment/loupe-gif.gif) 6:26

One thing Wes wants to show us is that even if the `setTimeout` duration was set to 0

```
setTimeout(function(){
  console.log('Running');
}, 0);
console.log(ending);
```

If you refresh the page and look at the console, you will see that we still get 
>Starting
>ending
>Running

![](@attachment/Clipboard_2020-05-08-06-43-54.png) 6:40

Even though the timeout happens after 0 seconds, what happens is Javascript runs the first line, then runs the setTimeout and queues up the callback to happen after 0 seconds, then it runs the next line and even though the timeout is 0 seconds, it still adds it to the web api which in turn adds it to the callback queue. Because the browser was already busy with the log, it runs the callback after. 

Let's demo that in loupe. 

![](@attachment/loupe-0-timer.gif) 

It logs, runs setTimeout, puts running in the web api which puts it in the call back queue, and then when the "ending" log is finished executing, javascript grabs from the callback queue and runs it. 

As a beginner and intermediate web developer you don't have to understand all the nitty gritty of the call stack and event loop. 

What is really important that you understand is javascript is single threaded, meaning that the callstack can only ever run one thing at a time. 

Let's run the default example on loupe that is supplied to demonstrate what happens when multiple things are queued up. 

The example is in jQuery but it's the same idea. When you click a button, we set a timer for 2 seconds that says you clicked me, then it logs "hi" then another timer is set for 5 seconds, and then it logs welcome to loupe.

![](@attachment/Clipboard_2020-05-08-06-55-27.png) 8:55

![](@attachment/loupe-0-timer.gif)  

How that works is first the click listener goes on the callstack and gets put into the web apis, then the event listener is added. The hi is run and logged, and after that the timer also gets put in the web apis, and then it logs welcome to loupe. 

Once the timer is finished, it will get moved to the callback queue. 

Now everytime we click the button it sticks an event handler in the queue and you can see the callstack is reaching in and grabbing the next callback to handle itself. 

![](@attachment/Clipboard_2020-05-08-06-59-35.png) 9:10

So how do we deal with a scenario in Javascript where we do actually want to wait for something. Let's say we wanted to go off to an API and grab some data and then come back to it, we shouldn't have to freeze up the entire browser, or we shouldn't have to stop everything else in the browser while that goes and fetches it.

Instead what we want is to send off the fetch request and to go and get the data and then carry on with the rest of our life. When the data does come back to us, we can deal with it, very similarly to how `setTimeout` will run the callback after the alloted time. 

Callbacks are great, but it is very difficult to orchestrate multiple things at once. 

Let's try with an example. 

What we want to do is make a div and do a few things to it: 
1. change the text to GO when clicked
2. Make it a circle after 2 seconds
3. Make it red after 0.5s
4. make it a square after 0.25 seconds
5. make it purple after 0.3s
6. fade out after 0.3s

That is not an uncommon thing in javascript, where you have to perform some things in a series, one after the other.

What we will do is make a div within the body tag and give it a class of go. 

```
<div class="go">Click Me</div>
```

Comment out all the other code we have in the script tag and let's start with selecting the div and changing the text to go when clicked. 

```
go.addEventListener('click', function(e){
  const el = e.currentTarget;
})

```

stopped at 11:40

























---

## 67 - Promises

---

## 68 - Promises - Error Handling

---

## 69 - Refactoring Callback Hell to Promise Land

---

## 70 - Async Await

---

## 71 - Async Await Error Handling

---

## 72 - Async Await Prompt UI

---

## 73 - Async Typer UI - two ways
