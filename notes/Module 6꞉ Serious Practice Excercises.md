---
attachments: [Clipboard_2020-03-15-15-15-20.png, Clipboard_2020-03-15-15-31-07.png, Clipboard_2020-03-15-15-31-09.png, Clipboard_2020-03-15-16-06-43.png, Clipboard_2020-03-15-16-18-16.png, Clipboard_2020-03-15-16-29-54.png, Clipboard_2020-03-15-16-36-41.png, Clipboard_2020-03-15-16-38-41.png, Clipboard_2020-03-15-16-40-43.png, Clipboard_2020-03-15-16-41-17.png, Clipboard_2020-03-15-18-01-03.png, Clipboard_2020-03-15-18-32-04.png, Clipboard_2020-03-17-20-44-18.png, Clipboard_2020-03-23-19-52-26.png, Clipboard_2020-03-23-19-56-52.png, Clipboard_2020-03-23-19-57-48.png, Clipboard_2020-03-23-19-59-27.png, Clipboard_2020-03-23-20-09-14.png, Clipboard_2020-03-23-20-14-43.png, Clipboard_2020-03-23-20-25-53.png, Clipboard_2020-03-23-20-29-52.png, Clipboard_2020-03-23-20-30-24.png, Clipboard_2020-03-28-15-59-03.png, Clipboard_2020-03-28-15-59-08.png, Clipboard_2020-03-28-15-59-32.png, Clipboard_2020-06-02-07-43-39.png, Clipboard_2020-06-02-07-46-00.png, Clipboard_2020-06-02-07-50-17.png, Clipboard_2020-06-02-07-51-33.png, Clipboard_2020-06-02-07-56-33.png, Clipboard_2020-06-02-07-58-13.png, Clipboard_2020-06-02-17-32-22.png, Clipboard_2020-06-02-17-38-34.png, Clipboard_2020-06-02-17-48-28.png, Clipboard_2020-06-02-17-49-50.png, Clipboard_2020-06-02-17-51-11.png, Clipboard_2020-06-02-17-53-23.png, Clipboard_2020-06-02-17-55-12.png, Clipboard_2020-06-02-17-55-40.png, Clipboard_2020-06-02-18-13-04.png, Clipboard_2020-06-02-18-13-23.png]
favorited: true
title: 'Module 6: Serious Practice Excercises'
created: '2020-03-15T19:10:20.059Z'
modified: '2020-06-03T01:01:58.261Z'
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

That is obviously not what we want. Wes mentioned earlier that there is another argument to `addEventListener`. The first two arguments specify what event the listener should listen on, and what to do when the event occurs. There is a third arguments object for addEventLIstener, and we have only so far used the capture option. 

Now we are going to use the option `once`, which we will set to true. If you set once to be true, what happens is addEventListener will unbind itself. It will call `removeEventLIstener` for you, without having to write any code.

```
// clear or shake function
function clearCanvas() {
  canvas.classList.add("shake");
  canvas.addEventListener(
    "animationend",
    function() {
      console.log("done the shake!");
      canvas.classList.remove("shake");
    },
    {
      once: true
    }
  );
}
```

If we didn't have that option, we would have to call canvas.removeEventListener('animationend' and reference the function within which we are calling removeEventListener, which is a bit of a pain. Thankfully we don't have to do that and can use the options argument to set once to true, which will automatically remove the event listener when the animation is done. 

Now if you refresh the page and call `clearCanvas()` from the console, you will notice that we don't keep attaching event listeners. Instead the event listner is being added and removed, added and removed as we need to. 

Next we need to hook up the `clearCanvas()` function to our shake button click. We will add an event listener on the button for a click event. 

Add the following code:

```
shakebutton.addEventListener("click", clearCanvas);
```

If you refresh the page and use the arrows to draw something on the etch-a-sketch and click shake, you might notice the animation happens bu the content is not removed from the etch-a-sketch. That is because we forgot to do an entire part, which is clearing the canvas (which is actually very simple).

Let's modify the `clearCanvas()` function to add some more code. Right after we add the shake class, and before we add the animationend eventlistener, we will call `clearRect` on the canvas context. What that does is clear part of or all of the canvas. We tell it to start at 0,0 which is the top left hand corner of the canvas and go for 500 & 500 pixels. Add the following code:

```
  ctx.clearRect(0, 0, 500, 500);
```  

Now refresh the page and draw across the canvas.

![](@attachment/Clipboard_2020-03-28-15-59-08.png)

Now click the Shake! button. 

![](@attachment/Clipboard_2020-03-28-15-59-32.png) 44:3`

You should notice only a rectange that is 500 by 500 pixels from the top left corner is cleared. 

Instead of hardcoding the 500x500 pixel value, we will replace those with the variables that we created at the very top of the file, `width` and `height`. 

```
  ctx.clearRect(0, 0, width, height);
```

Now if you refresh, it should all be cleared. 

That is all! That is our first exercise. We went a little over the stuff we have learned, and that is Wes' intention for these exercise videos. He is going to push us in these exercises by introducing some new concepts, desctructuring, canvas, right in the excercise. This is so you can get an idea of how it works when you are in the headspace of building real world things. 

  
---

## 34 - Click Outside Modal

In this lesson we are going to learn how to check whether you clicked outside an element, which kind of tough. 

Let's look at the HTML we will be working with.  

![](@attachment/Clipboard_2020-06-02-07-43-39.png) 00:17
```
<body>
  <div class="cards">
    <div class="card" data-description="Wes is cool">
      <img src="https://picsum.photos/200?random=1" alt="Wes Bos">
      <h2>Wes Bos</h2>
      <button>Learn more →</button>
    </div>
    <div class="card" data-description="Scott is neat!">
      <img src="https://picsum.photos/200?random=2" alt="Wes Bos">
      <h2>Scott Tolinski</h2>
      <button>Learn more →</button>
    </div>
    <div class="card" data-description="Kait is beautiful!">
      <img src="https://picsum.photos/200?random=3" alt="Wes Bos">
      <h2>Kait Bos</h2>
      <button>Learn more →</button>
    </div>
    <div class="card" data-description="Snickers is a dog!">
      <img src="https://picsum.photos/200?random=4" alt="Wes Bos">
      <h2>Snickers the dog</h2>
      <button>Learn more →</button>
    </div>

  </div>

  <div class="modal-outer">
    <div class="modal-inner">
    </div>
  </div>

  <script src="./click-outside.js"></script>
</body>

```

As you can see, each card has a random image, an h2 and a button that says "learn more". 

Let's add the following CSS: 

```
 <style>
    .cards {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      grid-gap: 20px;
      padding: 2rem;
    }

    .card {
      background: white;
      padding: 1rem;
      border-radius: 2px;
    }

    .card img {
      width: 100%;
    }

    .card h2 {
      color: black;
    }
  </style>
```

![](@attachment/Clipboard_2020-06-02-07-46-00.png) 2:55

That is now looking good. Let's move onto the modal. Let's add some dummy content inside of it so when we style it we can visual what it will look like. 

```
<div class="modal-outer">
    <div class="modal-inner">
      <p>TEsting 123</p>
    </div>
  </div>
```

As you can see we have an modal inner and a modal outer. Let's go ahead and style the modal in the on position and then we will turn it off with CSS.

```
   .modal-outer {
      display: grid;
      background: hsla(50, 100%, 50%, 0.7);
      position: fixed;
      height: 100vh;
      width: 100vw;
      top: 0;
      left: 0;
      justify-content: center;
      align-items: center;
   }

    .modal-inner {
      max-width: 600px;
      min-width: 400px;
      padding: 2rem;
      border-radius: 5px;
      min-height: 200px;
      background: white;
    }
```

![](@attachment/Clipboard_2020-06-02-07-51-33.png) 5:50

Now we have this modal which will pop up and you want to be able to close it. Let's just do a really quick example to demonstrate how ti works. 

We need to hide the modal by default. There are LOTS of different ways you could do that, such as display: none, visibility hidden, or something that Wes likes to do is give it an opacity of 0, which won't cut it in our case. That is because even if you did give the modal an opacity of 0, you will see that the modal will prevent the other elements from being clicked like that buttons. That is because the modal outer is actually still there, even if you give it an opacity of zero. 

What you can do is give the modal outer a pointer-events of none like so:

```
 .modal-outer {
      display: grid;
      background: hsla(50, 100%, 50%, 0.7);
      position: fixed;
      height: 100vh;
      width: 100vw;
      top: 0;
      left: 0;
      justify-content: center;
      align-items: center;
      /*hide this modal until we need it*/
      opacity: 0;
      pointer-events: none;  
   }
```

That tells the browser to just ignore that any events that come to that and to not capture them. That is an example of where Javascript and CSS work together. 

Now if you refresh the page and give the modal outer an opacity of .5 in the dev tools, you will see that the modal outer is still there but you will see how the buttons underneath can still be clicked and the events aren't being captured by modal outer.

![](@attachment/Clipboard_2020-06-02-07-56-33.png) 7:28

Now what we will do is when the modal has a class of open, we will set the opacity to 1, and the pointer events to all.

```
.modal-outer.open{
  opacity: 1;
  pointer-events: all;
}

```

Now if you go into the dev tools and give `modal-outer` a class of open, it will show up. 

![](@attachment/Clipboard_2020-06-02-07-58-13.png) 8:02

Let's add a transition to make that look a bit smoother. 

```
/*hide this modal until we need it*/
opacity: 0;
pointer-events: none;  
transition:opacity:0.2s
```

Now if we refresh the page, grab the modal outer in the dev tools and give it a class of open, it will fade itself in, and then fade itself out. 

Now let's get into the Javascript.

We will work on clicking the button on each card now, starting by selecting them. Then we will loop over each of the buttons and add an on click event listener to each one and pass a function as the handler called `handleCardButtonClick`. 

```
const cardButton = document.querySelectorAll('.card button');
cardButtons.forEach(button => button.addEventListener('click', handleCardButtonClick))
```

Now above that code lets go ahead and create that function. For now we will just log "YA CLICKED IT" when the button is clicked. 


```
function handleCardButtonClick(){
  console.log('YA CLICKED IT');
}

const cardButton = document.querySelectorAll('.card button');
cardButtons.forEach(button => button.addEventListener('click', handleCardButtonClick))
```

Now if you refresh the page and try to click on the buttons, you will see the log in the console.

Next we need to grab something to show in the modal. Let's grab the data-description of the parent card and show a larger version of the image. 

To do that, let's grab the current target from the event and assign it to the variable `const button = event.currentTarget`. 

Now we need to find the card that is associated with the button. We could say `button.parentElement`, but if the button were to ever more or be nested inside of something, that wouldn't work that well.

What we can do is take the button and run the `.closest` method and search. It works kind of like `querySelectorAll` for the closest card. 

```
function handleCardButtonClick(event){
  const button = event.currentTarget;
  const card = button.closest('.card');
  console.log(card);
}
```

Now when you click each card's button, you will see the card logged to the console.

What is great abou using `closest` like we did is you can take any element, such as one of the h2s on the card and we can search for the closest div, the closest <html> element, and if there is something that does not match (like `$0.closest('.doesnotmatch')`) it will return null because there is no parent of it. 

![](@attachment/Clipboard_2020-06-02-17-32-22.png) 11:13

So `.closest()` is like `querySelectorAll`, except it is the opposite where it will climb up the nested tree of DOM elements instead of look down the DOM tree.

We are going to use it once more within this handler. What we can do is grab the image source. 

```
function handleCardButtonClick(){
 const button = event.currentTarget;
  const card = button.closest('.card');
  //grab the image src
  const imgSrc = card.querySelector('img').src;
  console.log(imgSrc);
}

```

If you refresh the page and click on the buttons, you should see the image source logged to the console.

Now let's grab the description from the data attribute on the card, like so:  `const desc = card.dataset.description`. Add a console log as well to make sure it is working. 

Now when we refresh the page, and click the buttons, we should see the descriptions logged to the console.

![](@attachment/Clipboard_2020-06-02-17-38-34.png) 12:20

Next we can populate the modal with the card's info. 

We will grab the modal above the `handleCardButtonClick` method because we do not need to reselct it every click.

```
const cardButtons = document.querySelectorAll('.card button');
const modalInner = document.querySelector('.modal-inner');

function handleCardButtonClick(event) {
  const button = event.currentTarget;
  const card = button.closest('.card');
  // Grab the image src
  const imgSrc = card.querySelector('img').src;
  const desc = card.dataset.description;
 }
```

Let's also select the name: `const name = card.querySelector('h2').textContent;`


Within our handler, let's set the innerHTML of the modal using backticks. We want to replace the 200 value in the image sources with 600. We will use the name as the alt attribute value. 

```
modalInner.innerHTML = `
    <img  src="${imgSrc.replace('200','600')}" alt="${name}"/>
    <p>${desc}</p>
  `;
```

Next we want to show the modal. To do that we need to select the outer modal, whcich we will do right above or below where we selected te modalInner. 

```
const cardButtons = document.querySelectorAll('.card button');
const modalOuter = document.querySelector('.modal-outer');
const modalInner = document.querySelector('.modal-inner');
```

Now at the bottom of the handler function, add `modalOuter.classList.add('open');` to show the modal. 


```
function handleCardButtonClick(event) {
  const button = event.currentTarget;
  const card = button.closest('.card');
  // Grab the image src
  const imgSrc = card.querySelector('img').src;
  const desc = card.dataset.description;
  const name = card.querySelector('h2').textContent;
  // populate the modal with the new info
  modalInner.innerHTML = `
    <img  src="${imgSrc.replace('200','600')}" alt="${name}"/>
    <p>${desc}</p>
  `;
  // show the modal
  modalOuter.classList.add('open');
}
```

If you refresh the page, you will see that it works. 

![](@attachment/Clipboard_2020-06-02-17-48-28.png) 14:32 

The image is also there, it is just spilling out so let's fix the CSS. Add the following to the style tag

```
.modal-outer img {
  width: 100%;
}
```

![](@attachment/Clipboard_2020-06-02-17-49-50.png) 15:54

Good, now we have the bare bones of a modal. The other thing we need to talk about is closing it. 

Obviously we could have a function called closeModal which would take the `modalOuter` an remove `open` from the classList, like so: 
```
function closeModal(){
  modalOuter.classList.remove('open');
}
```


But how do we code it so that the modal closes when you click outside of it, and not on the text or the image or anything like that. 

![](@attachment/Clipboard_2020-06-02-17-51-11.png) 16:33

We can solve this using a technique called **click outside**. 

What we will do is take the `modalOuter` and listen for a click on it. When that happens, we will take a look at the event. 

```
modalOuter.addEventListener('click', function(event){
  console.log(event);
})
```

Now when you click outside the modal on `modalOuter`, you will see the click event logged. 

![](@attachment/Clipboard_2020-06-02-17-53-23.png) 17:13

Let's now log the `target` and `currentTarget` of the event.

```
modalOuter.addEventListener('click', function(event){
  console.log(event.target);
  console.log(event.currentTarget);
})
```

![](@attachment/Clipboard_2020-06-02-17-55-40.png) 17:23

You might think this would be simple to solve because you can just check if the modalOuter and the currentTarget are the same thing, then we can go ahead and close it. 
But in the real world, modals are usually more complex than that. Sometimes they have elements on the outside, sometimes you want to listen for clicks on specific things. 

What we can do is use the `closest()` method to see if we are clicking inside of `modalInner` at all.

Let's make a variable called `isOutside` as assign it to the value of `e.target.closest('.modal-inner')`. Let's log the value of `isOutside`. 

```
modalOuter.addEventListener('click', function(event){
  const isOutside = event.target.closest('.modal-inner');
  console.log(isOutside);
})
```

How that works is if you click on the modal or anywhere inside of it, it will find `modalInner`. However, if you click on something that is outside of the inner or a close button or something, it won't be able to find anything. 

[](@attachment/click-outside.gif) 18:57

So what we can do is convert the `closest()` to a boolean true or false by putting a bang in front of it like so: `const isOutside = !event.target.closest('.modal-inner');`. If it finds something it will be false, and if it doesn't finds something it will be true. 

That gives us a nice boolean we can use like so: 

```
modalOuter.addEventListener('click', function(event){
  const isOutside = event.target.closest('.modal-inner');
  if(isOutside){
    closeModal();
  }
})
```

If you refresh the page now, it should work. 

Let's hook up the escape key really quickly. 

```
window.addEventListener('keydown', event => {
  console.log(event);
  if (event.key === 'Escape') {
    closeModal();
  }
});
```

That is it for the lesson, now Wes will just demo some cool stuff.

Add the following style to `modal-inner`: 

```
.modal-inner {
  max-width: 600px;
  min-width: 400px;
  padding: 2rem;
  border-radius: 5px;
  min-height: 200px;
  background: white;
  transform: translateY(-200%);
  transition: transform 2s;
}
```

Now the modal is way off the screen, above the browser. The transition will animate the transform over two seconds. 

Then we can say when the `modalOuter` has a class of open, we want to grab `modalInner` and change the transform to be 0 so it goes back to where it should be. 

```
.modal-outer.open .modal-inner {
  transform: translateY(0);
} 
```

Now if you refresh the page and try clicking on the buttons, you will see how it animates in now. However, you may notice that the transition is a bit jerky and not completely smooth. 

![](@attachment/bad-transition.gif) 22:17

What is happening there is the image isn't loading immediately. There are a couple of things we can do to fix that.

In our `handleCardButtonClick` function, let's set the width and height inline attribute on the image we set within the `modalInner.innerHTML` like so: 

```
modalInner.innerHTML = `
  <img width="600" height="600" src="${imgSrc.replace(
    '200',
    '600'
  )}" alt="${name}"/>
  <p>${desc}</p>
`;
```

If you refresh the page, you should notice it's much smoother because the image is loading as it animates in. 

What about if we had a slower network, would it still look smooth? 

We can test this by going into the dev tools. Go to the network tab and click the dropdown arrow next to "Online"  

![](@attachment/Clipboard_2020-06-02-18-13-04.png) 22:55

![](@attachment/Clipboard_2020-06-02-18-13-23.png) 22:56

We will select Fast 3G.

That option looks good but it is not perfect. 

The other option would be to use `document.createElement` to create an image and wait for that image to load. 

You would listen for the load event on the image and then run the `modalOuter.classList.add('open')` line of code. 
When someone clicks it you could show a spinner for a second as you wait for the image to load and then when it's loaded you can put it in. 

Personally Wes doesn't like that option because he doesn't think it is a smooth user experience. The user is just sitting there waiting for the image to load when they could be reading the text.

---

## 35 - Scroll Events and Intersection Observer

In this video we will learn about scroll events.

A scroll event is when someone goes ahead and scrolls on the page or the inside of an element. 

One thing you are likely to encounter in your career as a developer is building a terms and conditions scroll to accept.

That is where the user is forced to scroll all the way to the bottom of the text before the accept button will work.

![](@attachment/scroll-terms.gif)

First we are just going to dive into scroll events, and then Wes will show us why a scroll event is maybe not what you want, and there is this newer thing in the browser called **intersection observer** which actually might be what we want.   

Let's go into the `exercises` directory and find the `35 - Scroll To Accept` folder and let's open up the HTML page. You should see "IT WORKS" in the browser". 

If you see the example in the gif about, you can see it's not a window or document scroll. If you want to listen for a window scroll event you just listen for `window.addEventListener()`. 

If it's the case of another element that has an overflow scroll set on it, like Wess has done in the following style that is on the `scroll-to-accept.html` 👇

```
.terms-and-conditions {
  overflow: scroll;
}
```

we have to select that element and listen for a scroll on it. 

Select the terms and conditions class

```
const terms = document.querySelector('terms-and-conditions');
```

Let's add an event listener to terms on the scroll event and just log the event with the handler. 

```
terms.addEventListener('scroll', function(e){
  console.log(e); 
});
```

If you refresh the page, you will see the following error in your console

scroll-to-accept.js:3 Uncaught TypeError: Cannot read property 'addEventListener' of null
    at scroll-to-accept.js:3

    sttoppped at 1:57














