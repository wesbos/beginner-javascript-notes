---
attachments: [Clipboard_2020-03-15-15-15-20.png, Clipboard_2020-03-15-15-31-07.png, Clipboard_2020-03-15-15-31-09.png, Clipboard_2020-03-15-16-06-43.png, Clipboard_2020-03-15-16-18-16.png, Clipboard_2020-03-15-16-29-54.png, Clipboard_2020-03-15-16-36-41.png, Clipboard_2020-03-15-16-38-41.png, Clipboard_2020-03-15-16-40-43.png, Clipboard_2020-03-15-16-41-17.png, Clipboard_2020-03-15-18-01-03.png, Clipboard_2020-03-15-18-32-04.png]
title: 'Module 6: Serious Practice Excercises'
created: '2020-03-15T19:10:20.059Z'
modified: '2020-03-15T22:43:57.876Z'
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

We will add an if statement, which we haven't learned about before, but if conditions essentially check if something is true (whether it evalutes to boolean true or false), and then runs a block of code based on that condition. Here we will check whether the key includes the word arrow, and if it does, we will move the logic to log to the console within the if block like so:

```  
if (e.key.includes("Arrow")) {
    console.log(e.key);
    console.log("HANDLING KEY");
}
```

stopped at 20:00
