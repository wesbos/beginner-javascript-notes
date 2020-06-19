---
attachments: [Clipboard_2020-06-18-06-40-04.png, Clipboard_2020-06-18-06-49-00.png, Clipboard_2020-06-18-06-50-34.png, Clipboard_2020-06-18-06-52-14.png, Clipboard_2020-06-18-06-53-02.png, Clipboard_2020-06-18-07-03-08.png, Clipboard_2020-06-18-07-03-22.png, Clipboard_2020-06-18-07-05-02.png, Clipboard_2020-06-18-07-27-38.png, Clipboard_2020-06-18-19-19-53.png, Clipboard_2020-06-18-19-24-57.png, Clipboard_2020-06-18-19-28-57.png, Clipboard_2020-06-18-19-29-56.png, Clipboard_2020-06-18-19-31-17.png, Clipboard_2020-06-18-19-32-12.png, Clipboard_2020-06-18-19-33-33.png, Clipboard_2020-06-18-19-37-39.png, Clipboard_2020-06-18-19-38-28.png, Clipboard_2020-06-18-19-40-50.png, Clipboard_2020-06-18-19-44-55.png, Clipboard_2020-06-18-19-57-42.png, Clipboard_2020-06-18-19-58-12.png, Clipboard_2020-06-18-20-01-11.png, Clipboard_2020-06-18-20-03-05.png, Clipboard_2020-06-18-20-06-54.png, Clipboard_2020-06-18-20-08-22.png, Clipboard_2020-06-18-20-08-25.png, Clipboard_2020-06-19-08-46-17.png, Clipboard_2020-06-19-08-49-41.png, Clipboard_2020-06-19-10-06-10.png, Clipboard_2020-06-19-10-06-28.png, Clipboard_2020-06-19-10-07-52.png, Clipboard_2020-06-19-10-14-13.png, Clipboard_2020-06-19-10-21-16.png, Clipboard_2020-06-19-10-24-50.png, Clipboard_2020-06-19-10-25-21.png, Clipboard_2020-06-19-10-28-37.png, Clipboard_2020-06-19-10-37-23.png, Clipboard_2020-06-19-10-42-21.png, Clipboard_2020-06-19-10-46-19.png, Clipboard_2020-06-19-11-03-19.png, Clipboard_2020-06-19-11-15-55.png, Clipboard_2020-06-19-11-25-39.png, Clipboard_2020-06-19-11-38-41.png, Clipboard_2020-06-19-11-48-48.png, Clipboard_2020-06-19-11-49-59.png, Clipboard_2020-06-19-11-53-50.png, Clipboard_2020-06-19-12-18-16.png, Clipboard_2020-06-19-12-20-30.png, Clipboard_2020-06-19-12-31-50.png, Clipboard_2020-06-19-12-34-19.png, Clipboard_2020-06-19-12-35-04.png, Clipboard_2020-06-19-12-36-15.png, Clipboard_2020-06-19-12-41-22.png, Clipboard_2020-06-19-12-42-08.png, Clipboard_2020-06-19-13-02-06.png, Clipboard_2020-06-19-13-04-09.png]
title: Module 15 - Final Round of Exercises
created: '2020-06-18T10:37:29.455Z'
modified: '2020-06-19T17:05:23.866Z'
---

# Module 15 - Final Round of Exercises 

--- 

## 84 - Web Speech Colours Game

![](@attachment/Clipboard_2020-06-09-06-45-57.png) 00:27

In this exercise we will be using the Speech Recognition API that is currently only available in the Chrome broswer to practice our Javascript skills by building a little game. 

The way it will work is When you say a colour, the background colour of the website should change to reflect that. 

Let's start by opening chrome and navigating to `chrome://flags` in the browser. On this paeg, we need to make sure that "Experimental Web Platform features" are turned on. '

![](@attachment/Clipboard_2020-06-09-06-50-08.png) 1:02

We also need to get a server going. 

If you open up the `84 - Web Speech Colour Game` folder within the `exercises` directory, lets take a look at what we are working with. 

Wes has given us `colors.js` which gives us an object containing every color that is available in CSS, and it's corresponding hex code. 

Within the file there is also a function called `isDark` which Wes grabbed from StackOverFlow which takes in a color name and figures out if it is a dark or light color.

Then there is `style.css` which contains a few styles and animations, like the word popping up and getting crossed off when you say it. 

![](@attachment/Clipboard_2020-06-09-06-55-21.png) 2:26

If look at the `package.json`, you will see we have `parcel-bundler` and `browserslist`, both of which we have used before. 

Open up the terminal and navigate to the exercises folder and type `npm install` and that will install the dev dependencies for us. 

After that is finished installing, simply type `npm start` and open up the server in a browser to see what we are starting with. 

![](@attachment/Clipboard_2020-06-09-06-58-40.png)  3:20  

Let's start by getting the web speech going and then we will connect the colours.

Now we need to check if there is something called `window.SpeechRecognition`. However if you try to reference that in the console, you will get undefined because it is actually `window.webkitSpeechRecognition`. 

![](@attachment/Clipboard_2020-06-09-07-01-04.png) 4:10

Add the following to `speech.js`. 

```
//speech.js
function start(){
  //see if their browser supporst this

}
start();
```

That is what is referred to as vendor prefix (adding `webkit`). That means that the API is not completely done, so they will vendor prefix it by adding webkit infront of it. 

Chrome engine used to be called WebKit, it is now called blink.

At the top of our javascript file, let's normalize that like so: 

```
//speech.js
window.SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition. 
```

Now in our chrome tools we can access it like so: 

![](@attachment/Clipboard_2020-06-09-07-07-43.png) 5:02

Now within `start` let's check if it there is a property called 'SpeechRecognition` that is in the window.

![](@attachment/Clipboard_2020-06-09-07-08-43.png) 5:29

```
//speech.js
function start(){
  //see if their browser supports this
  if(!('SpeechRecognition` in window)){
    console.log('Sorry your browser does not support speech reco.');
    return;
  }
  console.log('Starting...');
}

start();
```

If the API does exist in the user's browser, let's make a new speech recognition instance. 

```
const recognition = new SpeechRecognition();
```

Now we need to set a few options. Let's set it to continuously listening for speech recognition instead of stopping itself when the speech has been recognized (similar to how Siri stops listening after completing actions) like so:

```
const recognition = new SpeechRecognition();
recognition.continuous = true;
```

Let's also set `recognition.interimResults = true`, which will give us the results as we are speaking instead of waiting till you are done speaking. 

We also need to hook up an event listener.

This is a little bit different than most event listeners because normally you would add `.addEventListener`. but if you try to log our `recognition` variable and look at the prototype, you will see there is no method like `addEventListener`.

![](@attachment/Clipboard_2020-06-18-06-40-04.png) 7:30

So how do we listen for a result? You can listen for an event like this...

```
recognition.onresult = handleResult;
```

Next we need to start it like so:

```
recognition.start();
```

Now let's create another file called `handlers.js`. Inside of that, we will have a function `handleResutl` which for now will just log the event, and we will export the function. 

```
export function handleResult(event){
  console.log(event);
}
```

Now within `speech.js` we will import that function.

```
import handleResult from './handlers';
```

This time we do not have to include the `.js` extension when importing from `handlers.js` because we are using Parcel.

Now when you refresh the page, you may be prompted to accept permissions to the microphone.

![](@attachment/Clipboard_2020-06-18-06-49-00.png) 8:41

In our case we want to allow it, so go ahead and do that and then refresh the page. Now it should be listening to our voice, and you should events streaming as we speak. 

![](@attachment/Clipboard_2020-06-18-06-50-34.png) 9:27

If you open up one of the SpeechRecognitionEvents that have been logged in the console, you will see it is very similar to an event object.

![](@attachment/Clipboard_2020-06-18-06-52-14.png) 9:38

However we have this property called resuls. Within that property there will be a few items that the speech recognition thinks you said. 

![](@attachment/Clipboard_2020-06-18-06-53-02.png) 9:55

In our case, we will be taking both of the results. 

It will keep giving us words as it tries to figure out what you said. Even after you stop talking, it keeps streaming the results in until it is confident in the result. 

Now within our `handlers.js` file, let's create another function `logWords` that takes in the results and for now we will just log them. 

We will call this new function from our `handleResult` method. 

```
//handlers.js
function logWords(results){
  console.log(results);
}

export function handleResult(event){
  logWords(event.results);
}

```

Sometimes the SpeechRecognition event will return a list, from which we want to grab the last one. 

![](@attachment/Clipboard_2020-06-18-07-03-22.png) 10:53

Within the last one, Wes has only ever run into there being one `SpeechRecognitionAlternative` from which we can grab the transcript.

Let's log that in our `logWords` function by modifying it like so: 

```
//handlers.js
function logWords(results){
  console.log(results[results.length - 1][0].transcript);
}
```

Now if you refresh the page and try to say something like "I love Pizza", you will see that logged in the console. 

![](@attachment/Clipboard_2020-06-18-07-05-02.png) 11:16

So what we are doing there is we are accessing the deeply nested property on the results object. 

Now that we have the speech being chimed in, lets go and get the color layout working. 

We want to loop over each of the colours in `colors.js` and display it as a span on our page. 

One thing you might have noticed is Wes has stored the colors by the length of the name.

Within that file, let's add the following code and export it. 

```
//colors.js
export const colorsByLength = Object.keys(colors)

console.log(colorsByLength);
```

Let's import that function into `speech.js` like so:

```
import { handleResult } from "./handlers";
import { colorsByLength } from "./colors";
```

![](@attachment/Clipboard_2020-06-18-07-27-38.png) 13:37

As you can see if you refresh the page and open the console, that gives us an array of all the colors. 

Next we need to run a sort command on the colors array command based on their length, like so:

```

export const colorsByLength = Object.keys(colors).sort(a,b => {
  return a.length - b.length;
});

console.log(colorsByLength);
```

As a refreshing from our sorting course:
If you return a postive number, it will put the item in front.
If you return a negative number it will put it behind.
If you return 0 it will not move that item. 


Now if you refresh the page, you will see that the colors are now sorted by length. 

![](@attachment/Clipboard_2020-06-18-19-19-53.png) 14:10

Now within `speech.js` let's write the function to display the colors. 

```
//speech.js
import { handleResult } from "./handlers";
import { colorsByLength } from "./colors";

function displayColors(colors){
  colors.map(color =>  `<span class="color">${color}</span>`)
}

```

At the very bottom of the file, let's call that right away. 

```
//speech.js
start();
displayColors();
```

Now within displayColors, we will map through each color and return a span with the class of color and the colors name. 

```
function displayColors(colors){
  colors.map(color =>  `<span class="color">${color}</span>`)
}
```

![](@attachment/Clipboard_2020-06-18-19-24-57.png) 15:27

As you can see, in our `index.html`, we have a div with the class of colors. We will select that on page load. 

```
//speech.js
import { handleResult } from "./handlers";
import { colorsByLength } from "./colors";

const colorsEl = document.querySelectors('.colors');
```

Next we will replace where we call displayColors and instead set the value of `colorsEl.innerHTML` to the value returned from `displayColors()`

```

//speech.js
import { handleResult } from "./handlers";
import { colorsByLength } from "./colors";

const colorsEl = document.querySelectors('.colors');
 
function displayColors(colors){
  colors.map(color =>  `<span class="color">${color}</span>`)
}

window.SpeechRecognition =
  window.SpeechRecognition || window.webkitSpeechRecognition;

function start() {
  // see if their browser supports this
  if (!('SpeechRecognition' in window)) {
    console.log('Sorry your browser does not support speech reco. ');
    return;
  }
  // it does work
  console.log('Starting...');
  // make a new speech reco
  const recognition = new SpeechRecognition();
  recognition.continuous = true;
  recognition.interimResults = true;
  recognition.onresult = handleResult;
  recognition.start();
}

start();
colorsEl.innerHTML = displayColors();
```

However now when we refresh the page, you might notice that we get the following error: 

![](@attachment/Clipboard_2020-06-18-19-28-57.png) 16:06

That issue is happening because we did not pass in the colors. Let's fix that. 

```
colorsEl.innerHTML = displayColors(colorsByLength);
```

However now you will see that on the page we just see undefined and there is nothing in the console. 

![](@attachment/Clipboard_2020-06-18-19-29-56.png) 16:18

If you go to our `speech.js` file, yu will see that we forgot to return the colros map in our `displayColors` function. 

```
//speech.js
function displayColors(colors){
  return colors.map(color =>  `<span class="color">${color}</span>`)
}
```

![](@attachment/Clipboard_2020-06-18-19-31-17.png) 16:26

As you can see, now it works. That gives us a list of all the colors. 

To get rid of the commas we can call `.join('');` like so: 


```
//speech.js
function displayColors(colors){
  return colors.map(color =>  `<span class="color">${color}</span>`),join('');
}
```

![](@attachment/Clipboard_2020-06-18-19-32-12.png) 16:38

Now lets add some style properties to each of the colors. We will set the background to be the name of the colors. 

```
//speech.js

function displayColors(colors) {
  return colors
    .map(
      color =>
        `<span class="color" style="background: ${color};">${color}</span>`
    )
    .join('');
}

```


![](@attachment/Clipboard_2020-06-18-19-33-33.png) 16:55

Next we want to know if the color is light or dark so we can change the color of the text accordingly to the CSS Wes wrote ahead of time. 

To do that we can import the `isDark` function from our `colors` module like so: 

```

//speech.js
import { handleResult } from "./handlers";
import { colorsByLength, isDark  } from "./colors";

```


That function will return true or false so we can use that within our backticks to determine what text color to show. 

```
//speech.js
function displayColors(colors) {
  return colors
    .map(
      color =>
        `<span class="color ${
          isDark(color) && 'dark' }" style="background: ${color};">${color}</span>`
    )
    .join('');
}
```
 
 ![](@attachment/Clipboard_2020-06-18-19-37-39.png) 17:40

As you can see, that gives all the class of dark to the dark ones and a class of light to the light ones.

 ![](@attachment/Clipboard_2020-06-18-19-38-28.png) 17:46

Actually if you inspect the element in the dev tools, you will see that the classes that are dark have the dark class but the classes that are light are returning a false class. We do not want to return a false class. 

Let's fix that by using at ternary statement instead of the &&. 

```
//speech.js
function displayColors(colors) {
  return colors
    .map(
      color =>
        `<span class="color ${
          isDark(color) ? 'dark' : ''
        }" style="background: ${color};">${color}</span>`
    )
    .join('');
}
```

![](@attachment/Clipboard_2020-06-18-19-40-50.png) 17:59

As you can see, no class of "false" is being return any longer. 

Now let's go into our `handlers.js` and actually do something with the word that the user has said. 


```
//handlers.js

function logWords(results) {
   console.log(results[results.length - 1][0].transcript);
}

export function handleResult(event){
  logWords(event.results);
  const words =  results[results.length - 1][0].transcript;
  console.log(words);
}
```

Now if you refresh the page and try to say red, you will see an error logged complaining that results is not defined.  

![](@attachment/Clipboard_2020-06-18-19-44-55.png) 18:29

To fix that, let's destructure the resutls property in the function defintions. 

```
export function handleResult({results }){
  logWords(results);
  const words = results[results.length - 1][0].transcript;
  console.log(words);
}
```

Now if you refresh the page, you will see the speech streaming in. Now what we need to do is check whether the word that is streaming in is a valid color. 

In order to check, we need to first lowercase everything so we don't have to deal with upper and lowercase versions. 
We also want to strip any spaces out because sometimes the SpeechRecognition will return spaces in front of the word. 
If it is a valid color, show the UI for that. 

```
export function handleResult({results }){
  logWords(results);
  const words = results[results.length - 1][0].transcript;
  console.log(words);
  //lowercase everything
  //strip any spaces out
  //check if its a valid colour
  // if it is, then show the UI for that  
}
```

Let's start by first lowercasing.

```
//handlers.js

//lowercase everything
const color = words.toLowerCase();
```

Next we will strip any spaces out. To do that we need to modify the color variable to be a let. We will be replacing all spaces with nothing.

If you have only one space to replace you can use `replace()` like so: 

```
//handlers.js

//strip any spaces out
color  = color.replace(' ', '');
```

However if there is more than one space, you have to use a Regex. There is a new `replaceAll` method coming, which will do that for you but it is not in the browsers yet. 

So let's use a Regex for our replace method instead, which will match all spaces. The regex to match a space is `/\s/` and the if you pass a `/g` flag that means global, so find them all. 


```
//handlers.js

//strip any spaces out
color = color.replace(/\s/g, '');
```

Next we want to check if it is a valid color. 

Lets go into our `colors.js` module and add a new function and immediately export it.

```
export function isValidColor(word){
  return colors[word];
}
```

That will return the actual hex if there is something matching. It will return undefined if there is no match. In our case, we do not want the hex, we want a boolean. 

We can add a double bang to coerce it to return true or false like so: 

```
export function isValidColor(word){
  return !!colors[word];
}
```

How that works is calling `colors.red` will return the hex, but calling `!!colors.red` will return true and if the property doesn't exist, it will return false. 

![](@attachment/Clipboard_2020-06-18-19-57-42.png) 22:22

We could also use the `in` syntax and it would give us the same results. 

![](@attachment/Clipboard_2020-06-18-19-58-12.png) 22:35

Next we can import that into our `handlers.js`.

```js
//handlers.js
import { isValidColor } from './colors';

function logWords(results) {
  // console.log(results[results.length - 1][0].transcript);
}

export function handleResult({ results }) {
  logWords(results);
  const words = results[results.length - 1][0].transcript;
  // lowercase everything
  let color = words.toLowerCase();
  // strip any spaces out
  color = color.replace(/\s/g, '');
  // check if it is a valid colour
  if (!isValidColor(color)) return; // thats all folks
  console.log("This is a valid color!")
}
```

If you try talking now and say a valid color, you should see the message "This is a valid color!" pop up.

Now if it is a valid color, let's start working on the UI.

Let's start by crossing the word out. Let's select the span with a class of color... Oh no. We have run into an issue. We need a way to select a specific span. 

![](@attachment/Clipboard_2020-06-18-20-01-11.png) 24:34

Let's add the color name as a class as well. Go back and modify our `speech.js` code like so: 

```
//speech.js

function displayColors(colors) {
  return colors
    .map(
      color =>
        `<span class="color ${color} ${
          isDark(color) ? 'dark' : ''
        }" style="background: ${color};">${color}</span>`
    )
    .join('');
}
```

Now back to our `handleResults` function, we can select the color span that was spoken like so: 

```
// if it is, then show the UI for that
const colorSpan = document.querySelector(`.${color}`);
console.log(colorSpan);
```

![](@attachment/Clipboard_2020-06-18-20-03-05.png) 25:22

If you refresh and try, you should see the span logged. 

If you open up the css file, you will see we have a class of `.got`. 

```
//style.css
colors span.got {
  text-decoration: line-through;
  animation: jump 0.2s ease-in-out 2 alternate-reverse;
}
```

That gives an animation of jump which scales up the item and scales it back down. Let's add that class to the span once it has been spoken. 


```
export function handleResult({ results }) {
  logWords(results);
  const words = results[results.length - 1][0].transcript;
  // lowercase everything
  let color = words.toLowerCase();
  // strip any spaces out
  color = color.replace(/\s/g, '');
  // check if it is a valid colour
  if (!isValidColor(color)) return; // thats all folks
  // if it is, then show the UI for that
  const colorSpan = document.querySelector(`.${color}`);
  colorSpan.classList.add('got');
  console.log(colorSpan);
  console.log('This is a valid color!');
  console.log(color);
}
```


![](@attachment/Clipboard_2020-06-18-20-06-54.png) 26:57

As you can see it is giving the span with the color a class of got and animating it once the color is spoken. 

We also want to change the background color: `document.body.style.backgroundColor = color;`

```
export function handleResult({ results }) {
  logWords(results);
  const words = results[results.length - 1][0].transcript;
  // lowercase everything
  let color = words.toLowerCase();
  // strip any spaces out
  color = color.replace(/\s/g, '');
  // check if it is a valid colour
  if (!isValidColor(color)) return; // thats all folks
  // if it is, then show the UI for that
  const colorSpan = document.querySelector(`.${color}`);
  colorSpan.classList.add('got');
  console.log(colorSpan);
  console.log('This is a valid color!');
  console.log(color);
  // change the background color
  document.body.style.backgroundColor = color;
}
```

Now the page will change color when the word is spoken as well. 

![](@attachment/Clipboard_2020-06-18-20-08-25.png) 28:03



---

## 85 - Audio Visualization

![](@attachment/Clipboard_2020-06-19-08-46-17.png) 00:16

In this lesson, we will be using the Web Audio API which is really cool. 

There is a whole spectrum of Javascript which is working with audio. Wes does not know a lot about how audio works but he understands things like frequency and time and using that we will build this cool audio visualizer that you seen in the screenshot above. 

The rainbow bar graph represents the frequencies and the yellow line is time data as the audio is coming in. We are just painting those two things to canvas. 

By the end of the lesson, it will all probably only be around 100 lines of code, which is pretty cool. 

We are working out of the `85 - Audio Visualizer Oscilloscope` exercise folder. Open up a terminal, cd into that directory and run `npm install`. 

If you take a look at our `package.json` file, you will see we have one dev dependency, Parcel, a start script and browserslist. 

We will be starting with the following HTML. 

```
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Audio Analyzer</title>
</head>

<body>
  <canvas></canvas>
  <script src="./sound.js"></script>

  <style>
    html {
      margin: 0;
      background: black;
    }

    canvas {
      width: 100%;
      height: 100%;
    }

    body {
      min-height: 100vh;
      display: grid;
      grid-template-rows: 1fr;
      margin: 0;
    }
  </style>
</body>

</html>
```


We have a blank canvas and a script tag for the sound. Then we have basic styles, which Wes is using to stretch the canvas to be whatever the width and height of the window. 

This will be working off of the microphone, but if you want it to work to music, you have a couple of options. 

There are some APIs to pipe it in from an audio element. We are not going to go into those, because we are just doing microphone for now. You can always just unplug your headphones and play your music over your speakers and that will make it back into your microphone. The last option is this app called LoopBack which allows you to take apps like Spotify and pipe that into the microphone. That is a paid app however, and not something you probably need. Wes just wanted to show us how he is doing it.

Open up `sound.js`. The first thing that we want to do is have a `WIDTH` and a `HEIGHT` variable. 

The value we assign to those two variables doesn't actually matter that much. If you assign them a lower number, it is going to be much more responsive. If you do a higher number, it is going to really slow down your computer. You have to find what works for you. Wes has found the following values work well on hish computer. 

```
const WIDTH = 1500;
const HEIGHT = 1500;
```

If you find that those values are two high for your computer and it is too slow, feel free to adjust. All the calculation we will be doing will be based off these variables, so there is no issue swapping out that variable value.

Next we need to grab the canvas element and the context and then we will size up the canvas to be the width and height values that we set in the variables. 

```
const WIDTH = 1500;
const HEIGHT = 1500;
const canvas = document.querySelector('canvas');
const ctx = canvas.getContext('2d');
canvas.width = WIDTH;
canvas.height = HEIGHT;
```

If the `npm install` you ran earlier is finished, you can go ahead and run `npm run start` to start the server. Click the link in the termninal to open up the server in your browser. 

There are kind of two that are going to go on here. First, we need to actually get the audio and the data about the frequency, time and all that. Then we want to draw the frequency bars that are along the bottom as well as draw the time data. 

Let's start with the audio.

We need to make an async function called `getAudio` and within that function we need to get access to the user's microphone. That is why we are running this example on a server, as we can only access the microphone on a server that is secure origin on HTTPS or localhost. The browser will not allow you to have access to the webcam, microphone or any of those API's unless you are on a secure origin. 

```
 const stream = await navigator.mediaDevices
    .getUserMedia({ audio: true })
```

This is exactly the same API we used in previous lessons, the only difference is this time we are passing `audio: true`. That is because we do not want access to use the webcam. 

Next we need to get the audio context in the browser. The audio context will be where all the processing is done. 

```
const audioCtx = new AudioContext();
```

So we have this audio context, and inside of there we can create an analyzer. 

We will also write a few functions that will need access to that analyzer. Those functions will be responsible for: getting the audio, drawing the frequency bars, and drawing the time bars. All three of those need access to the audio context. 

To solve this, let's create a variable at the top of the file. We could also pass it in as an argument to the functions, but because the logic of this will already be complex, we want to make it as simple as possible so we will scope it to the sound.js module. 

```
//sound.js
const WIDTH = 1500;
const HEIGHT = 1500;
const canvas = document.querySelector('canvas');
const ctx = canvas.getContext('2d');
canvas.width = WIDTH;
canvas.height = HEIGHT;
let analyzer;
```

Now we will take that variable and assign it to the value of `audioCtx.createAnalyser()`. 

```
async function getAudio() {
  const stream = await navigator.mediaDevices.getUserMedia({ audio: true })
  const audioCtx = new AudioContext();
  analyzer = audioCtx.createAnalyser();

}
```

Next we need to create a source which will take our stream and pipe that into the audio context. The idea with the whole context thing is that you can take data and then pipe it through your context, do stuff to it like change frequency and time and then you pipe the data out, very similar to how it would work if you had physical audio devices. 

Let's take out audio context and call `createMediaStreamSource(stream)` on it. Then we will need to take that source and connect it to the analyzer. That should have wired everything up for us. 


```
async function getAudio() {
  const stream = await navigator.mediaDevices.getUserMedia({ audio: true })
  const audioCtx = new AudioContext();
  analyzer = audioCtx.createAnalyser();
  const source = audioCtx.createMediaStreamSource(stream);
  source.connect(analyzer);
}
```

Now that we have the analyzer, we need to figure out how much data we want access to because you can get really detailed and sample a lot of data or sample just a bit of data. 

Here is an example with a lot of data: 

![](@attachment/Clipboard_2020-06-19-10-06-10.png) 10:28

And here is an example with just some data: 

![](@attachment/Clipboard_2020-06-19-10-06-28.png) 10:32

It is up to us how much data we want to collect. To set that we use the `fftSize` property of the analyzer. If you are curious you can look up the docs for that property but essentially that iwhat we use to set how much data should be collected.

![](@attachment/Clipboard_2020-06-19-10-07-52.png) 11:24

We will set it to be 2 to the power of 10, which you represent using two multiplication signs like so: 

```
analyzer.fftSize = 2 ** 10;
```

Now that we have that, let's go ahead and pull the data off the audio. We will grab that in an array.

```
const timeData = new Uint8Array(analyzer.frequencyBinCount);
```

Let's break that down starting with looking up the docs for the Uint8Array.

![](@attachment/Clipboard_2020-06-19-10-14-13.png) 14:22

What does that all mean? Well the data that we are getting back from the time data is 8 bits or 1 byte. This is getting pretty nerdy but essentially if you have an array, normal arrays you can put as much data as you want in every single item. However with this special array, each item can only ever be 8 bits of 1 byte (8 bits is 1 byte). 

What that allows us to do is if we know ahead of time how big each of them are, we can make really big arrays, meaning that they are typed and we are not accidentally going to put some data in there that does not work for us. This is useful for heavy lifting like data analysis. You also see those special types of arrays when working with graphics as well. 

Lets go ahead and log `timeData`, which is our new array containing data about the time. Let's also add a call to run `getAudio()` on runtime. 

```
async function getAudio() {
  const stream = await navigator.mediaDevices.getUserMedia({ audio: true })
  const audioCtx = new AudioContext();
  analyzer = audioCtx.createAnalyser();
  const source = audioCtx.createMediaStreamSource(stream);
  source.connect(analyzer);
  // How much data should we collect
  analyzer.fftSize = 2 ** 10;
  // pull the data off the audio
  const timeData = new Uint8Array(analylzer.frequencyBinCount);
  console.log(timeData);
}

getAudio();
```

Now when the page refreshes, we should see an array of audio logged to the console. However, we are currently seeing an error "Uncaught (in promise) DOMException: Permission denied

![](@attachment/Clipboard_2020-06-19-10-21-16.png) 15:35

What is happening there is our call to `getUserMedia` has been denied. Let's create a `handleError` function that logs "You must give access to your mic in order to proceed". Then let's modify our call to `getUserMedia` to chain a `catch()` on it and pass it our `handleError` function. 


```
//sound.js
function handleError(err) {
  console.log('You must give access to your mic in order to proceed');
}

async function getAudio() {
  const stream = await navigator.mediaDevices
    .getUserMedia({ audio: true })
    .catch(handleError);
  
```

Now we will see the following log instead: 

![](@attachment/Clipboard_2020-06-19-10-24-50.png) 16:05

To allow access, you need to click here within chrome: 

![](@attachment/Clipboard_2020-06-19-10-25-21.png) 16:07

Now when you refresh the page, you will see we get an array. At first they will all contain zeros but as we keep talking and keep sampling the data, it will fill up with a bunch of numbers that represent the frequencies and the time data in what we say. 

Let's make the second one as well for frequency. 

```
const frequencyData = new Uint8Array(analyzer.frequencyBinCount);
console.log(frequencyData);
```

![](@attachment/Clipboard_2020-06-19-10-28-37.png) 16:49

Now we have these two empty arrays with the right amount of slots that we are going to fill up with data.

Next we will make a function called `drawTimeData(timeData)`, which will need to run as frequently as possible. 

What we will do is we will initially call it within our `getAudio` method.

```
async function getAudio() {
  const stream = await navigator.mediaDevices
    .getUserMedia({ audio: true })
    .catch(handleError);
  const audioCtx = new AudioContext();
  analyzer = audioCtx.createAnalyser();
  const source = audioCtx.createMediaStreamSource(stream);
  source.connect(analyzer);
  // How much data should we collect
  analyzer.fftSize = 2 ** 8;
  // pull the data off the audio
  // how many pieces of data are there?!?
  bufferLength = analyzer.frequencyBinCount;
  const timeData = new Uint8Array(bufferLength);
  const frequencyData = new Uint8Array(bufferLength);
  drawTimeData(timeData);
}

```

 Now within the drawTimeData we will log the `timeData` array, and we will make the function call itself as soon as possible. To do that, we will use `requestAnimationFrame`. 

That allows us to tell the browser that the next time it is possible to paint the screen again, can you call the `drawTimeData` function again. To do that we will use an array function like so:

```
function drawTimeData(timeData){
  console.log(timeData);
  //call itself as soon as possible
  requestAnimationFrame(()=> drawTimeData(time));
}
```

Now when you refresh you will see we have this stream of data coming in. 

![](@attachment/Clipboard_2020-06-19-10-37-23.png) 18:03

It is all still zeros because it was 0 initially but we have another method that will allow us to pull the data out of it: `analyzer.getByteTimeDomainData(timeData);`

This method is a bit weird. How it works is it allows us to inject our time data into our `timeData` array. Now when we log `timeData`, you should see as you talk, the numbers go from 128 all the way to 255. 

```
function drawTimeData(timeData) {
  analyzer.getByteTimeDomainData(timeData);
  console.log(timeData);
  //call itself as soon as possible
  requestAnimationFrame(() => drawTimeData(time));
}
```

![](@attachment/Clipboard_2020-06-19-10-42-21.png) 19:13

That data is a visual representation of the words that Wes is speaking. 

Now that we have that data, let's turn it into something visual, starting with drawing with the canvas.

The first thing we need to do is clear the canvas. Let's leave a TODO for ourselves and move onto the next steps so you can see what happens when we do not clear the canvas. 

The next steps involve setting the `lineWidth`, `strokeStyle` and calling the `beginPath()` method on the canvas context. 
 
```
function drawTimeData(timeData) {
  // inject the time data into our timeData array
  analyzer.getByteTimeDomainData(timeData);
  // now that we have the data, lets turn it into something visual
  // 1. Clear the canvas TODO
// 2. setup some canvas drawing
  ctx.lineWidth = 10;
  ctx.strokeStyle = "#ffc600";
  ctx.beginPath();
```

Next what we need to do is figure out how long each line will be. 

![](@attachment/Clipboard_2020-06-19-10-46-19.png) 21:06

Let's use the example above and assume there are 8 pieces of data we have to represent that visual. That means we need to draw lines between each of those data points like a line graph. 

We need to figure out how wide each of those lines are going to be because we have 1500 pixels, and then we have 8 pieces of data. 1500 / 8 = 187.5. That eans each line is going to be above 188 pixels wide. Or if we had 512 pieces of data, each line would be about 2-3 pixels wide (1500/512 = 2.9).

Everytime we draw something, like the 7 bar graph pieces you see in the visual above, we will call each piece a slice. So let's figure out what the sliceWidth is equal to. 


We do that by taking the `WIDTH` variable and dividing it by the array of time data, which we will call a buffer. 

Let's go ahead and make a new variable for that. The buffer length is `analyzer.frequencyBinCount` but that is hard to understand. 

```
const WIDTH = 1500;
const HEIGHT = 1500;
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");
canvas.width = WIDTH;
canvas.height = HEIGHT;
let analyzer;
let bufferLength;
```

Now within `drawTimeData()` add the following code `const sliceWidth = WIDTH / bufferLength;`. That should give us how big each slice will be. Let's also log that value and then refresh the page. 

![](@attachment/Clipboard_2020-06-19-11-03-19.png) 23:16

That gives us 2.9 pixels long. 

If we were to modify the `WIDTH` variable to 2500, that value will go up to 4.88 pixels wide per slice. 

Wes is not going to round that because canvas does a good enough job of rounding those values for us. 

Now that we have the slice width, we need an x variable which we will set to 0. 

```
let x = 0;
```

The reason for that is we will loop over each piece of our time data and we will increment that by the slice width everytime we loop over it. 

We will use the `forEach` loop here. That will take in two arguments, the first being the data and the second being our index variable. 

Within the loop, we will create a variable `v` that will be equal to the data, and then divide that by 128. The reason we do that is because if you recall, when you are not speaking, it returns 128 and then when you start speaking it goes up. So the `v` variable is going to be a multiplier that we will use in drawing the data (that will make sense in just a second).

Then we also want to make a `y` value. 

![](@attachment/Clipboard_2020-06-19-11-15-55.png) 25:09

Take the visual above as an example. 

We have this line going left to right on the X axis, but we also need to know how high or how low that the line needs to go which will be based on our `y` value. 

To calculate that we will take our `v` variable and multiply it by our `HEIGHT` variable and divide that by 2. 

```
const y = (v * HEIGHT) / 2;
```

You might be thinking that this is a lot of math, and that is how a lot of graphics and stuff is done, there is lots of division and multiplication to scale thigns up and down. 

Now let's start to draw our lines within the forEach. 

We need to first check whether the item is the first item in the array. We can use the `i` variable to tell the index of the current element from the array that is being processed. 

If it is the first element, we want to move it to the x and y coordinates. Otherwise, we will call `lineTo()` like so: 

```
if(i === 0){
  canvas.moveTo(x, y);
}
else {
  canvas.lineTo(x,y);
}
```

Next we need to call `x += sliceWidth;`. That will move our x axis along everytime that we loop over. 

However now if you refresh the page, you will see an error complaining that "canvas.moveTo is not a function".  

That is because we are supposed to be calling `moveTo` and `lineTo` on the `ctx` not canvas. Modify the code like so: 


```
if(i === 0){
  ctx.moveTo(x, y);
}
else {
  ctx.lineTo(x,y);
}
```

Now outside of the forEach we will call `ctx.stroke()`. 

```
function drawTimeData(timeData) {
  // inject the time data into our timeData array
  analyzer.getByteTimeDomainData(timeData);
  // now that we have the data, lets turn it into something visual
  // 1. Clear the canvas TODO
  // 2. setup some canvas drawing
  ctx.lineWidth = 10;
  ctx.strokeStyle = "#ffc600";
  ctx.beginPath();
  const sliceWidth = WIDTH / bufferLength;
  let x = 0;
  timeData.forEach((data, i) => {
    const v = data / 128;
    const y = (v * HEIGHT) / 2;
    // draw our lines
    if (i === 0) {
      ctx.moveTo(x, y);
    } else {
      ctx.lineTo(x, y); 
    }  
    x += sliceWidth;
  });

  ctx.stroke();

  // call itself as soon as possible
  requestAnimationFrame(() => drawTimeData(timeData));
}
```

![](@attachment/Clipboard_2020-06-19-11-25-39.png) 26:51

What is happening there is that every single time we are drawing something, it is drawing that to the page. 

We take our huge array of data, loop over each piece of that data, draw it to the canvas, and then finall run `stroke()` at the very end and that will just paint it to the thing. 

Let's go back to the TODO that we left for the first step where we need to clear the canvas and actually add that code. 

```
// 1. Clear the canvas TODO
  ctx.clearRect(0, 0, WIDTH, HEIGHT);
```

![](@attachment/Clipboard_2020-06-19-11-38-41.png) 27:31
[ANJA ADD GIF HERE: 27:33 into video]

Now every single time that this runs, we first clear out the canvas so it looks like it is actually animating. That is just us painting very very quickly however. 

Now lets go back to the place in the code where we set the `fftSize`.  Let's try modifying it to be `analyzer.fftSize = 2 ** 6;`

![](@attachment/Clipboard_2020-06-19-11-48-48.png) 28:00

The higher limit is 32768. Let's try setting it to that like so: `analyzer.fftSize = 32768;`. 

![](@attachment/Clipboard_2020-06-19-11-49-59.png) 28:14

As you can see when we set it to the upper limit, we have tons of data streaming in. Let's bring that back to be 2 to the power of 10 instead. 

That is the first visualization. 

Now let's do it again but this time for the frequency data. 

Wes will demonstrate this using a frequency app. 

ANJA INSERT GIF HERE 29:21

![](@attachment/Clipboard_2020-06-19-11-53-50.png) 29:25

As you can see the different frequencies in the audio will affect how high the graph goes. 

Let's create another function called `drawFrequency` which will take in `frequencyData` as an argument.

Within that function, the first thing we need to do is get the frequency data into the `frequencyData` array. You can think of `frequencyData` like a holder that we will inject the data about frequency into. 

We will do that using the method `getByteFrequencyData(frequencyData);` that we can call on the analyzer. 


```
function drawFrequency(frequencyData){
  // get the frequency data into our frequencyData array
  analyzer.getByteFrequencyData(frequencyData);
  console.log(frequencyData);
}
```

We also have to run the `drawFrequency` function from within `getAudio` like so:

```
async function getAudio() {
  const stream = await navigator.mediaDevices
    .getUserMedia({ audio: true })
    .catch(handleError);
  const audioCtx = new AudioContext();
  analyzer = audioCtx.createAnalyser();
  const source = audioCtx.createMediaStreamSource(stream);
  source.connect(analyzer);
  // How much data should we collect
  analyzer.fftSize = 2 ** 8;
  // pull the data off the audio
  bufferLength = analyzer.frequencyBinCount; 
  // how many pieces of data are there?!?
  bufferLength = analyzer.frequencyBinCount;
  const timeData = new Uint8Array(bufferLength);
  const frequencyData = new Uint8Array(bufferLength);
  drawTimeData(timeData);
  drawFrequency(frequencyData);
}
```

Now we need to use `requestAnimationFrame` within the `drawFrequency` function so the function can call itself. 

```

function drawFrequency(frequencyData){
  // get the frequency data into our frequencyData array
  analyzer.getByteFrequencyData(frequencyData);
  console.log(frequencyData);
  requestAnimationFrame(() => drawFrequency(frequencyData));
}
```

Now you should see that when Wes talks, the high and low ends are starting to fill each other up. If you zoom out while focused in the console and start talking, you will see that the data is streaming in. 

![](@attachment/Clipboard_2020-06-19-12-18-16.png) 32:01

Let's take that data and paint it to the canvas. It will be a similar approach to how we visualized the time data. 

We need to figure out the bar width by figuring out what the width of the canvas is and how many data points we have. 

```
const barWidth = (WIDTH / bufferLength);
console.log(barWidth);
```

![](@attachment/Clipboard_2020-06-19-12-20-30.png) 32:50

As you can see, we get the same width as we did for the time. Let's multiply that value by 2.5 like so: `  const barWidth = (WIDTH / bufferLength) * 2.5;`. 

The reason for that is when Wes was testing this, there was a whole lot of frequency on the left hand side that we never hit. In order to get the visualization to look it's best, we are lopping off over half of it by multiply the width to be 2.5. 


Next we will make an `x` variable and set it to 0. 

`const x = 0;`

Next we will loop over all the data in the array. 

```
frequencyData.forEach(amount => { 

});
```

The frequency data comes in a range from 0 to 255. We need to figure out what height that will be. If it's 100%, we want it to go up to the center line, and if it is 0%, that would obviously be at the bottom. So we need to figure out what percent that is, how high will it go.  

We can figure that out by taking the amount of the freqency, and dividing that by 255 which will give us a percentage anywhere from 0 to 100%. 

We also figure out the bar height by taking the height of the canvas, and multiplying that by the percent. That will tell us if it is 0 percent high or 100% high. 

```
frequencyData.forEach(amount => { 
  // 0 to 255
  const percent = amount / 255;
  const barHeight = HEIGHT * percent;
});
```
 
We will modify that to just go halfway up in a second. 

Let's add a TODO next to convert the colour to HSL. For now we will just set the fill style to be red. 


```
frequencyData.forEach(amount => { 
  // 0 to 255
  const percent = amount / 255;
  const barHeight = HEIGHT * percent;
  // convert the color to HSL TODO
  ctx.fillStyle = 'red';
});
```

Then we run `ctx.fillRect`. We pass that four values, which are the x and the y of where we start, which is the x variable and we want to start at the y axis. To calculate that y axis we will take our height, and subtract the bar height from it. 

We have to do this because there is no way to tell it to anchor from the bottom. So what we need to do is tell it to anchor from the top plus the height of the bar. That will allow us to start at 100 in and 20 down.  

We also have to pass it how wide it will be and how high, like so: 

```
ctx.fillRect(
  x, 
  HEIGHT - barHeight, 
  barWidth, 
  barHeight
);
```

![](@attachment/Clipboard_2020-06-19-12-31-50.png) 36:31

Now when you refresh the page, you will see the bar, and it is going all the way to the top. That is because we need to increment the x variable by the width of the bar, so they go all the way across. 

Add the following code as the last line of the forEach: `x += barWidth`. Now you should see the data is going all the way across. 

![](@attachment/Clipboard_2020-06-19-12-34-19.png) 37:06

If you wanted to space the bars out a bit more, you could do something like `x += barWidth + 1` or `x += barWidth + 10`. 

![](@attachment/Clipboard_2020-06-19-12-35-04.png) 37:19

Now let's fix the issue where the bars are going too high. We can do that by taking the barHeight variable and dividing it's value by 2 like so: 

```
const barHeight = (HEIGHT * percent) / 2;
```

![](@attachment/Clipboard_2020-06-19-12-36-15.png) 37:48

Now you should notice that the bars don't go quite as high as they would. 

We can also set the fillStyle to use an rgba value like so:

```
    ctx.fillStyle = `rgba(255, 255, 0, 0.2)`;
    ctx.fillRect(x, HEIGHT - barHeight, barWidth, barHeight);
    x += barWidth + 2;
  });
```
![](@attachment/Clipboard_2020-06-19-12-41-22.png) 38:19  

That will cause the bars to be semi transparent and allow the time data line to show through. 

The cool thing we want to do is use HSL to figure out which color each of the bars will be. 

If you go to the website https://mothereffinghsl.com, you will see that for HSL, the hue goes from 0 to 360, and it goes through the entire rainbow. 

![](@attachment/Clipboard_2020-06-19-12-42-08.png) 38:37

What we can then do is say something that has 0 will be 0 on the HSL and something that has a 255 frequency will be 360 on the HSL spectrum. We can use that as a base to go through the entire thing. 

Let's make an array. The first value in the array will be the hue which we will calculate like so: `360 / (percent * 360)`. For the saturation and lightness, we do 0.5, 0.75 and that is it. That will affect the saturation of the color, the lower is less saturated, the higher the value the more saturated. The lightness goes between white and black. We will keep it at .75. 


```
const [h, s, l] = [360 / (percent * 360), 0.5, 0.75];
```

What is good about HSL is that it is very easy to programmatically calculate values like hue, saturation and lightness, however we cannot use HSL on canvas. 

To solve that, what Wes has done is in the `util.js` module, there is the following function: 

```
export function hslToRgb(h, s, l) {
  let r;
  let g;
  let b;

  if (s == 0) {
    r = g = b = l; // achromatic
  } else {
    const hue2rgb = function hue2rgb(p, q, t) {
      if (t < 0) t += 1;
      if (t > 1) t -= 1;
      if (t < 1 / 6) return p + (q - p) * 6 * t;
      if (t < 1 / 2) return q;
      if (t < 2 / 3) return p + (q - p) * (2 / 3 - t) * 6;
      return p;
    };

    const q = l < 0.5 ? l * (1 + s) : l + s - l * s;
    const p = 2 * l - q;
    r = hue2rgb(p, q, h + 1 / 3);
    g = hue2rgb(p, q, h);
    b = hue2rgb(p, q, h - 1 / 3);
  }

  return [Math.round(r * 255), Math.round(g * 255), Math.round(b * 255)];
}

```

What that does is it takes in the hue, saturation and lightness value and will return to you an RGB value. We can use this method to convert it. 

Let's import it into `sound.js`. 

```
import { hslToRgb } from './utils';
```

Now we can use that function to convert the HSL value like so: `const [r, g, b] = hslToRgb(h, s, l);`

Then we use those deconstructed variables to set the rgb value using back ticks like so: 

```
frequencyData.forEach((amount) => {
  // 0 to 255
  const percent = amount / 255;
  const [h, s, l] = [360 / (percent * 360), 0.5, 0.75];
  const barHeight = HEIGHT * percent * 1.2;
  // TODO: Convert the colour to HSL TODO
  const [r, g, b] = hslToRgb(h, s, l);
  ctx.fillStyle = `rgb(${r},${g},${b})`;
  ctx.fillRect(x, HEIGHT - barHeight, barWidth, barHeight);
  x += barWidth + 2;
});
```

![](@attachment/Clipboard_2020-06-19-13-02-06.png) 42:07

It is working, however the colors are a bit pastel. 

Let's fix that. Wes found that to get vibrant colors,  you can simply subtract 0.5 from the hue and it will offset where you start on the HSL spectrum which will give us a few more reds. 

```
const [h, s, l] = [360 / (percent * 360) - 0.5, 0.8, 0.5];
```

![](@attachment/Clipboard_2020-06-19-13-04-09.png) 43:04

You can feel free to play with these hue, saturation and lightness values. 

That is the very basics of visualizing data. 

One cool thing Wes wanted to point out was that the method `getByteTimeDomainData`, it gives us decible values. What would be cool is if you mapped that decibel value to HSL. 
