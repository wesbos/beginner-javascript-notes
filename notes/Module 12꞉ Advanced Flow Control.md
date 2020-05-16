---
attachments: [Clipboard_2020-05-07-19-46-46.png, Clipboard_2020-05-07-20-30-57.png, Clipboard_2020-05-08-06-15-54.png, Clipboard_2020-05-08-06-19-08.png, Clipboard_2020-05-08-06-21-56.png, Clipboard_2020-05-08-06-21-58.png, Clipboard_2020-05-08-06-25-50.png, Clipboard_2020-05-08-06-26-29.png, Clipboard_2020-05-08-06-26-44.png, Clipboard_2020-05-08-06-28-04.png, Clipboard_2020-05-08-06-29-13.png, Clipboard_2020-05-08-06-29-54.png, Clipboard_2020-05-08-06-30-45.png, Clipboard_2020-05-08-06-31-37.png, Clipboard_2020-05-08-06-37-41.png, Clipboard_2020-05-08-06-38-21.png, Clipboard_2020-05-08-06-39-09.png, Clipboard_2020-05-08-06-39-23.png, Clipboard_2020-05-08-06-40-00.png, Clipboard_2020-05-08-06-43-54.png, Clipboard_2020-05-08-06-55-27.png, Clipboard_2020-05-08-06-59-35.png, Clipboard_2020-05-08-20-01-54.png, Clipboard_2020-05-08-20-05-09.png, Clipboard_2020-05-08-20-09-15.png, Clipboard_2020-05-08-20-11-45.png, Clipboard_2020-05-08-20-16-18.png, Clipboard_2020-05-11-07-07-09.png, Clipboard_2020-05-11-07-11-39.png, Clipboard_2020-05-11-07-14-47.png, Clipboard_2020-05-11-07-19-32.png, Clipboard_2020-05-11-07-20-48.png, Clipboard_2020-05-11-07-21-16.png, Clipboard_2020-05-11-07-27-24.png, Clipboard_2020-05-12-06-45-31.png, Clipboard_2020-05-12-06-50-19.png, Clipboard_2020-05-12-06-50-58.png, Clipboard_2020-05-13-18-25-48.png, Clipboard_2020-05-13-18-36-33.png, Clipboard_2020-05-13-18-42-40.png, Clipboard_2020-05-13-18-48-06.png, Clipboard_2020-05-13-18-53-48.png, Clipboard_2020-05-13-18-53-52.png, Clipboard_2020-05-13-18-53-54.png, Clipboard_2020-05-14-07-53-01.png, Clipboard_2020-05-14-07-55-32.png, Clipboard_2020-05-14-08-05-54.png, Clipboard_2020-05-14-08-07-15.png, Clipboard_2020-05-14-08-08-07.png, Clipboard_2020-05-14-08-09-12.png, Clipboard_2020-05-14-08-13-58.png, Clipboard_2020-05-14-08-15-32.png, Clipboard_2020-05-14-08-17-26.png, Clipboard_2020-05-16-16-02-08.png, Clipboard_2020-05-16-16-12-34.png, Clipboard_2020-05-16-16-13-20.png, Clipboard_2020-05-16-16-26-37.png, loop-animation.gif, loupe-0-timer.gif, loupe-gif.gif, loupe-interval.gif, loupe-multi.gif]
title: 'Module 12: Advanced Flow Control'
created: '2020-05-07T23:18:40.737Z'
modified: '2020-05-16T20:42:33.247Z'
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


When the div is clicked, we will grab the event and save the div element in a variable `el`. The reason we are saving that in a variable will  make sense in just a second.

```
go.addEventListener('click', function(e){
  const el = e.currentTarget;
  console.log(el);
})
```

![](@attachment/Clipboard_2020-05-08-20-01-54.png) 12:02

As you can see, we have the div.  

Let's add some default styling there. Add style tag on the page with some styling. 

```
.go { 
  margin: $rem;
  background: white;
  background: 5rem; 
  width: 25rem;
}
```

Now when you refresh the page, your button should look like this: 

![](@attachment/Clipboard_2020-05-08-20-05-09.png) 12:43

Now we have to make it a cirlce after two seconds. We ccan do that by adding a `setTimeout`. 

```
go.addEventListener('click', function(e){
const el = e.currentTarget;
console.log(el);
setTimetout(function(){
  el.classList.add('circle');
}, 2000);
});
```

Now back in our style tag, let's add a border radius of 50% for the class circle. 

```
.go.circle {
  border-radius:50%;
}
```

![](@attachment/Clipboard_2020-05-08-20-09-15.png)

If you refresh the page you will see that the div style changes to a cirlce after 2 seconds. We forgot to change the text when clicked for step one so right before the `setTimeout` add 👇

```
el.textContent = 'GO!';
```

Let's put a height on the go css style class as well so that it is square. 

![](@attachment/Clipboard_2020-05-08-20-11-45.png) 13:38

We can add a transition on there too.


```
.go { 
  margin: $rem;
  background: white;
  background: 5rem; 
  width: 25rem;
  height:25rem;
  transition: all 0.2s; 
}
```

After 0.5 seconds we need to make it ren. Let's add anotehr `setTimeout` to do that.


```
go.addEventListener('click', function(e){
const el = e.currentTarget;
console.log(el);
  setTimetout(function(){
      el.classList.add('circle');
      setTimeout(function(){
        el.classList.add('red');
      }, 500);
    }, 2000);
});
```

Let's add the follow css styles to the css class "red" and to purple. 

```
.go.red {
  background:red;
}

.go.purple {
  background: purple;
  color: white;
}
```

![](@attachment/Clipboard_2020-05-08-20-16-18.png) 14:31

Now after 0.25 seconds we need to make it a square. 


```js
go.addEventListener("click", function(e) {
      const el = e.currentTarget;
      console.log(el);
      //1. make it a circle after 2 seconds
      setTimeout(function() {
        el.classList.add("circle");
        //2. make it red after 0.5s
        setTimeout(function() {
          el.classList.add("red");
          //3. make it square after 0.3
          setTimeout(function() {
            el.classList.remove("circle");
          }, 300);
        }, 500);
      }, 2000);
    });
```

Now we need to make it purple after 0.3 seconds.

Add these  styles 👇

```css
.go.purple {
  background: purple;
  color: white;
}
```

```js
go.addEventListener("click", function(e) {
      const el = e.currentTarget;
      console.log(el);
      //1. make it a circle after 2 seconds
      setTimeout(function() {
        el.classList.add("circle");
        //2. make it red after 0.5s
        setTimeout(function() {
          el.classList.add("red");
          //3. make it square after 0.3
          setTimeout(function() {
            el.classList.remove("circle");
            //4. make it purple after 0.3s
            setTimeout(function() {
              el.classList.remove("red");
              el.classList.remove("purple");
              //5. fade out after 0.5 seconds
              setTimeout(function(){
                el.classList.add('fadeOut');
              })
            }, 300);
          }, 300);
        }, 500);
      }, 2000);
    });

```

Add this style

```css
.go.fadeOut {
  opacity: 0;
}
```


![](@attachment/loop-animation.gif) 16:44

That was a really simple animation and look at all this, this is what is referred to as callback hell.

Callback hell is if you must do things one after the other, you must nest things inside of each other because they all depende on the previous callback to being called before it can then go ahead and run. 

It is also redered to as "Christmas Tree" code because of how indented the code is sideways.

It's not all that great. 

The solution to call-back hell is the "promise" land. 

Promises are a sort of IOU for something that will happen in the future. They allow us to write code that is much easier to look at. 

We will be looking at that in the next video. 

---

## 67 - Promises

The solution to callback hell is to use a promise, and although we haven't covered that yet, we will now. 

Promises are an IO for something that will happen in the future. 

If you think of our timer, data being returned from an API or someone giving access to a webcam, when we request or start those things, what we often get in return is not the immediate data back, because those things take time. Instead of getting the immediate data returned, we get a promise. 

You can think of a Promise as a litlte ticket you have in your hand that says "I might get a timer, or some data at some point" and eventually at some point we will get some data back (it can also fail which is called rejecting). 

Or, if you are asking for a user's webcam, like we did in our Face Detection exercises, we were asking for a user's webcam using the code below.

```
const stream = await navigator.mediaDevices.getUserMedia({
  video: { width: 1280, height:720 },
});
video.srcObject = stream;
await video.play();
```

We had to wait for the user to give us access to their webcam before playing the video. That happens all the time in Javascript, and that is what a promise is.

In our `playground` directory, let's make a `promises.html` file. Let's give ourselves the base HTML and then lets add a script tag.

```
<script>
function makePizza(){

}

</script>
```

Inside of this script tag, we are going to make a pizza promise. You can't make a pizza instantly. You gotta put the toppings on, the pepperoni on, that takes time. 

If you were to order a pizza by phoning them or doing it online, they will immediately give you some sort of order number. That order number is not the pizza -- you cannot eat it, but you know that the order number or that receipt is a promise that they will give it to you when its finished. 

So what we need to do is to make a promise and then return it from our function immediately.

```
function makePizza(){
  const pizzaPromise  = new Promise();
  return pizzaPromise;
}
```

Promises are made immediately, but they do not resolve immediately (they resolve once the timer is finished or the data comes back). 

That idea of returning happening immediately and resolving happening when it's done is really important. 

A promise takes a callback function, and that calback function is going to give us two arguments. We get the `resolve` function and the `reject` function (first will always be resolve, second will always be reject). 

Now what you can do is when you are ready, you can resolve the promise or if something went wrong you can reject it. 

```
function makePizza(){
  const pizzaPromise = new Promise(function(resolve. reject){
    resolve('');
  });
  return pizzaPromise;
}
const pizza = makePizza();
console.log(pizza);
```

Now if we refresh the page, what do you think we will get in the console? Will we get the pizza or something else, like a promise.

![](@attachment/Clipboard_2020-05-11-07-07-09.png) 4:39

If you refresh the page, you should see the promise. What is important to note is that our `makePizza` function doesn't give us the pizza, it givs us the promise of pizza, that at some point in the future, we will either resolve a slice of pizza or reject it if something went wrong.

Let's make the function a bit more robust.

We will take in some toppings and will resolve using back ticks. Modify the code like so to make a `pepperoniPomise` and a `canadianPromise` like so:

```
function makePizza(toppings){
  const pizzaPromise = new Promise(function(resolve. reject){
    resolve(`Here is your pizza 🍕 with the topppings ${toppings.join(' ')`);
  });
  return pizzaPromise;
}
const pepperoniPromise = makePizza('[pepperoni]');
const canadianPromise = makePizza(['pepperoni', 'mushroom', 'onions'])

console.log(pepperoniPromise, canadianPromise);
```

![](@attachment/Clipboard_2020-05-11-07-11-39.png) 6:09

As you can see, we get our two promises. But how do we get the actual pizza itself? This is a bit confusing because the devtools will show you the value when it is resolved, but in Javascript if you actually want to access the value of the pizza, you cannot say `pepperoniPromise.value` or anything. 

The way that we can access it by using the `then()` method, which takes in a callback method. The callback method will pass you the pizza, which we will then log. 

```
pepperoniPromise.then(function(pizza){
  console.log("Ahh I got it!");
  console.log(pizza);
});
```

Now when you refresh the page you should see the following..

![](@attachment/Clipboard_2020-05-11-07-14-47.png) 7:00

At this stage, you might be wondering "why are you doing it like this Wes? this seems like a much harder way to just return data".

The reason for that is we haven't introduced any time delays in our example so let's go ahead and do that. We will add a 1 second wait for the pizza to cook using `setTimeout` and then call `resolve` from within that timeout. 

```js
function makePizza(toppings){
  const pizzaPromise = new Promise(function(resolve, reject){
    //wait 1 second for the pizza to cook
    setTimeout(function(){
      resolve(`Here is your pizza 🍕 with the topppings ${toppings.join(' ')`);
    }, 1000)
    //if something went wrong, we can reject this promise
  });
  return pizzaPromise;
}

const pepperoniPromise = makePizza(['pepperoni']);
pepperoniPromise.then(function(pizza){
  console.log("Ahh I got it!");
  console.log(pizza);
});
```

If you refresh the page, you will see in the console that we get our promise immediately and then a second after actually have access to our pizza. 

![](@attachment/Clipboard_2020-05-11-07-19-32.png) 7:59 

That is a great example of how we sometimes have to wait.

Often what you will see is instead of making a promise and then returning it, people will often just return the promise immediately. 

![](@attachment/Clipboard_2020-05-11-07-20-48.png) 8:27

The logic to how a Promise gets resolved is always inside of the Promise body.

![](@attachment/Clipboard_2020-05-11-07-21-16.png) 8:36

That function will resolve or reject whenever it feels ready. In our case, we feel like the pizza is ready after one second.

So what is happening here is when we declare our `pepperoniPromise` we can call `makePizza(['pepperoni'])`, which returns a promise of pizza. In order to get the pizza, the way we can access the resolved value is by chaining a `.then` onto it. 

```
console.log('Starting');
pepperoniPromise.then(function(pizza){
  console.log('Ahhh got it!');
  console.log(pizza);
});
console.log('finishing');
```

When you fresh the page you will see that we get "Starting" then "finishing" then the I got it message. 

![](@attachment/Clipboard_2020-05-11-07-27-24.png) 9:21

We will look at how we can use `async await` to actually do that sequentially if we would like to, but for now we know we can chain a `.then()` onto it.

Why is that any more useful than a regular callback? That is useful becaue let's say we wanted to make multiple pizzas one after the other, and let's say we have an oven that can only cook one at at time. 

Delete our `canadianPizza` and `pepperoniPizza` declaration code and everything below it in the script tag and just leave this: `makePizza(['pepperoni'])`. 

We can chain a `.then()` immediately onto it (because `makePizza` returns a promise), which gives a function that has a pizza. Let's just log the pizza so that we know that it still works. 

The neat thing is if from this `then()` we return another `makePizza`, you can then chain another `.then()` on that function. 


```
makePizza(['pepperoni', 'ham']).then(function(pizza){
   console.log(pizza);
   return makePizza(['ham', 'cheese']);
}).then(function(pizza){
  console.log(pizza);
})
```

As you can see first we get one pizza and then after a second we see the other pizza logged to the console. 

![](@attachment/Clipboard_2020-05-12-06-45-31.png) 11:03

You can chain as many as you want. 

Often people like to organize the code so that each `.then()` is on it's own line to make it more readable as you see below.


```
makePizza(['pepperoni', 'ham'])
  .then(function(pizza){
    console.log(pizza);
    return makePizza(['ham', 'cheese']);
  })
  .then(function(pizza){
    console.log(pizza);
    return makePizza(['hot peppers','onion', 'feta']);
  })
  .then(function(pizza){
    console.log(pizza);
  })
```

Unlike what we were doing the lesson where we were adding and removing classes which were all nested in callback hell, this chaining of `then` is the promise land and it allows us to keep all of our logic one level deep.

The downside to that is if you had a log of First and After all our promise chaining, both logs would execute before any of our pizzas are logged. 


```js
console.log('First');
makePizza(['pepperoni', 'ham'])
  .then(function(pizza){
    console.log(pizza);
    return makePizza(['ham', 'cheese']);
  })
  .then(function(pizza){
    console.log(pizza);
    return makePizza(['hot peppers','onion', 'feta']);
  })
  .then(function(pizza){
    console.log(pizza);
  })
console.log('Right after');
```

![](@attachment/Clipboard_2020-05-12-06-50-19.png) 12:26

We will look at how we can use async await to get around that. 

If you look at the call stack, what we know is that it first runs function highlighted below, which immediately returns a proimse. 

![](@attachment/Clipboard_2020-05-12-06-50-58.png) 12:34

Then it runs the bottom log, before jumping back up to the first `then` we have when the promise is resolved, and then it keeps going down the promise chain. 

Let's make our `makePizza` function a bit more resilient, starting with `toppings`. Let's set an empty array as the default because sometimes people might order a pizza with nothing on it `function makePizza(toppings = [])`. 


For every single topping that is added to the pizza, let's add 200 miliseconds to the initial bake time which is 500. Let's calculate that and save it in a variable like so `const amountOfTimeToBake = 500 + (toppings.length * 200);`. 

Now we will take that variable and pass it to our timeout. 
```
function makePizza(toppings = []){
  const pizzaPromise = new Promise(function(resolve, reject){
    const amountOfTimeToBake = 500 + (toppings.length * 200);
    //wait 1 second for the pizza to cook
    setTimeout(function(){
      resolve(`Here is your pizza 🍕 with the topppings ${toppings.join(' ')`);
    }, amountOfTimeToBake)
    //if something went wrong, we can reject this promise
  });
  return pizzaPromise;
}
```

![](@attachment/Clipboard_2020-05-13-18-25-48.png) 13:35

When we refresh the page and the above code is executed, what should happen is ham and cheese should be logged to the console faster than the pizza with three toppings. 


Let's chain two more pizzas together, one with no toppings, the other with a lot of toppings. THen let's resolve that last pizza and just log it using an arrow function like so 

```
console.log('First');
makePizza(['pepperoni', 'ham'])
  .then(function(pizza){
    console.log(pizza);
    return makePizza(['ham', 'cheese']);
  })
  .then(function(pizza){
    console.log(pizza);
    return makePizza(['hot peppers','onion', 'feta']);
  })
  .then(function(pizza){
    console.log(pizza);
    return makePizza();
  })
  .then(function (pizza) {
        console.log(pizza);
        return makePizza(['one', 'two', 'three', 'four', 'one', 'two', 'three', 'four', 'one', 'two', 'three', 'four']);
      })
  .then(pizza => {
      console.log('All done! here is your last pizza');
      console.log(pizza);
    })
console.log('Right after');
```

Let's say we have a big oven and we can make all the pizzas at once. You could them all at once concurrently, instead of one after another like we are doing (which is referred to as sequentially). 

If you have 10 employees and an oven big enough to cook the mall at once you can do it like so 👇

```
  // Run them Concurrently
    const pizzaPromise1 = makePizza(['hot peppers', 'onion', 'feta']);
    const pizzaPromise2 = makePizza(['one', 'two', 'three', 'four', 'one', 'two', 'three', 'four', 'one', 'two', 'three', 'four']);
    const pizzaPromise3 = makePizza(['ham', 'cheese']);
```

So how do we know when all of those promises are done? We could do .then() on each of them like so 👇

![](@attachment/Clipboard_2020-05-13-18-36-33.png) 16:36

But those are going to pop into the console in whatever order they are done, which isn't what we want. We can instead make it into a "mega promise" that we then wait upon. 

If you have a few promises and all you care about is when all three of them are finished, you can make a mega promises, which we will call a `dinnerPromise`. 

```
    const dinnerPromise = Promise.all([pizzaPromise1, pizzaPromise2, pizzaPromise3]);
```

`Promise.all()` is a static method because it lives on the momma Promise directly. 

It takes an array of "baby" promises which are `pizza1`, `pizza2`, `pizza3`. 

That makes one big promise which then you can call `.then()` on and we get passed the `pizzas` which we will log. 

```
dinnerPromise.then(pizzas => {
  console.log(pizzas);
})
```

Now we wait for all three to be finished, and we get an array of all three of them. 

![](@attachment/Clipboard_2020-05-13-18-42-40.png) 17:58

If you wanted the first pizza it would be `pizza[0]`. 

A pretty common thing to do is destructure the pizzas. Let's convert the arrow function to a regular function to make it clearer to understand. 

We will use an array destructuring. Let's call the first pizza `hottie`, second one `garbagePail` and third one `hamAndCheese`. Those will now be equal to three variables which we can now log or use however we want like so 👇

```
innerPromise.then(function (pizzas) {
  [hottie, garbagePail, hamAndCheese] = pizzas;
  console.log(hottie, garbagePail, hamAndCheese);
}); 
```
![](@attachment/Clipboard_2020-05-13-18-48-06.png) 18:58

You do not have to destructure those variables in the body of the function, you can destructure the argument directly with square brackets.

```
dinnerPromise.then(function ([hottie, garbagePail, hamAndCheese]) {
  console.log(hottie, garbagePail, hamAndCheese);
});
```

That is saying take the first argument and destructure it into a variable named `hottie` , the second one into `garbagePail` and so on.

If you refresh the page you will see it still works. 

To reiterate, `Promise.all()` will take all of your promises and will only resolve when all three of the sub-promisess have been resolved themselves.

Similarly there is `Promise.race()`. Let's say someone is really hungry and they will take whichever pizza the first pizza is that is ready because they are very hungry. 

We could do this 👇

```
const firstPizzaPromise = Promise.race([pizzaPromise1, pizzaPromise2, pizzaPromise3]);
```

Now we can log it. 

```
firstPizzaPromise.then(pizza => {
  console.log('You must be hungry, here is the first one ready');
  console.log(pizza);
})
```

TO reiterate, `Promise.race()` will wait for the first one to finish rendering. 

![](@attachment/Clipboard_2020-05-13-18-53-52.png) 20:46

There are also a couple of other ones which we will get into when we talk about error handling. 

That is a high level overview of promises. 

---

## 68 - Promises - Error Handling

In this lesson we will talk about the opposite of resolving, which is rejecting. When a promise goes awry, and you want to bail on it, you can call the reject function. 

Let's go back to our `makePizza` definition and inside of our promise we need to check whether one of the toppings chosen for the pizza is pineapple. If it is true, we need to reject the pizza from happening. 

To do that we will add the following code. For now will only check for lowercase "pineapple" but we will have to try to weed out people who uppercase it as well later. If that condition is met, then we will call reject and pass it "seriously? get out". 

```
if(toppings.includes('pineapple')){
  reject("Seriously? Get out 🍍");
}
```

Now let's go to the bottom of the script section and let's commment out the code we added in the previous lesson when we were doing an example on how to run promises concurrently. 

Below that commented out code add the following

```
makePizza(['cheese','pineapple']).then(pizza=>{
  console.log(pizza);
})
```

![](@attachment/Clipboard_2020-05-14-07-53-01.png) 1:55

What does that log that we see mean? It means that there was an error in one of our promises, but we did not write any code in order to handle that error and try to catch it. 

The way you catch an error in a promise is you chain a `.catch()` to it. Catch will pass you the error as a parameter which we will use to log the error like so: 

```
makePizza(['cheese','pineapple']).then(pizza=>{
  console.log(pizza);
}).catch(err=>{
  console.log('Oh noooo!!');
  console.log(err);
})
```

As you see, we no longer get an error logged because we caught and logged the error ourselves.

![](@attachment/Clipboard_2020-05-14-07-55-32.png) 2:24

`.then()` will only run when the promise resolves successfully, and the catch will only run if the promise doesn't go successfully.

Almost always with your promise built functions you must chain a `.then()` and a `.catch()` at the end so that if anything goes wrong, you are able to catch it and display it to the user.

What Wes will usually do is make a function called `handleError` which will take in the error and log it like so:

```
function handleError(err){
  console.log('Oh noooo!');
  console.log(err);
}
```

Now instead of catching the error using the code we had before we can simply replace it with this:

```
makePizza(['cheese','pineapple']).then(pizza=>{
  console.log(pizza);
}).catch(handleError);
```

In the code above we are passing the reference to the function which will then handle the error.

It's important to note that not every single promise needs a catch on the end.  

If we go back to our pizzas where we chained a bunch of promises together and modify the pizza with no toppings to instead pass the topping of "pineapple", 


![](@attachment/Clipboard_2020-05-14-08-07-15.png) 3:59

What happens there is we go through the chain of promises and then as soon as we hit the code where we try to make a pizza with a pineapple we get the uncaught i promise error. 

![](@attachment/Clipboard_2020-05-14-08-08-07.png) 4:06

So how do we catch the error? Does it mean we have to add a `catch` after each `then`? That would be annoying. 

Thankfully, the answer is no. 

You just need to put one catch at the very end that will be able to handle our error. 

![](@attachment/Clipboard_2020-05-14-08-09-12.png) 4:31

The thing about an error happening in a promise chain is that where the error happens, it will then bail out of executing the rest of the promise chain. 

If you have 7 or 8 steps in the promise chain and they are all dependent on one another, then that is good because if step three in the breaks, you don't want to continue to step 4.

But sometimes you want to continue even if one of the promises fails. If that is the case, then promise chaining is not what you want to use. Instead, you'd want to use some of the other Promise static methods like `Promise.all()` or `Promise.race()`.

Let's do an example. We will start with two pizzas. 

```
const p1 = makePizza(['pep']);
const p2 = makePizza(['pineapple']);
```

We will use a new API that we haven't learned yet called `Promise.allSettled()`.

Let's start by making a mega promise.

```
const dinnerPromise2 = Promise.allSettled([p1, p2]);
```

Let's just get the results and log them for now. 

```
dinnerPromise2.then(results=> {
  console.log(results)l
})
```

![](@attachment/Clipboard_2020-05-14-08-13-58.png) 6:17

As you can see in our results we can see that the first one was **fulfilled** and the second one was **rejected**. Fulfilled is another word they use for resolved.

If we tried that example but with `Promise.all()` like so, you will see that the code will break. 

```
const dinnerPromise2 = Promise.all([p1, p2]);
```

![](@attachment/Clipboard_2020-05-14-08-15-32.png) 6:39

That is because `Promise.all` assumes that all of them will go successfully. 

If you want to catch any errors that happen in `Promise.all()` you would have to catch them like so:

```
const dinnerPromise2 = Promise.all([p1, p2]).catch(handleError);
```

![](@attachment/Clipboard_2020-05-14-08-17-26.png) 7:02

That is probably not what you want because if one of them breaks, you might still want the other one, because those other pizzas are still good. 

`Promise.allSettled()` will tell you when all the promises are done, regardless of whether they were rejected or resolved.

There are a few more error handling techniques that we need to use but they do not get introduced until we learn **async await**. 

Let's go back and refactor the last exercise we did to use promises instead of callback hell.

---

## 69 - Refactoring Callback Hell to Promise Land

In this lesson we will go back to the event loop example, where we added the classes of `circle`, `purple` and `fadeout`, and we will refactor it to use promises instead.

![](@attachment/Clipboard_2020-05-16-16-02-08.png) 00:13

We will be coming back to this example one more time and refactor it after we learn `async await`.

Take out `event-loop.html` file, duplicate it and rename it as `promise-chain.html`.

The first thing we want to do is make a function that will simply wait for a certain amount of time. This is something Wes does in almost every single project because it is such a common thing.

Let's make a function called `wait` which will take in the number of miliseconds we want to wait using the parametetr `ms`, which we will default to 0 seconds, and then we will return a new promise which will resolve after the number of miliseconds that got sent in.

Then we will just test our new method by waiting 2 seconds (2000 miliseconds) before logging "DONE".

```
function wait(ms = 0){
  return new Promise(function(resolve){
    setTimeout(resolve, ms);
  });
}

wait(200).then(()=>{
  console.log('Done');
})
```
Now if you refresh the page, after 2 seconds you should see "done" logged to the console.

![](@attachment/Clipboard_2020-05-16-16-13-20.png) 2:03

That is such a common thing that Wes actually has an npm package called `Waait` which gets around 75k downloads per week and all it does is return a promise that resolves after a certain number of miliseconds that have been passed in. 

We can use the implicit return and arrow function to refactor the `wait` function like so to be on one line:  

```
const wait = (ms = 0) => new Promise(resolve =>  setTimeout(resolve, ms));
```

Now that we have this `wait` function, we can start to tackle all the callback hell.

Let's just rewrite it starting at the beginning by taking all our setTimeouts and instead making them promise based.

The first thing we will do is make an external function called `animate` and when someone clicks the go button, we will run `animate`. 

`animate` will take in the event and let's start moving logic up to it. 

For the event listener we already had on `go`, we will replace `click` with `clickXXXXX` so it doen't actually trigger and we can refactor piece by piece.


```
function animate(e){

}
go.addEventListener('click', animate);

go.addEventListener('clickxxxx', function go(e){

})
```

The first thing we want to do is grab the element, then we want to change the text to "GO" when clicked, which is immediately so we can put it right into our animate function. 

```
function animate(e){
  const el = e.currentTarget;
  //1. change the text to GO when clicked
  el.textContent = 'GO';
}
```

Now we want to make it a circle after two seconds so we can use our `wait` function we made. We will chain a `.then()`, although there is no piece of data that is resolved from the wait, it simply is just done. 

```
function animate(e){
  const el = e.currentTarget;
  //1. change the text to GO when clicked
  el.textContent = 'GO';
  wait(200).then(()=>{
     el.classList.add('cirlce');
  })
}
```

Now after 2 miliseconds, the GO square will turn into a circle. If you refresh the page, you will see it still works.

![](@attachment/Clipboard_2020-05-16-16-26-37.png) 6:11

Now how do we make it red after 0.5 seconds? We cannot just call it after the wait function because that will cause it to go red before it goes to circle.

What we can do instead is we can return another wait of 500 miliseconds and then chain anonther  `.then()` onto it and put our third item in their, like so:


```
function animate(e){
  const el = e.currentTarget;
  //1. change the text to GO when clicked
  el.textContent = 'GO';
  //2. make it a circle after 2 seconds
  wait(200).then(()=>{
     el.classList.add('cirlce');
     return wait(500);
  }).then(()=>{
    //3. make it ared after 0.5 seconds
    el.classList.add('red');
  })
}
```

To make this more readable you can format them each on their own line like so:


```
function animate(e){
  const el = e.currentTarget;
  //1. change the text to GO when clicked
  el.textContent = 'GO';
  //2. make it a circle after 2 seconds
  wait(200)
  .then(()=>{
     el.classList.add('cirlce');
     return wait(500);
  })
  .then(()=>{
    //3. make it ared after 0.5 seconds
    el.classList.add('red');
  })
}
```
Now we have to make it a square after 0.25 seconds by removing the class of circle.  

```
.then(()=>{
  //3. make it ared after 0.5 seconds
  el.classList.add('red');
  return wait(250);
})
.then(()=>{
  el.classList.remove('cirlce');
})
```

Now after 500 miliseconds we want to remove the red class and add the purple one like so:


```
.then(()=>{
  //3. make it ared after 0.5 seconds
  el.classList.add('red');
  return wait(250);
})
.then(()=>{
  el.classList.remove('cirlce');
  return wait (500);
})
.then(()=>{
  el.classList.remove('red');
  el.classList.add('purple');
})
```

Now finally, after half a second, we need to make it invisible.

```
.then(()=>{
  el.classList.remove('red');
  el.classList.add('purple');
  return wait(500);
})
.then(()=>{
  el.classList.add('fadeOut');
})
```

So what we have done here is taken the nested callback function and made it one level deep, which is waiting returning, waiting returning. That is chaining multiple `.then()`s onto each other.

That gets much better when we get to `async await` but for now, this is the best way we can refactor these promises into a promise chain. 

 
---

## 70 - Async Await

---

## 71 - Async Await Error Handling

---

## 72 - Async Await Prompt UI

---

## 73 - Async Typer UI - two ways
