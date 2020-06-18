---
attachments: [Clipboard_2020-06-18-06-40-04.png, Clipboard_2020-06-18-06-49-00.png, Clipboard_2020-06-18-06-50-34.png, Clipboard_2020-06-18-06-52-14.png, Clipboard_2020-06-18-06-53-02.png, Clipboard_2020-06-18-07-03-08.png, Clipboard_2020-06-18-07-03-22.png, Clipboard_2020-06-18-07-05-02.png, Clipboard_2020-06-18-07-27-38.png]
title: Module 15 - Final Round of Exercises
created: '2020-06-18T10:37:29.455Z'
modified: '2020-06-18T11:27:51.638Z'
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

As you can see, that gives us an array of all the colors.

stopped at 13:37

---

## 85 - Audio Visualization

















