---
attachments: [Clipboard_2020-03-15-15-15-20.png, Clipboard_2020-03-15-15-31-07.png, Clipboard_2020-03-15-15-31-09.png, Clipboard_2020-03-15-16-06-43.png, Clipboard_2020-03-15-16-18-16.png, Clipboard_2020-03-15-16-29-54.png, Clipboard_2020-03-15-16-36-41.png, Clipboard_2020-03-15-16-38-41.png, Clipboard_2020-03-15-16-40-43.png, Clipboard_2020-03-15-16-41-17.png, Clipboard_2020-03-15-18-01-03.png, Clipboard_2020-03-15-18-32-04.png, Clipboard_2020-03-17-20-44-18.png, Clipboard_2020-03-23-19-52-26.png, Clipboard_2020-03-23-19-56-52.png, Clipboard_2020-03-23-19-57-48.png, Clipboard_2020-03-23-19-59-27.png, Clipboard_2020-03-23-20-09-14.png, Clipboard_2020-03-23-20-14-43.png, Clipboard_2020-03-23-20-25-53.png, Clipboard_2020-03-23-20-29-52.png, Clipboard_2020-03-23-20-30-24.png]
title: 'Module 6: Serious Practice Excercises'
created: '2020-03-15T19:10:20.059Z'
modified: '2020-03-24T00:30:37.662Z'
---

# Module 6: Serious Practice Excercises

## 33 - Etch-a-Sketch

Now that we have gone over some of the fundamentals of Javascript, it is important for us to practice what we have learned so we can put our skills into use, and have fun along the way. 

In this video we will build an Etch-a-Sketch that you can control by moving the arrow keys around. Wes has added some fun things to it, for example the line is a rainbow gradient and then you can shake it an refresh. Another thing to note is whenever you reload the page, it picks a random spot to begin. 

![](@attachment/Clipboard_2020-03-15-15-15-20.png) 00:39

Topics we will be covering in this video include DOM elements and keyboard events. We will be learning about something called **canvas** in javascript, and we will be touching on **switch** statements which we have not learned yet. 

Inside of the `/excerises` directory there should be a folder called `/33 - Etch-a-sketch` containing two files: `index.html` and `etch-a-sketch.js`. Open up the `index.html` file which Wes provided for us. It should contain the following: a div with the class of canvasWrap, and then a canvas element, which is an HTML element that is used for drawing on. We have explictly given the canvas element a width and a height. 


If you look at the CSS, you will notice that we have halved those width and height values for the canvas. The reason for that is beause you can think of the html width and height values we have set via html attributes as the actual width of an image.. those values represent that actual height and width of the canvas element. 
However, the values we set in CSS are the size that is should be on in the screen. The reason Wes halved the size via CSS is so that it won't look pixelated. On most screens, these things are going to be high resolution and when we are dealing with pixel based stuff, you want to be at least double so get crisp stuff on the page. 

We also have a button with a class of shake which is wrapped within a div because you could add other buttons like up right left down for people who are on mobile and do not have arrow keys. 

We have some animation stuff which we will dive into later. 

```
<body>
  <div class="canvasWrap">
    <canvas width="1600" height="1000" id="etch-a-sketch"></canvas>
    <div class="buttons">
      <button class="shake">Shake!</button>
    </div>

  </div>
  <script src="./etch-a-sketch"></script>
  <style>
      body {
        min-height: 100vh;
        display: grid;
        align-items: center;
        justify-items: center;
        background: white;
        background: url(https://s3.amazonaws.com/media.locally.net/original/HABA_ALT_2017-08-02-13-22-45.jpg);
        background-size: cover;
      }

      canvas {
        border: 30px solid #e80000;
        border-radius: 10px;
        /* Set the width and height to half the actual size so it doesn't look pixelated */
        width: 800px;
        height: 500px;
        background: white;
      }

      canvas.shake {
        animation: shake 0.5s linear 1;
      }

      @keyframes shake {

        10%,
        90% {
          transform: translate3d(-1px, 0, 0);
        }

        20%,
        80% {
          transform: translate3d(2px, 0, 0);
        }

        30%,
        50%,
        70% {
          transform: translate3d(-4px, 0, 0);
        }

        40%,
        60% {
          transform: translate3d(4px, 0, 0);
        }
      }
    </style>
</body>
```

Open up the javascript file `etch-a-sketch.js`, and open up `index.html` in the browser. Add a console.log and make sure the javascript file is properly linked. 

We are going to start by writing pseudo code for what we need to do within the javascript file. 
 
```
// Select the elements on the page - canvas, shake button

// set up our canvas for drawing

// write a draw function 

// write a handler for the keys

//clear or shake function

//listen for arrow keys
```

If you have never seen **canvas** before, the way it works is that you go ahead and grab onto the canvas, then you grab onto this thing called "context" which is either 2D or 3D (we will be working with 2D canvas today), and then you have a set of APIs (methods) that are used for drawing on the canvas. Think of something like Microsoft Paint. Rectangles, circles, drawing, lines, borders, different fill colors, all of those things are available to us in canvas and they are used for when you want to programmatically draw something to the browser. 

If you inspect the canvas element in dev tools, you will see that it's just a regular old canvas element.

![](@attachment/Clipboard_2020-03-15-15-31-09.png) 5:12

First we will grab the canvas:
```
const canvas = document.querySelector('#etch-a-sketch');
```

Next we need to grab the context. The canvas is the element and the place where we do our drawing is called the context, where we will be drawing our cirlces and everything too.  We just need to all `getContext('2d')` on the canvas element to get the 2d context like so

```
const ctx = canvas.getContext('2d');
```
Note: `ctx` is a very common variable name for context. 

If you google `three.js` you can see a lot of examples of things people are doing with 3d canvas. 

Next, we need the shake button. The shake button has a class of shake which we can use to grab it. 

```
const shakebutton = document.querySelector('.shake');
```

Now we have all of the different elements we want. Now we need to setup our canvas for drawing. 

We will just set a couple of defaults on the canvas. 

```
ctx.lineJoin = 'round';
ctx.lineCap = 'round';
```

Those two settings ensure that we get a smooth drawing. By default, you are going to get a squared off edge and that doesn't look as good. You can also set the width of the line to be as wide as you want. By default, it's one pixel. We want it to be thicker so we will set the lineWidth to be 10 (you don't have to specify the pixel value). 

```
ctx.lineWidth = 10;
```

Refresh the HTML page and then open up the console. Type in `ctx` so we can have a look at our ctx. You will see we get this `CanvasRenderingContext2D`.

![](@attachment/Clipboard_2020-03-15-16-06-43.png) 8:03

This is our context object. Inside are all these different properties that you can set or get from them, including what color the fill will be, the stroke will be, etc. 

Next we have to put our drawer somewhere. That means we have to put a dot somewhere, because that is where we need tostart, that is how an etch-a-sketch works. If you load the finished project in an HTML page and refresh the page, each time it loads, you will see that the dot is randomly places. 

Next what we have to do is put a dot somewhere, and then we will work on randomizing it. We will take the ctx and run something called, `beginPath()` which will start the drawing. 

You can think of let's say you have a marker, and you are going to draw on a page, what are you going to do? First you need to put the marker on the page, which is what `beginPath()` does. Then you need to move the context so `ctx.moveTo(200,200);`. That will place the dot 200 pixesl from the left and 200 pixels from the top. Then we will run `ctx.lineTo(200, 200)`, to which we pass the exact same values `200, 200`. Then you run `ctx.stroke();` which will draw a line between where you started and where you drew your line to. That will sort of make an invisible line and that will stroke it.

Now if you fresh the page, you will see a dot 200 pixels over and 200 pixels down. 

![](@attachment/Clipboard_2020-03-15-16-18-16.png) 9:50

 What is cool about an Etch-a-Sketch is that it can start in a random spot. How can we pick a random spot in this Etch-a-Sketch? You could take the width, and the height and then generate a random number between zero and the width and then zero and the height. 

 ```
 const width = canvas.width;
 const height = canvas.height;
 console.log(width, height);
 ``` 

If we console the width and the hieght, what should we get? You will get 600 and 1000 which are the actual height and weight of the canvas, not the display width. 

You might notice that when you save the javascript file, Prettier modifiies the variable declarations for width and height like so: 

![](@attachment/Clipboard_2020-03-15-16-29-54.png) 10:38

Prttier is doing **destructing** for us. 
If you are simply making variables from a property on an object, you can shortform this. 

Instead of:

```
const width = canvas.width;
const height = canvas.height;
```

You can do:
```
const { width, height } = canvas;
```

That is called destructuring. Meaning that we are going to take the width property and put it into a variable called width. We are going to take the height property and put it into a variable called height. That is a nice short way to do that. 

We will do a lot more destructuring in this course, this is just our first time encountering it. 

Why are we grabbing the width and height variables? Wes likes to have top level variables. He finds it easier to use when doing math. It's much easier than writing canvas.width everytime. 

Now we want to creta a random x and y starting points on the canvas. So how do you create random values in Javascript? You may have seen that we have **Math.random()**. If you type that into the console, you will see that it gives us a random number that seems to always be underneath one. 

![](@attachment/Clipboard_2020-03-15-16-36-41.png) 12:54

Can we just pass a random number? Could we do something like `Math.random(100)`? No, that doesn't do anything. Let's look at the docs!

![](@attachment/Clipboard_2020-03-15-16-38-41.png) 13:19

Math.random returns a floating-point (that means it contains decimals), pseudo-random number in the range of 0 to 1, inclusive of 0 but not 1. That means there is a possibility that you will get zero, but you will never get one. It doesn't take any arguments or anything like that.

What you can do is take the `Math.random` value that it give syou and multiply it by 100, we are going to get a random number between zero and 99.99999. 

![](@attachment/Clipboard_2020-03-15-16-40-43.png) 14:09

Then what we can do is run `Math.floor(Math.random() * 100))`, which should give us a number between 0 and 99. 

![](@attachment/Clipboard_2020-03-15-16-41-17.png) 14:24

So that is exactly what we are going to use. We will do:

```
const { width, height } = canvas;

let x = Math.floor(Math.random() * width);
```

Replace the hard coded x value was passed to `ctx.moveTo` and `ctx.lineTo` with the variable x. 

```
ctx.beginPath();
ctx.moveTo(x, 200);
ctx.lineTo(x, 200);
ctx.stroke();
```

Now when you refresh the page, you should see that we are randomly getting an x value.

Now we will do the same for the y value.

```
let y = Math.floor(Math.random() * height);
...
ctx.moveTo(x,y);
ctx.lineTo(x,y);
```

We might need to come back and modify that so it move a little bit quicker but we can leave it there for now.

For now, whenever you refresh the page you get a random x and y value that moves the dot around the page. 

If you change `ctx.lineCap="round";` to `ctx.lineCap = "square";` it looks like this:

![](@attachment/Clipboard_2020-03-15-18-01-03.png) 16:23

But switch it back to round because we want to use round.

Now that we have the basis of our canvas working, let's write the handler for working with the arrow keys. We need to know whether to move the line up or down or left or right. 

We will make a function called `handleKey`. 

We can listen for the arrow keys using a keydown event listener. You can listen for a keydown event on anything, we already did it on text inputs, but if you want to listen to it site wide, you listen to it on the window. 

We listen for a keydown event and when that happens we want to run the `handleKey` function.

```
function handleKey(){
  console.log("HANDLING KEY");
}
window.addEventListener('keydown', handleKey);
```

Refresh the `index.html` page and open the console. Click on the html page and try pressing the arrow keys (up, down, left, right) and you should see the console logging "HANDLING KEY" every time you press a key.

You might notice that when you hit the arrow keys, the page is also scrolling. That is because it's a default. You probably don't want to turn off the scroll default unless you were accounting for the page being loaded on a very small window but if you did want to, you could just pass the event to the `handleKey` function like so `handleKey(e)` and call `e.preventDefault();` on it.

If you refresh the html page, and then hit COMMAND + R on your keyboard, that should refresh the page. However, when you try it, you will notice that it does not refresh the page. That is because we called `preventDefault()` on every keydown event. So let's actually comment out the `e.preventDefault()` line of code within the `handleKey()` function and then manually refresh the HTML page. 

```
function handleKey(e) {
  // e.preventDefault();
  console.log(e.key);
  console.log("HANDLING KEY");
}

```

Now, if you were to press any key, you would see it logged in the console. We only really care about the arrow keys so what we can is check whether the key value has the word arrow in it. 

![](@attachment/Clipboard_2020-03-15-18-32-04.png) 19:39

We will add an if statement, which we haven't learned about before, but if conditions check if something is true (whether it evalutes to boolean true or false), and then runs a block of code based on that condition. 

Here we will check whether the key includes the word arrow, and if it does, we will move the logic to log to the console within the if block as well as the `preventDefault()` call, like so:

```  
if (e.key.includes("Arrow")) {
       e.preventDefault();
    console.log(e.key);
    console.log("HANDLING KEY");
}
```

Now, if you refresh the html page, if you use any of the arrow keys, you will see it logged in the console, but if you press any other key, it won't. Now you should be able to press command + R to refresh your html page using the keyboard shortcut. 

That was just the handler, and what we are going to do is hand off the key to the draw function.

Let's create a function called `draw` that takes in an argument. 

Instead of just having a key passed as the first argument, we are instead going to take in an options object. That options object will contain everything that we wish to pass to the draw function. 

This is useful when you have a function that needs a lot of things passed to it. It's too long to pass in that many variables such as `function(one, two, three, four five)` for example, you need to pass them in the specific order and if some of them are optional, it gets even trickier. 

So instead of passing each argument, we will pass in the option object which will contain different properties that contain the data we need. 

```
function draw(options){
  console.log(options.key);
}
```

Although we haven't learned objects yet, in the handler, we will be passing in an object that has a key property whose value is `e.key` like so:

```
functionHandleKey(e){
  if(e.key.includes('Arrow')){
    e.preventDefault();
    draw({key:e.key});
    console.log(e.key);
    console.log('HANDLING KEY');
  }
}
```

Now, within the draw function, let's console log the options argument.

At this point we have: our event listener, which listens for keydown and runs handleKey, which checks if the key is an arrow and if it is, passes that along to the draw function.

Now our draw function has an object and inside of that there is one property called key which tell us the key is arrow up. 

Another thing Wes likes to use, similar to how we used destructing in an earlier example, is using destructuring in function declarations. 

So instead of doing the following:

```
function draw(options){
  console.log(options.key);
}
```

We could destructure the options object directly into a key variable like so:

```
function draw({key}){
  console.log(key);
}
```

This gives us a top level variable called key that we can use directly.

So this curly bracket here:

![](@attachment/Clipboard_2020-03-17-20-44-18.png) 22:57 

is called object destructuring, where we can take properties and rename them into proper variables and it allows us to have shorter variable names.

Get rid of the console logs that we have within our handlers. That should leave one console log of the key within the draw function. Now if you refresh the html page and press the arrow keys, you will see they are being logged.

Now, when someone goes ahead and uses their keys, we can start to draw directly onto the canvas.

Just like we have created our `ctx.beginPath` earlier in the javascript file, we can call beginPath on the context within the draw function. 

```
function draw({ key }) {
  console.log(key);
  //start the path
  ctx.beginPath();
}
```

Similarly like we called `ctx.moveTo(x,y)` earlier, we need to call `moveTo()`. We want to move the context to where it was so add the following: `ctx.moveTo(x,y);`. Now we need to move our x and y depending on what the user did. 

Let's add the following:

```
 // move our x and y values depending on what the user did
  x = x - 10;
  y = y - 10;
  ctx.lineto(x,y);
  ctx.stroke();
```

So what we did there was change the x and y values and then we created a line to our new x and y values, and then called `.stroke()`. 
You may notice that Prettier/ESLint is complaining that x and y are const values, which cannot be updated. Previously, ESLint or Prettier noticed that our x and y values which we had saved as let variables were never updated, so ESLint updated them to const. However, now that we want to change those values, we need to switch them back to lets. 

You also may notice that when you save your javascript file, it reformats from `x = x - 10;` to `x -= 10;` which is a shortform way to say the same thing. 

Now if you refresh the page and press an arrow key, you will see an error in the console that says something like this: 

>Uncaught TypeError: ctx.lineto is not a function
>   at draw (etch-a-sketch.js:31)
>    at handleKey (etch-a-sketch.js:42)

That is because it should be `ctx.lineTo(x,y)`. Make that change in your code.

Now if you refresh the page and hit an arrow key, you should see a line being drawn on the etch-a-sketch! What is happening there is anytime an arrow key is pressed we are removing 10 pixels from the x and 10 from the y, and then we paint. That's obviously not wht we want but this is just to demonstrate that it is responding to our key pressed. 

One thing Wes doesn't like doing is hardcoding the values like `x = x - 10;`. SO instead, what we will do is we will setup a variable amount and we will set that at the top of the file and reference it to change the value whenever we want. Add the following towards the top of the file:

```
const MOVE_AMOUNT = 10;
```

You may be wondering why did Wes use all capitals for that variable name? It's not a "best practice" but it is something that some developers do and Wes has picked it up himself. When it is a true constant, meaning that value will never change, we tend to make it uppercase and use underscores. 

Now, we will go through our `etch-a-sketch.js` file and everywhere that we have used `10`, we will replace with MOVE_AMOUNT. Now we have used one variable to reference the width everywhere we go. 

Now we don't want to just go up and to the left whenever someone presses an arrow key. We need to go back into our draw function and write a bit more code that depending on which arrow key the person has done, we can do it.

We haven't really learned about flow control yet (if statements and such), but this is a perfect case to learn for something called a switch statement. Wes doesn't use switch statements all that often, but it is perfect use case.

A switch statement is essentially saying, take in a variable like the key, and depending on all of the different cases (it might go up, down, left or right). SO we have four possible cases in this example. Each of those cases has a different outcome. A switch statement allows us to say "based on these four different outcomes, do the following". 

Within the `draw` function remove these two lines of code: 

```
x -= MOVE_AMOUNT;
y -= MOVE_AMOUNT;
```

We will instead run a switch statement. We pass the switch statement the variable we want to run it against (the key in this case), and then the cases are the possible values that key might be. 

Note: a switch statement could also be written as an if statment such as 

```
if(key == 'ArrowUp'){

}
else if(key == 'OtherValue'){
  
}
```

However a switch statement is a lot more readable. We are going to add a case for `'ArrowUp'`. If key equals ArrowUp, we will move the y 10 pixels like so ` y = y - MOVE_AMOUNT;`. 

```
switch(key){
 case 'ArrowUp':
  y = y - MOVE_AMOUNT;
   
}
```

You might notice if you save the code, vs code will throw an error complaining that the switch statement expects a default case. A switch statement should always have a default case which specifies the behaviour to execute if none of the other cases match (if key does not equal ArrowUp, ArrowDown, ArrowLeft or ArrowRight in our example). Hopefully that should never happen but it's always best practice to give your cases a default. 

Our default will be followed with the keyword `break`. Add the following:

```
  switch (key) {
    case "ArrowUp":
      y -= MOVE_AMOUNT;
    default:
      break;
  }
```

Actually in a switch statement after every single case, you have to write the `break` keyword which will actually stop the switch from running, and skip over the rest of it. Here is what we have so far:

```
  switch (key) {
    case "ArrowUp":
      y -= MOVE_AMOUNT;
      break;
    default:
      break;
  }
```

We have only implemented the case for ArrowUp. If you refresh the page and hit the arrow up key, you should see a line being drawn! 

![](@attachment/Clipboard_2020-03-23-19-52-26.png) 31:06

Now, let's add the rest. Duplicate that case three more times. 

For `ArrowRight`, we will increment the x value. For `ArrowDown` the y value will be incremented. For ArrowLeft, the x value will be decremented.

```
  switch (key) {
    case "ArrowUp":
      y -= MOVE_AMOUNT;
      break;
    case "ArrowRight":
      x += MOVE_AMOUNT;
      break;
    case "ArrowDown":
      y += MOVE_AMOUNT;
      break;
    case "ArrowLeft":
      x -= MOVE_AMOUNT;
      break;
    default:
      break;
  }
```

Note: if you get an error about the x being a const, that is likely the result of prettier changing it if it doesn't see it being updated anywhere in your code. You need to change it back to a let variable. 

Now refresh the page and let's try it!

![](@attachment/Clipboard_2020-03-23-19-56-52.png) 32:02

Now what we want to do is modify the code so the colour of the line changes as we go along.

![](@attachment/Clipboard_2020-03-23-19-57-48.png) 32:30

That is actually very simple to do, we just have to change the HSL values. If you have never seen Mothereffing HSL, I would recommend going to https://mothereffinghsl.com. **HSL** is a way to declare color in a browser. It is similar to Hex Codes and RGB, but HSL is a cool way to do it. If you just hover over the gradient, you will see the H value goes from zero to 359-360. Once you pas that, it will just go from the start and give you a rainbow. We can use that value, everytime we move the cursor, we will increment the H value (hue) by 1. 

![](@attachment/Clipboard_2020-03-23-19-59-27.png) 33:00

Above our `draw()` function, we will make a new value called hue and set it to 0. Next we will update the stroke color to start at a bright green like so:

```
const hue = 0;
ctx.strokeStyle = `hsl(100, 100%, 50%)`;
```

Now instead of hardcoding the first argument to hsl, we will interpolate it to pass in the `hue` variable like so: 

```
ctx.strokeStyle = `hsl(${hue}, 100%, 50%)`;
```

Now the line will always be red, but what we will do is everytime that we use the draw function, let's increment hue by one and update the stroke style. Add the following code:

```
// write a draw function
function draw({ key }) {
  // increment the hue
  hue += 1;
  ctx.strokeStyle = `hsl(${hue}, 100%, 50%)`;
```

We do need to call `strokeStyle` again, even though we set it on pageload to be a variable, that is done once the page loads, it's not like a live variable that will update itself. We have to explicitly update the strokeStyle by 1. 

If you try it now, you will see that it works. If you want to change  the colors more quickly, you can instead add + 10 when incrementing the hue. 

You can also try to play around with it and do something like this:

```
ctx.strokeStyle = `hsl(${Math.random()*360}, 100% , 50%);
```

That will give you cool effects like these: 

![](@attachment/Clipboard_2020-03-23-20-09-14.png) 36:22

You can have a lot of fun with HSL. 

Now we need to work on the shake / clear canvas function! The idea for this effect is to be similar to what you do to clear a real etch-a-sketch, you shake it! We will have a shake button that is responsible for triggering this. 

Add the following code:

```

// clear or shake function
function clearCanvas()){
  canvas.classList.add('shake');
}
```

Now, when you refresh the html page and run `clearCanvas()` in the console, you should notice the etch-a-sketch doing a little shake animation. That is because the class of shake is applied to it. Because it has a class of shake has been added to it, and Wes has written some CSS to create that effect in this code:

![](@attachment/Clipboard_2020-03-23-20-14-43.png) 38:01

```
canvas.shake{
  animation: shake 0.5s linear 1;
}
```

What we are saying there is when the canvas has a class of shake, run the shake over 0.5 seconds, run it linearly and only run it once. You could run the animation 10 times if you wanted by pass in the 10 instead of 1. 

We have a couple of problems here. If you were to run `clearCanvas()` again in the console, you will notice nothing happens because the canvas already has a class of shake. However if you were to manually remove that class of shake and then call `clearCanvas()`, it would work. 


You might be thinking what the solution is.. do we wait .5 seconds and then remove the shake class? However, trying to lineup timers that are set in your CSS with your Javascript, it is okay but tends to get you in a world of hurt. What we can do is listen for the animation to finish and then programatically remove the class from it.

Just like we can listen to a click, we can listen to this event called `animationend`. 

Within the `clearCanvas()` function, we will add an eventlistener that listens for the animationend event and when that event happens, we will run a function that will remove the class of shake for the canvas. 

```
// clear or shake function
function clearCanvas() {
  canvas.classList.add("shake");
  canvas.addEventListener("animationend", function() {
    console.log("done the shake!");
    canvas.classList.remove("shake");
  });
}
```

Now if you refresh the page and run `clearCanvas()`, you should see the console log and the canvas should shake again. However if you run it again and again from the console, you will notice that "done the shake" is being called many times:

![](@attachment/Clipboard_2020-03-23-20-25-53.png) 41:02

You may be wondering what is going on. This is a common problem, what we are doing is when we run `clearCanvas()`, we add the class, listen for that animation to be over, and then we remove it. 

But what is happening is the canvas still has the event listener of `animationend` added to it. Everytime we clear the canvas, we are adding a new eventlistener to it over and over again. So the number of times you run `clearCanvas()` in the console was the number of eventlisteners that were being added for the same thing. 

If you click on the canvas element in the devtools and then select the "Event Listeners" tab: 

![](@attachment/Clipboard_2020-03-23-20-29-52.png) 41:38

You will see that we are listening for the animationend event every time we run it: 
![](@attachment/Clipboard_2020-03-23-20-30-24.png) 41:44

 stopped at 41:52



