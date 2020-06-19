---
attachments: [Clipboard_2020-06-18-06-40-04.png, Clipboard_2020-06-18-06-49-00.png, Clipboard_2020-06-18-06-50-34.png, Clipboard_2020-06-18-06-52-14.png, Clipboard_2020-06-18-06-53-02.png, Clipboard_2020-06-18-07-03-08.png, Clipboard_2020-06-18-07-03-22.png, Clipboard_2020-06-18-07-05-02.png, Clipboard_2020-06-18-07-27-38.png, Clipboard_2020-06-18-19-19-53.png, Clipboard_2020-06-18-19-24-57.png, Clipboard_2020-06-18-19-28-57.png, Clipboard_2020-06-18-19-29-56.png, Clipboard_2020-06-18-19-31-17.png, Clipboard_2020-06-18-19-32-12.png, Clipboard_2020-06-18-19-33-33.png, Clipboard_2020-06-18-19-37-39.png, Clipboard_2020-06-18-19-38-28.png, Clipboard_2020-06-18-19-40-50.png, Clipboard_2020-06-18-19-44-55.png, Clipboard_2020-06-18-19-57-42.png, Clipboard_2020-06-18-19-58-12.png, Clipboard_2020-06-18-20-01-11.png, Clipboard_2020-06-18-20-03-05.png, Clipboard_2020-06-18-20-06-54.png, Clipboard_2020-06-18-20-08-22.png, Clipboard_2020-06-18-20-08-25.png]
title: Module 15 - Final Round of Exercises
created: '2020-06-18T10:37:29.455Z'
modified: '2020-06-19T00:08:43.616Z'
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

















