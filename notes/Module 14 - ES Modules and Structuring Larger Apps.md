---
attachments: [Clipboard_2020-05-27-06-59-50.png, Clipboard_2020-05-27-07-05-17.png, Clipboard_2020-05-27-07-15-19.png, Clipboard_2020-05-27-07-18-36.png, Clipboard_2020-05-27-07-19-13.png, Clipboard_2020-05-27-07-19-33.png, Clipboard_2020-05-27-07-21-39.png, Clipboard_2020-05-27-07-22-53.png, Clipboard_2020-05-27-07-23-08.png, Clipboard_2020-05-27-15-20-43.png, Clipboard_2020-05-27-16-49-29.png, Clipboard_2020-05-27-17-06-30.png, Clipboard_2020-05-27-17-18-32.png, Clipboard_2020-05-27-17-26-13.png, Clipboard_2020-05-27-19-15-20.png, Clipboard_2020-05-27-19-28-13.png, Clipboard_2020-05-27-19-38-57.png, Clipboard_2020-05-27-19-40-30.png, Clipboard_2020-05-27-19-41-43.png, Clipboard_2020-05-27-19-41-58.png, Clipboard_2020-05-27-20-04-41.png, Clipboard_2020-05-27-20-05-09.png, Clipboard_2020-05-27-20-10-27.png, Clipboard_2020-05-27-20-13-19.png, Clipboard_2020-05-28-06-29-55.png, Clipboard_2020-05-28-06-31-53.png, Clipboard_2020-05-28-06-33-44.png, Clipboard_2020-05-28-06-33-59.png, Clipboard_2020-05-28-06-34-39.png, Clipboard_2020-05-28-06-35-54.png, Clipboard_2020-05-28-06-39-12.png, Clipboard_2020-05-28-06-41-47.png, Clipboard_2020-05-28-08-09-54.png, Clipboard_2020-05-28-08-11-02.png, Clipboard_2020-05-28-08-12-26.png, Clipboard_2020-05-28-08-17-12.png, Clipboard_2020-05-28-08-18-27.png, Clipboard_2020-05-28-08-19-38.png, Clipboard_2020-05-28-08-26-55.png, Clipboard_2020-05-28-08-35-21.png, Clipboard_2020-05-28-14-52-06.png, Clipboard_2020-05-28-14-55-41.png, Clipboard_2020-05-28-17-12-41.png, Clipboard_2020-05-28-17-25-25.png, Clipboard_2020-05-28-17-27-17.png, Clipboard_2020-05-28-17-29-33.png, Clipboard_2020-05-28-17-35-43.png, Clipboard_2020-05-29-07-03-18.png, Clipboard_2020-05-29-07-16-29.png, Clipboard_2020-05-29-08-35-09.png, Clipboard_2020-05-29-08-36-19.png, Clipboard_2020-05-29-08-41-20.png, Clipboard_2020-05-29-08-43-35.png, Clipboard_2020-05-29-08-44-39.png, Clipboard_2020-05-29-19-45-28.png, Clipboard_2020-05-29-19-54-53.png, Clipboard_2020-05-29-19-56-56.png]
title: Module 14 - ES Modules and Structuring Larger Apps
created: '2020-05-27T10:45:39.129Z'
modified: '2020-05-30T00:00:13.762Z'
---

# Module 14 - ES Modules and Structuring Larger Apps


## 78 - Modules 

Let's talk about modules. 

Being able to share code across multiple javascript files and even across multiple projects is an easy thing to do when you start to use modules in Javascript.

So what are they? Modules are a way to structure and organize your Javascript, and it gives us the ability to share functionality and data across multiple files and projects. 

Here are a few things you need to know about modules:
- They have their own scope, similar to how a function has scope.
- They can hold anything (functionality, data, config)

If you recall in the previous lesson where we built a currency converter, we had a variable `currencies` that was a giant object of all the currency codes and names. 

It would be nice if instead of having that object directly in our file, we could put it in a separate module and then import it into the file to use when we need it. That is what modules will allow us to do. 

Another use case for modules is utility functions. In the Dad Jokes lesson that we finished, we had a `randomItemFromArray` method. That method is not specific to our Dad Jokes project, it's just a handy array utility. We could throw that off into a separate file that is used for utilities. 

Let's look at how modules work in the browser, and then we will look at some tooling that will help us work with them. 

You might hear modules referred to as **ESM**, **EcmaScript modules**, or **ES6 modules**. They were added to Javascript a couple of years ago, and they are the best way to organize your javavscript when you have multiple files. 

Let's go into our playground and create a folder called `modules` (it might already be there for you). 

Inside of that let's make the following files: `index.html`, `utils.j`, `handlers.js`, `scripts.js`. Now we have three different javascript files here. 

Let's say we had the following code in `scripts.js`: `const name = 'wes'`. 

In `utils.js`, lets add a simple function. 

```js
function returnHi(name){
  return `hi ${name}`;
}
```

So if we are in `scripts.js` and we want to use that `returnHi` function, can we?

Let's try. Modify the code like so. 

```
const name = 'wes';
console.log(returnHi(name)();
```

Now let's go into our `index.html` and add our base HTML if it is not already there. Let's add a script source tag and link it to `scripts.js`, and open it up in the browser.

When you do that, you should see an error that `returnHi` is not defined.  

![](@attachment/Clipboard_2020-05-27-06-59-50.png) 3:58

That makes sense becuase we have not yet put our `utils` on the page. You might think we can just add another script source tag above the one we added and link it to utils.

```
<script src="./utils.js"></script>
<script src="./scripts.js"></script>
```

![](@attachment/Clipboard_2020-05-27-07-05-17.png) 4:27

As you can see, now it works. All we had to do is put one script in front of the other one that we needed it in. This used to be the way we shared code across multiple files. 

That got out of hand pretty quickly because you had all these files that had dependencies and the order of the script tags affected the execution because they all have to load in a waterfall, which means one after the other. Each file is assuming that the other one has access to it. 

If you look at our `scripts.js` file in VS code, ESLint is complaining that `returnHi` is not defined. That is because that function does not exist within the file, so where did it come from? 

The only reason it works is because we have globally scoped the function in another file and we are just assuming that it will be available to us on the page. That is a very brittle way to write javacript. 

The solution to that is to use modules! When you need a function like `returnHi`, we can just import the function from the module, from the file that actually contains that function.

When you do that, you don't really have to worry about things loading before each other, because we will import the valuse we need before hand. 

Let's change this example to a very simple module. 

In our `index.html`, we will just have one script tag and that script tag is going to be your entry point into your Javascript. We will add the `type` attribuet on the script tag and set it to `module` like so:

```html
<scripts src="./scripts.js" type="module"></script>
```

Let's modify the code in our `scripts.js` file to contain the following:

```
const name = 'wes';
console.log('Its working...');
```

Let's refresh the HTML page and look at the console you will see a bunch of errors. 

![](@attachment/Clipboard_2020-05-27-07-15-19.png) 7:11


This first one is the CORS issue again. It is giving us trouble because you cannot use modules unless you are running it on a server. 

### Setting up Server 

We cannot use a Parcel server because Parcel also handles modules for us and Wes is trying to show us how they work without using a bundler. We just need a very simple server up and running. 

If you know how to run a server to serve us these files, feel free to skip ahead. (to 10:41)

There are a couple of different ways to do this. 

1. VSCode plugin

If you go to extensions in VS code and search for "Live Server", you should see an extension that matches it and you can click install. 

![](@attachment/Clipboard_2020-05-27-07-18-36.png) 8:13

If you go back to the modules and right click on the `index.html` and click open with Live server, and that will start it up in the browser. 

![](@attachment/Clipboard_2020-05-27-07-19-13.png) 8:26

![](@attachment/Clipboard_2020-05-27-07-19-33.png) 8:34

That will start up a localhost server. The url is `127.0.0.1:5550` which is the equivalent as localhost, it is just the IP address. You can replace it with localhost and it will work just the same `localhost:5550`. 

Now if you open up the dev tools, you will see that it is working. 

2. BrowserSync

Another way to get a server running. Open your terminal and run `npm install -g browser-sync`. 

![](@attachment/Clipboard_2020-05-27-07-21-39.png) 9:16

Then we need to do into our `modules/playground` folder within the terminal and then we just type `browser-sync` and it should start up a server. 

![](@attachment/Clipboard_2020-05-27-07-22-53.png) 8:43

If you open up the dev tools, you will see it is working but we get an error regarding `base.css`. 

![](@attachment/Clipboard_2020-05-27-07-23-08.png) 9:47

That is because we are running the server within our `/modules` folder but the base CSS file is actually at a higher level and it can't go up higher than the root. 

The solution for that is to open up `base.css`, copy all the content and then make a new file within our `/modules` directory called `base.css`. 

Now let's modify the path to that file within `index.html`. Modify it like so:

```
<link rel="stylesheet" href="./base.css">
```

Now if you refresh the page, you should no longer see that error. 

It looks like both of those ways of making a server support live reload, so if you make a change to the HTML, css or javascript files, the browser will automatically reload the page. 

It actually looks like browsersync isn't doing hot-reloading, you may need to pass additional parameters. We will just stick with the VSCode server since it is the simplest one. 

Now that we have the server runnning, lets go back to where we left off. 

How do we take a function that exists in one file and use it in another? 
You can import it from that file. 

There are two types of imports:
1. **Named Imports**
2. **Default Imports**

Before we can import something, we first need to export it. Let's go to our `utils` file and export the `returnHi` function. 

```
function returnHi(name){
  return `hi ${name}`;
}
```

When sharing code between multiple files like this, the word we use for each file is a module (so a file is a module). 

If you want to surface functionality from one file to another, you first must export it. We will export it like this for now:

```
export function returnHi(name){
  return `hi ${name}`;
}
```

Now in our `scripts.js` we are going to import the name of the function that has been exported.

We do that by using the keyword `import`, then we have curly brackets inbetween which we supply the name of the function we want to import, whcih is `returnHi` in this case and then we add the keyword "from" and the relative path to the file that contains the export, which is `utils` in our case. 


```
import { returnHi } from "./utils.js";
```

Now within `scripts.js`, we should be able to add the following code:

```
import { returnHi } from "./utils.js";

const name = 'wes';
console.log(returnHi(name));
console.log('Its working....');
```

Now if you refresh the page, you will see that it is working.

![](@attachment/Clipboard_2020-05-27-15-20-43.png) 12:30

To recap: 

What we did there is we defined some functionality in a separate file and in order for us to acccess that functionality, we must first export it from the file it is in. 

Exporting is basically saying "these things that I have exported can be used by other Javascript modules". 

Then in our `scripts.js` where we want to use that functionality, we simply import it from the file that it is in. 

Note: you always do your imports at the very top of the file that you are in, and you can have multiple imports as well. Then you simply have access to that functionality and can use it.  

### Things we need to know about Modules

#### Scope 

One thing that Wes mentioned briefly earlier is that modules have their own scope. 

What does that mean? Let's look at an example to demonstrate. 

Let's say we have the following variable within `utils.js`: `const last = 'bos';`. 

What would happen if we want to access that within the `scripts.js` file like so:

```
import { returnHi } from "./utils.js";

const name = 'wes';
console.log(returnHi(name));
console.log('Its working....');
console.log(last);
```

If you refresh the HTML page, you will see we get an error "last is not defined". That is because `last` is in a different module.

![](@attachment/Clipboard_2020-05-27-16-49-29.png) 13:38

 What if within the `returnHi` function in `utils.js` we use the `last` variable like so 👇

```
export function returnHi(name){
  return `hi ${name} ${last}`;
}
```

Is that allowed? And is it going to work? 

Let's find out. Within our `scripts.js` let's remove `console.log(last)` that we just added a few steps ago and refresh the HTML page. 

![](@attachment/Clipboard_2020-05-27-17-06-30.png) 13:52

As you can see, it is working. 

That means that you can use variables that are defined inside of a module, and they will not leak out and become available in any other file, however you can use them inside of that module, no problem. 

That is what is referred to as scoped to the module. So the `last` variable is not available in the console if we were to try, because it is not globally scoped, and it is not available in my `scripts` module. 

The `last` variable is simply scoped to the `utils` file and can only be used within that file. 

Is that good practice? Yes! 

The beauty of modules is that you don't have to worry about scoping or anything like that. 
You can just create variables inside of that file and they are only available inside of that file and nowhere else.

Now what if we _did_ want to be able to access the `last` variable inside of the `scripts` file? We could export that variable by putting the `export` keyword infront of the variable declaration. 

```
export const last = 'bos';
```

Now within `scripts.js` we can modify our `import` statement to import that variable. 

```
import { returnHi, last } from './utils.js';
```

At the bottom of `scripts.js` let's log `console.log(last)`. 

![](@attachment/Clipboard_2020-05-27-17-18-32.png) 15:07 

As you can see, that works!

Another way to export a value is instead of exporting it when you create it, you can export it from the bottom of the file like so `export { last }`. This is referred to as a named export because they have a name on them. 

Here is what the `utils.js` file looks like now:

```js
//utils.js
const last = 'bos';
export function returnHi(name){
  return `Hi ${name} ${last}`;
}
//NAMED exports
export { last }
```

Let's say we have multiple variables like `const middle = 'slam dunk'` and we wanted to export that as well we could either add an `export` to the variable declaration or we can export middle using a named export like so:

```js
//utils.js
const last = 'bos';
const middle = 'slam dunk';
export function returnHi(name){
  return `Hi ${name} ${last}`;
}
//NAMED exports
export { last, middle };
```

If you go into scripts and modify the file to import that variable and use it like so 👇

```js
//scripts.js
import { returnHi, last, middle } from './utils.js';

const name = 'wes';

console.log(returnHi(name));

console.log('Its working....');

console.log(last, middle);
```

![](@attachment/Clipboard_2020-05-27-17-26-13.png) 16:18

Which type of export should you use? That is a personal preference so use what you prefer. 

Wes often uses a combination of both. 

You can also export async functions. If `returnHi` were async, we could export it like so: 

```
export async function returnHi(name){
  return `Hi ${name} ${last}`;
}
```

As mentioned earlier, that is what is referred to as **named exports** and **named imports**.

The way you can tell if something is a named export is if it has the `export` keyword infront of the function definition or variable declaration or it is exported using curly brackets. Curly brackets means it is a named export. 

The other way to do that is a called a **default export**. 

Every module can have as many **named exports** as they want. 
However, a module can only have one **default export**, which is the default this the file exports. 

If we make another module `wes.json` and in it we will assign a variable `person` to an object, and then export that variable like so:

```
const person = {
  name: 'Wes',
  last: 'Bos'
}

export default person;
```

Then if you want to access the `person` object within `scripts.js`, we could import it like so: 

```
import { returnHi, last, middle } from './utils.js';
import wes from './wes.js';
```

Now let's log it `console.log(wes)`.  

![](@attachment/Clipboard_2020-05-27-19-15-20.png) 17:58

Now we could have named that import anything we wanted. 

For example we could have done 

```
import { returnHi, last, middle } from './utils.js';
import westernhoff from './wes.js';

console.log(westerhoff);
```

If you refresh the page, you will see it still works. 

The difference between default exports and named exports is that with named imports, you must know what the name they have been exported as, but since there is only one default export per file, you can import them and name they whatever you want. 

Which type of export should you use? There are certainly arguments on both sides. 

Wes will usually use a default export if the module does one thing, but if the module does multiple things, like a utility library or something like that, then you can just have multiple named exports from it.

You can have both named and default exports in one file. 

In `utils.js`, we will default export a variable called `first`, by adding the following code to the botto of the file 👇

```
const first = 'wes';
export default first; 
```

Now within `scripts.js`, if we wanted to import that it wouldn't go in curly brackets because that is only for named and `first` is the default. So we could import and log it like so: 

```
import first, { returnHi, last, middle } from './utils.js';
import westernhoff from './wes.js';

console.log(westerhoff);
console.log(first);
```

![](@attachment/Clipboard_2020-05-27-19-28-13.png) 19:58 

To reiterate: named are in curly brackets, default are always only one and always outside of the curly brackets.

Another thing about modules is you can rename them as you import them. 

Let's say we wanted to rename `returnHi` to `sayHi`. We could do that right in the import statement. 

```
import first, { returnHi as sayHi, last, middle } from './utils.js';
```

That will import `returnHi` and rename it to `sayHi`, kind of like destructuring but with different syntax because we use the `as` keyword. 

Now let's replace where we are calling `returnHi` and instead call `sayHi`. Let's also log `sayHi`. 


```
import first, { returnHi as sayHi, last, middle } from './utils.js';
import westernhoff from './wes.js';

console.log(westerhoff);
console.log(sayHi);
console.log(first);

const name = 'ws'; 

console.log(returnHi(name));

console.log('Its working...');

console.log(last, middle);
```

![](@attachment/Clipboard_2020-05-27-19-38-57.png) 20:39

As you can see, when we log `sayHi`, you see that we have that function there as `returnHi`. 

Let's take a quick look at the docs. Google "mdn import". 

![](@attachment/Clipboard_2020-05-27-19-40-30.png) 20:51

As you can see those are all the different types of imports. 

Sometimes you will see people importing modules by leaving the `.js` off. Let's try that. 

Remove the `.js` from the `utils` import statement like so: 

```
import first, { returnHi as sayHi, last, middle } from './utils';
```

When you refresh the page, you will see we get an error. 

![](@attachment/Clipboard_2020-05-27-19-41-58.png) 21:06

In a lot of bundlers, like Parcel,  you can leave the end `.js` off, but that isn't part of the specs, so if you are using pure HTML-browser based loading (like we are) you must include it. 

```
import defaultExport from "module-name";
import * as name from "module-name";
import { export1 } from "module-name";
import { export1 as alias1 } from "module-name";
import { export1 , export2 } from "module-name";
import { foo , bar } from "module-name/path/to/specific/un-exported/file";
import { export1 , export2 as alias2 , [...] } from "module-name";
import defaultExport, { export1 [ , [...] ] } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name";
var promise = import("module-name");
```


Let's keep going through the different ways to import.

`import * as name from 'module-name';`
You can import everything that comes in as name. 

Let's go into `wes.js` and let's add the following code:

```
const person = {
   name: 'Wes',
   last: 'Bos',
}

export default person;

export const dog = 'Snickers';
export const food = 'pizza';
export function eat(){
  console.log('chomp chomp');
}
```

By the way -- you import modules into any other modules, it's not limited to the entry point (which is `scripts.js` in our example). 

`dog`, `food` and `eat` are named exports, and if we wanted to import them into `scripts`, we could do the following:

```
import first, { returnHi as sayHi, last, middle } from './utils.js';
//import westernhoff from './wes.js';
import * as everything from './wes.js';

//console.log(westerhoff);
console.log(everything);
console.log(sayHi);
console.log(first);

const name = 'ws'; 

console.log(returnHi(name));

console.log('Its working...');

console.log(last, middle);
```

What we did is we commented our existing import of the `wes.js` module and replaced it with `import * as everything from './wes.js';`, and then in the file we log `everything`.

![](@attachment/Clipboard_2020-05-27-20-05-09.png) 23:05

If you look at the console you will see that we get this thing that kinda looks like an object but its called a module.

Inside of it we have our `default`, `dog`, `eat` and `food`.

![](@attachment/Clipboard_2020-05-27-20-10-27.png) 23:25

That is useful when you want to import absolutely everything from a module.

You can `import { export1 as alias } from 'module-name';`. 

Wes will refer to these docs often but 99% of the time he will just use the `returnHi as sayHi` and that will cover you almost all of the time.

They also have docs for export where you can see how to export different types of expressions and objects and things like that (we will be covering some in the examples we do). 

![](@attachment/Clipboard_2020-05-27-20-13-19.png) 24:16

The last thing we want to do is called an `on-demand` import. 

```
var promise = import("module-name");
```

That is handy when you want to import things nly when you need them. 

Lets say we go into the `/exercises/77 - Currency` folder and grab the big `currencies` object and copy it. 

Let's go back to our `modules` folder and create a new file called `currencies.js` and paste that object within the file. 

If we try to export it as default by putting `export default` infront of the declaration, that will not work.
```
export default const currencies = {..
```

If we want to export default a variable declaration, we must go to the bottom of the file and export it like so 👇

```
export const currencies = {
  USD: 'United States Dollar',
  AUD: 'Australian Dollar',
  BGN: 'Bulgarian Lev',
  BRL: 'Brazilian Real',
  CAD: 'Canadian Dollar',
  CHF: 'Swiss Franc',
  CNY: 'Chinese Yuan',
  CZK: 'Czech Republic Koruna',
  DKK: 'Danish Krone',
  GBP: 'British Pound Sterling',
  HKD: 'Hong Kong Dollar',
  HRK: 'Croatian Kuna',
  HUF: 'Hungarian Forint',
  IDR: 'Indonesian Rupiah',
  ILS: 'Israeli New Sheqel',
  INR: 'Indian Rupee',
  JPY: 'Japanese Yen',
  KRW: 'South Korean Won',
  MXN: 'Mexican Peso',
  MYR: 'Malaysian Ringgit',
  NOK: 'Norwegian Krone',
  NZD: 'New Zealand Dollar',
  PHP: 'Philippine Peso',
  PLN: 'Polish Zloty',
  RON: 'Romanian Leu',
  RUB: 'Russian Ruble',
  SEK: 'Swedish Krona',
  SGD: 'Singapore Dollar',
  THB: 'Thai Baht',
  TRY: 'Turkish Lira',
  ZAR: 'South African Rand',
  EUR: 'Euro',
};

export default currencies;
```

Let's say we want to click a button and get all of the currencies. One problem we might have is that it's too big of a file to load on homepage or when your scripts load. It also might not be necessary to actually load the currencies.

A popular thing to do is people will on-demand load Javascript, for example a shopping cart Javascript will only be loaded when someone hovers over a buy now button. Or a list of counties might only be loaded when someone opens the checkout. 

Loading javascript on demand ensures that your website loads nice and fast because we are not loading Javascript until we need it. 

If we want to add a button to our page that when you click it, it will load the currencies, it would work like this. 

Let's go to the html and add a button right in the body tag like so 

```
<body>
  <button>Load Currencies</button>
  <script src="./scripts.js" type="module"></scripts>
```

Now in our `scripts.js`, lets remove everything but this code to start. 

```
import first, { returnHi as sayHi, last, middle } from './utils.js';
import * as everything from './wes.js';
```

Let's start by selecting the button and listening for a click on it. 
We are going to do something different this time by putting the code we will pass to our event listener in another file. 

Normally we would just go above the event listener and make a function like `handleButtonClick` or something that we would pass to it. 

Instead, we will go into our `handlers.js` file and make a function called `handleButtonClick` which for now will just log the event, and we will export that. 

```
export function handleButtonClick(event){
  console.log(event);
}
```

Back in `scripts.js` we need to import it now. 

```
import { handleButtonClick } from './handlers.js';

const button = document.querySelector('button');
button.addEventListener('click', handleButtonClick);
```

This is normally what Wes does, have a JS file that will select his elements and hook up the event listeners, and then almost all his other utilities, data, functionality and handlers all go in separate files. 

That allows Wes to import them as he needs them and that keeps `scripts.js` which is the entry point nice and lean. He can open the file and quickly get an idea of the functionality. 

Then if he wants to know how something works, he needs to dig a bit further into the modules and read that.

If you refresh the HTML page and try clicking on the button, you will see the event logged. 

![](@attachment/Clipboard_2020-05-28-06-29-55.png) 28:47

Now we can go to `handlers.js` and work on that function. 

When the button is clicked, we want to get all the currencies. We could simply import them like so `import currencies from './currencies.js'`.  Now within the function, let's log `currencies`. 

If you do that, and refresh the page while the network tab is open, you will see all of the script modules that are being loaded.

![](@attachment/Clipboard_2020-05-28-06-31-53.png) 29:39

If you comment out that import statement and refresh the HTML page, you will see currencies is no longer in the network tab.

How do we on-demand load some data or some functionality from a module? We can make it `async`. 

```
export async function handleButtonClick(event){
  const currencies = await import('./currencies.js');
  console.log(currencies);
}
```

Now when you refresh the HTML page, you will see that currencies is no longer in the network tab until we click the button and then it is loaded.

![](@attachment/Clipboard_2020-05-28-06-33-44.png) 30:15

![](@attachment/Clipboard_2020-05-28-06-33-59.png) 30:17

That request was only made after we clicked the button.

Now we have the module logged in the console. 

![](@attachment/Clipboard_2020-05-28-06-34-39.png) 30:30

Now if we want to access the currencies we need to get the default. Let's refactor the import slightly to rename the variable. 

```
export async function handleButtonClick(event){
  const currenciesModule = await import('./currencies.js');
  console.log(currenciesModule.default);
}
```

Now when you refresh the page, you should have access to the curencies and they should be logged in the console. 

![](@attachment/Clipboard_2020-05-28-06-35-54.png) 30:53 

It does cache it, so if someone were to click the button again, the currencies would be loaded instantly instead of needing to be fetched again. 

Let's say `currencies.js` had another export, such as `export const localCurrency = 'CAD'`.  How would we also import that on demand?

If you refresh the HTML page, you will see that we do have the `localCurrency` in the `module`. 

![](@attachment/Clipboard_2020-05-28-06-39-12.png) 31:37

Let's destructure them into their own variables with curly brakcets like so:

```
const { localCurrency, default } = await import('./currencies.js');
console.log(localCurrency, default);
```

However if you try to do that, you will see the editor yelling at us that `default` is a reserved keyword, which means you cannot use it as a variable name.

So what we have to do is rename it. 

```
const { localCurrency, default: curency } = await import('./currencies.js');
console.log(localCurrency, currency);
```

![](@attachment/Clipboard_2020-05-28-06-41-47.png) 32:21

So when we are destructuring a property like `default` that is not allowed to be named `default`, we can use destructuring renaming like so `default: currency`. 

---

## 79 -  Currency Module Refactor

In this lesson let's take the currency conversion example we did and convert it into modules. 

Feel free to try this one yourself. 

Go into our `/exercises` folder and find the folder containing the currency converter we built. 

Duplicate that folder within the `/exercises` root and rename it to `79 - Currency Module Refactor`. Within that folder let's get rid of the `money-FINISHED.js` file.

Let's start by opening up the `index.html` and adding a `type="module"` on our existing script source tag.

Now `money.js` is our entry point. 

Let's take a look at what we are working with. 

```
const fromSelect = document.querySelector('[name="from_currency"]');
const fromInput = document.querySelector('[name="from_amount"]');
const toSelect = document.querySelector('[name="to_currency"]');
const toEl = document.querySelector('.to_amount');
const form = document.querySelector('.app form');
const endpoint = 'https://api.exchangeratesapi.io/latest';
const ratesByBase = {};

const currencies = {
  USD: 'United States Dollar',
  AUD: 'Australian Dollar',
  BGN: 'Bulgarian Lev',
  BRL: 'Brazilian Real',
  CAD: 'Canadian Dollar',
  CHF: 'Swiss Franc',
  CNY: 'Chinese Yuan',
  CZK: 'Czech Republic Koruna',
  DKK: 'Danish Krone',
  GBP: 'British Pound Sterling',
  HKD: 'Hong Kong Dollar',
  HRK: 'Croatian Kuna',
  HUF: 'Hungarian Forint',
  IDR: 'Indonesian Rupiah',
  ILS: 'Israeli New Sheqel',
  INR: 'Indian Rupee',
  JPY: 'Japanese Yen',
  KRW: 'South Korean Won',
  MXN: 'Mexican Peso',
  MYR: 'Malaysian Ringgit',
  NOK: 'Norwegian Krone',
  NZD: 'New Zealand Dollar',
  PHP: 'Philippine Peso',
  PLN: 'Polish Zloty',
  RON: 'Romanian Leu',
  RUB: 'Russian Ruble',
  SEK: 'Swedish Krona',
  SGD: 'Singapore Dollar',
  THB: 'Thai Baht',
  TRY: 'Turkish Lira',
  ZAR: 'South African Rand',
  EUR: 'Euro',
};

function generateOptions(options) {
  return Object.entries(options)
    .map(
      ([currencyCode, currencyName]) =>
        `<option value="${currencyCode}">${currencyCode} - ${currencyName}</option>`
    )
    .join('');
}

async function fetchRates(base = 'USD') {
  const res = await fetch(`${endpoint}?base=${base}`);
  const rates = await res.json();
  return rates;
}

async function convert(amount, from, to) {
  // first check if we even have the rates to convert from that currency
  if (!ratesByBase[from]) {
    console.log(
      `Oh no, we dont have ${from} to convert to ${to}. So gets go get it!`
    );
    const rates = await fetchRates(from);
    console.log(rates);
    // store them for next time
    ratesByBase[from] = rates;
  }
  // convert that amount that they passed it
  const rate = ratesByBase[from].rates[to];
  const convertedAmount = rate * amount;
  console.log(`${amount} ${from} is ${convertedAmount} in ${to}`);
  return convertedAmount;
}

function formatCurrency(amount, currency) {
  return Intl.NumberFormat('en-US', {
    style: 'currency',
    currency,
  }).format(amount);
}
async function handleInput(e) {
  const rawAmount = await convert(
    fromInput.value,
    fromSelect.value,
    toSelect.value
  );
  toEl.textContent = formatCurrency(rawAmount, toSelect.value);
}

const optionsHTML = generateOptions(currencies);
// populate the options elements
fromSelect.innerHTML = optionsHTML;
toSelect.innerHTML = optionsHTML;

form.addEventListener('input', handleInput);
```

We are selecting a bunch of elements, we have a `ratesByBase` and `currencies` object. 

Then we have a few functions like `generateOptions`, `fetchRates`  which needs the endpoint, we have a convert, format currency and one handler.

So we have some library functions (library functions are functions considered core to our application), some handlers, and then `generateOptions` which is a helper or utility method, and then we have some data. 

We won't use any folders for this example, Wes will show us how to do that with a flat file strucutre. 

So within our `79 - Currency Refactor` folder create a file called `currencies.js`. 

Let's take our entire `currencies` object and paste it in there. It is a big enough object that Wes would give it it's own file. 

```
//currencies.js

const currencies = {
  USD: 'United States Dollar',
  AUD: 'Australian Dollar',
  BGN: 'Bulgarian Lev',
  BRL: 'Brazilian Real',
  CAD: 'Canadian Dollar',
  CHF: 'Swiss Franc',
  CNY: 'Chinese Yuan',
  CZK: 'Czech Republic Koruna',
  DKK: 'Danish Krone',
  GBP: 'British Pound Sterling',
  HKD: 'Hong Kong Dollar',
  HRK: 'Croatian Kuna',
  HUF: 'Hungarian Forint',
  IDR: 'Indonesian Rupiah',
  ILS: 'Israeli New Sheqel',
  INR: 'Indian Rupee',
  JPY: 'Japanese Yen',
  KRW: 'South Korean Won',
  MXN: 'Mexican Peso',
  MYR: 'Malaysian Ringgit',
  NOK: 'Norwegian Krone',
  NZD: 'New Zealand Dollar',
  PHP: 'Philippine Peso',
  PLN: 'Polish Zloty',
  RON: 'Romanian Leu',
  RUB: 'Russian Ruble',
  SEK: 'Swedish Krona',
  SGD: 'Singapore Dollar',
  THB: 'Thai Baht',
  TRY: 'Turkish Lira',
  ZAR: 'South African Rand',
  EUR: 'Euro',
};

export default currencies;
```

Let's make a new file called `utils.js` and inside of that we will paste our `generateOptions` method and we will make it a named export. 

```
//utils.js
export function generateOptions(options) {
  return Object.entries(options)
    .map(
      ([currencyCode, currencyName]) =>
        `<option value="${currencyCode}">${currencyCode} - ${currencyName}</option>`
    )
    .join('');
}
```

Next we will make another file called `lib.js`. Let's move the `fetchRates` and `convert` functions to that file. 

```js
//lib.js
export async function fetchRates(base = 'USD') {
  const res = await fetch(`${endpoint}?base=${base}`);
  const rates = await res.json();
  return rates;
}

export async function convert(amount, from, to) {
  // first check if we even have the rates to convert from that currency
  if (!ratesByBase[from]) {
    console.log(
      `Oh no, we dont have ${from} to convert to ${to}. So gets go get it!`
    );
    const rates = await fetchRates(from);
    console.log(rates);
    // store them for next time
    ratesByBase[from] = rates;
  }
  // convert that amount that they passed it
  const rate = ratesByBase[from].rates[to];
  const convertedAmount = rate * amount;
  console.log(`${amount} ${from} is ${convertedAmount} in ${to}`);
  return convertedAmount;
}
```

Let's take the next function `formatCurrency` and put it in the `utils.js` file like so:

```
//utils.js
export function generateOptions(options) {
  return Object.entries(options)
    .map(
      ([currencyCode, currencyName]) =>
        `<option value="${currencyCode}">${currencyCode} - ${currencyName}</option>`
    )
    .join('');
}
export function formatCurrency(amount, currency) {
  return Intl.NumberFormat('en-US', {
    style: 'currency',
    currency,
  }).format(amount);
}
```

We have `handleInput` which is a handler so let's make a new file `handlers.js` and add that there. 

```
export sync function handleInput(e) {
  const rawAmount = await convert(
    fromInput.value,
    fromSelect.value,
    toSelect.value
  );
  toEl.textContent = formatCurrency(rawAmount, toSelect.value);
}
```

Now we are left with the following code in `money.js`.

```
//money.js
const fromSelect = document.querySelector('[name="from_currency"]');
const fromInput = document.querySelector('[name="from_amount"]');
const toSelect = document.querySelector('[name="to_currency"]');
const toEl = document.querySelector(".to_amount");
const form = document.querySelector(".app form");
const endpoint = "https://api.exchangeratesapi.io/latest";
const ratesByBase = {};

const optionsHTML = generateOptions(currencies);
// populate the options elements
fromSelect.innerHTML = optionsHTML;
toSelect.innerHTML = optionsHTML;

form.addEventListener("input", handleInput);
```

We have our options generation which we do on page load, our initialization and then our listeners. 

Let's start going one by one and decide if we are going to move the rest of the code from `money.js` or not.

Let's open up `index.html` in a VSCode live server and look to see if we have any errors in the console. 

![](@attachment/Clipboard_2020-05-28-08-09-54.png) 4:07

It is complaining that `generateOptions` is not defined. Let's import it.

```
import { generateOptions } from './utils.js';
```

Now we get an error saying `currencies` is not defined. 

![](@attachment/Clipboard_2020-05-28-08-11-02.png) 4:25

Let's import currencies so we can pass it to `generateOptions`. 

```
import { generateOptions } from './utils.js';
import { currencies } from './currencies.js'
```

If you refresh the page you will see we have yet another error. This time it is complaining that it cannot find an export named `currencies`.

![](@attachment/Clipboard_2020-05-28-08-12-26.png) 4:43

That is because it is a default export, not a named export, so it doesn't need the curly brackets. 

Modify it like so: `import currencies from './currencies.js';`

Now when we look at the console you will see it is complaining that `handleInput` is not defined. 

![](@attachment/Clipboard_2020-05-28-08-17-12.png) 4:59

Let's fix that by adding `import { handleInput } from './handlers';`

Now there are no more errors in the console but when we try to type in an amount, we see a reference error in the console complaining that `convert` is not defined, and it is happening in `handlers.js` on line 2.

![](@attachment/Clipboard_2020-05-28-08-18-27.png) 5:25

Let's fix that by importing the `convert` function into `handlers`. 

```
import { convert } from "./lib.js";
export sync function handleInput(e) {
  const rawAmount = await convert(
    fromInput.value,
    fromSelect.value,
    toSelect.value
  );
  toEl.textContent = formatCurrency(rawAmount, toSelect.value);
}
```

![](@attachment/Clipboard_2020-05-28-08-26-55.png) 5:55

Now we get another error that `fromInput` is not defined. Within `handleInput` we use the `fromInput`, `fromSelect`, `toSelect` and `toEl` variables. 

We also reference the function `formatCurrency` which we haven't imported. Let's import it to `handlers.js` like so `import { formatCurrency } from "./utils";`

We need all those elements now, and rather than pass them in as an argument to the function, let's put them in their own module. 

Create a new file called `elements.js`. 

Go into `money.js` and take all our selectors and move them to our new `elements.js` file. Let's add the export keyword infront of each.

```
//elements.js
export const fromSelect = document.querySelector('[name="from_currency"]');
export const fromInput = document.querySelector('[name="from_amount"]');
export const toSelect = document.querySelector('[name="to_currency"]');
export const toEl = document.querySelector(".to_amount");
```

![](@attachment/Clipboard_2020-05-28-08-35-21.png) 6:53 

What people will often do is instead of using `document.querySelector` for all of those, they will grab a parent element like the div with a class of `app` in the example above, and then look for the selectors inside of there. 

You would have `app.querySelector` for each of those instead which allows you to have multiple on the same page, just like we did with the slider.

The way we are doing it is fine for now. 

If you refresh the page, we have an error `fromSelect` is not defined. 

![](@attachment/Clipboard_2020-05-28-14-52-06.png) 7:11

Let's first go into `handlers` and import those elements. 

```
import { convert } from "./lib.js";
import { formatCurrency } from "./utils.js";
import { fromInput, fromSelect, toSelect, toEl } from "./elements.js";

export async function handleInput(e) {
  const rawAmount = await convert(
    fromInput.value,
    fromSelect.value,
    toSelect.value
  );
  toEl.textContent = formatCurrency(rawAmount, toSelect.value);
}
```

Now lets tackle the `fromSelect` is not defined bug in `money.js` line 11.

![](@attachment/Clipboard_2020-05-28-14-55-41.png) 7:44

As you can see, `fromSelect` and `toSelect` are also needed from `money.js` on page load. Let's go ahead and import them. 

```js
//money.js
import { generateOptions } from "./utils.js";
import currencies from "./currencies.js";
import { handleInput } from "./handlers.js";
import { fromSelect, toSelect } from "./elements.js"

const form = document.querySelector(".app form");
const endpoint = "https://api.exchangeratesapi.io/latest";
const ratesByBase = {};

const optionsHTML = generateOptions(currencies);
// populate the options elements
fromSelect.innerHTML = optionsHTML;
toSelect.innerHTML = optionsHTML;

form.addEventListener("input", handleInput);
```

Now when we refresh, we are getting an error that ratesByBase is not defined. 

![](@attachment/Clipboard_2020-05-28-17-12-41.png) 8:07

Our `endpoint` and `ratesByBase` variables need to go in our `lib.js` file. 

Let's copy those over to the lib.js file. 

```
//lib.js
const endpoint = "https://api.exchangeratesapi.io/latest";
const ratesByBase = {};

export async function fetchRates(base = "USD") {
  const res = await fetch(`${endpoint}?base=${base}`);
  const rates = await res.json();
  return rates;
}

export async function convert(amount, from, to) {
  // first check if we even have the rates to convert from that currency
  if (!ratesByBase[from]) {
    console.log(
      `Oh no, we dont have ${from} to convert to ${to}. So gets go get it!`
    );
    const rates = await fetchRates(from);
    console.log(rates);
    // store them for next time
    ratesByBase[from] = rates;
  }
  // convert that amount that they passed it
  const rate = ratesByBase[from].rates[to];
  const convertedAmount = rate * amount;
  console.log(`${amount} ${from} is ${convertedAmount} in ${to}`);
  return convertedAmount;
}
```

Now if you refresh the page, you will see that it is now working! Feel free to play around with the app to test it. 

That was simpler than Wes expected -- he thought dealing with the `ratesByBase` variable would be tricky because we are updating it. 

However, the beauty of module scope is that inside of the module, we can create the `ratesByBase` object and update it from our `convert` function. Even though we are calling the `convert` from another file, it still knows about the scope of the file (similar to how a closure works), so we can still access it without issues. 

The only gotcha about these modules is that if you are on a server, the `ratesByBase` will be shared by every request that comes in which may or may not be what you want. 

Wes has ran into an issue where Wes was storing data in one module that was being overwritten by multiple users. If that is the case, you need to get into sessions or scope it to each funciton but in our case, and most cases ,this is fine. 

We have refactored the entire app into modules, which makes it a bit more organized to work with and more modular. 

One more thing Wes wants to show us is a situation where we might take the form element and put it into a bootstrap or app init function. What does that mean?

All of this code in `money.js` runs on page load. 

```
//when the page loads, this code runs
const form = document.querySelector(".app form");

const optionsHTML = generateOptions(currencies);
// populate the options elements
fromSelect.innerHTML = optionsHTML;
toSelect.innerHTML = optionsHTML;

form.addEventListener("input", handleInput);
```

Sometimes you might want to delay the running of what happens on page load. If that is the case, what we would do is take all that logic from `money.js` and go to `lib.js` and make another function. 


```
//lib.js
export function init() {
  // when the page loads, this code runs
  const form = document.querySelector(".app form");

  const optionsHTML = generateOptions(currencies);
  // populate the options elements
  fromSelect.innerHTML = optionsHTML;
  toSelect.innerHTML = optionsHTML;

  form.addEventListener("input", handleInput);
}
```

We also need to import `fromSelect` and `toSelect`. Add the import below the other imports at the top of `libs.js` 

```
import { fromSelect, toSelect } from "./elements.js";
```

Now if you try to play with the app, nothing will happen because nothing has started. 

If we go back to `money.js`, we can now import that `init` function and start the app. 

```
import { generateOptions } from "./utils.js";
import currencies from "./currencies.js";
import { handleInput } from "./handlers.js";
import { fromSelect, toSelect } from "./elements.js";
import { init } from "./lib.js";

init();
```

If you refresh the page now, you will see the following error complaining that `generateOptions` is not defined. 

![](@attachment/Clipboard_2020-05-28-17-25-25.png) 11:42

We need to go to `lib.js` and import `generateOptions`. 

```
import { fromSelect, toSelect } from "./elements.js";
import { generateOptions } from "./utils.js";
```

Now if we refresh it is complaining about `currencies` not being defined. 

![](@attachment/Clipboard_2020-05-28-17-27-17.png) 12:17

What we can do is go to `money.js` and take all our import statements except for the `init` import and move them to `lib.js`. 

```
import { fromSelect, toSelect } from "./elements.js";
import { generateOptions } from "./utils.js";
import currencies from "./currencies.js";
import { handleInput } from "./handlers.js";
```

Wes' ESLint is complaining about the `handleInput` import. The error says "Dependency cycle detected". 

![](@attachment/Clipboard_2020-05-28-17-29-33.png) 12:39

If you look at our `handlers.js`, we are importing `convert` from there from `lib`. So both files require each other. That could cause you to end up with a situation where they require each other and it gets out of control. For our purposes, it is working, but let's fix that anyway.

Let's create one more file called `init.js` 

Let's take our `init` function and all the imports we added out of `lib.js` and put it in our `init.js` file instead. 

```
//init.js

import { fromSelect, toSelect } from "./elements.js";
import { generateOptions } from "./utils.js";
import currencies from "./currencies.js";
import { handleInput } from "./handlers.js";

export function init() {
  // when the page loads, this code runs
  const form = document.querySelector(".app form");

  const optionsHTML = generateOptions(currencies);
  // populate the options elements
  fromSelect.innerHTML = optionsHTML;
  toSelect.innerHTML = optionsHTML;

  form.addEventListener("input", handleInput);
}

```

Now in `money.js` let's modify the code to import from `init.js` instead. 

```
//money.js
import { init } from "./init.js";

init();

```

Now if you refresh the page and play with the app, you will see that it is working! 

We could go one step further and not even run the code unless someone clicks a button or hovers over it. 

To do that let's select the div with class of app within `money.js`. 

We will pass the event listener out `init` function to call, and also pass the options object to the event listener to specify we only want it to run once. 

```
import { init } from "./init.js";

const app = document.querySelector(".app");

app.addEventListener("mouseenter", init, { once: true });
```

Now when the page loads, it just says "Select a Currency" until you hover over the form, and then the code initializes and the base currency is switched out to USD.

![](@attachment/Clipboard_2020-05-28-17-35-43.png) 14:26

Now our entry point has almost nothing in it because it is in a separate file. 

Is that okay? Yes, some people like their entry point to have a little code but you could have also left all the code in `money.js` as well and it still would have worked!

---

## 80 - Dad Jokes Modules Refactor

In this lesson we will refactor our dad jokes exercise so you can see how Wes would structure that. 

Let's start by duplicating the `76 - Dad Jokes` folder within the `exercises/` directory and renaming it to `80 - Dad Jokes Modules`. 

Let's start by taking all the code in `jokes-FINISHED.js` and putting it `jokes.js` and the deleting the finished version of the file.

NOw let's convert this to modules by first putting an attribute of `type="module"` on the script tag on our HTML page. 

The second thing we need to do is run it under a server which we can do in VSCode by right clicking the file in VSCode and selecting "open with live server". 

When the server loads, the dad jokes app should be working as expected.

Let's take a look at the code within `jokes.js` and start splitting it out line by line, function by function. 

```js
//jokes.js
const jokeButton = document.querySelector('.getJoke');
const jokeButtonSpan = jokeButton.querySelector('.jokeText');
const jokeHolder = document.querySelector('.joke p');
const loader = document.querySelector('.loader');

const buttonText = [
  'Ugh.',
  '🤦🏻‍♂️',
  'omg dad.',
  'you are the worst',
  'seriously',
  'stop it.',
  'please stop',
  'that was the worst one',
];

async function fetchJoke() {
  // turn loader on
  loader.classList.remove('hidden');
  const response = await fetch('https://icanhazdadjoke.com', {
    headers: {
      Accept: 'application/json',
    },
  });
  const data = await response.json();
  // turn the loader off
  loader.classList.add('hidden');
  return data;
}

function randomItemFromArray(arr, not) {
  const item = arr[Math.floor(Math.random() * arr.length)];
  if (item === not) {
    console.log('Ahh we used that one last time, look again');
    return randomItemFromArray(arr, not);
  }
  return item;
}

async function handleClick() {
  const { joke } = await fetchJoke();
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}

jokeButton.addEventListener('click', handleClick);

```

Our entry point will be `jokes.js` because that is what we have linked on the HTML page.

In the entry point, Wes like to do his selecting and event listeners but everything else, all of the data, functionality, utilities and handlers will all be in separate files in their own modules. 

Let's keep the first 4 lines of code where we are selecting elements where it is. 

Where should we put the `buttonText` variable? Let's put it in it's own file. Sometimes people will organize their code into folders, so to demonstrate that, we will put this in a folder called `data`, which you need to create. 

Within the folder let's add a file called `buttonText.js`. 

Copy and paste the buttonText variable in that file. We will worry about importing and exporting these functions between modules later, for now we just want to get all of the different functions into their own files. 

Next is the `fetchJoke` function. That is core to what the application does so often people will make a `lib` folder for this. Let's make that folder.  
(Note: you don't have to do this, Wes personally finds it confusing when people have hundreds of folders for organization sakes. Feel free to just make files in the root directory or organize your files however you like. Wes suggests starting simple and the coming back and refactoring if you need more organization.)

Within that `lib` directory we will create a file `index.js` which will contain all of our library javascript.

Copy and cut the `fetchJoke` function into the `index.js` file.

![](@attachment/Clipboard_2020-05-29-07-03-18.png) 3:31

In Wes' VSCode, the loader variable within `fetchJokes` is underlined as red because that function needs to access the loader but we have not passed it a reference to the loader. 

Because modules have their own scope, we are no longer able to reference the `loader` variable from the `jokes.js` module.

There are two ways we can fix this. We can either select the loader within that function, or we can pass it in as a parameter. We will pass it as a parameter. 

Let's also export the function as a named function.

```
//lib/index.js
//named export, you can have lots of these
export async function fetchJoke(loader) {
  // turn loader on
  loader.classList.remove('hidden');
  const response = await fetch('https://icanhazdadjoke.com', {
    headers: {
      Accept: 'application/json',
    },
  });
  const data = await response.json();
  // turn the loader off
  loader.classList.add('hidden');
  return data;
}
```

Now we have to modify the function that calls `fetchJoke` so it can pass the loader. 

```js
//money.js
async function handleClick() {
  const { joke } = await fetchJoke(loader);
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}
```
 
Let's go back to our buttonText and do a default export. 

```
//data/buttonText.js
const buttonText = [
  "Ugh.",
  "🤦🏻‍♂️",
  "omg dad.",
  "you are the worst",
  "seriously",
  "stop it.",
  "please stop",
  "that was the worst one",
];

//default export, you can only have one. 
export default buttonText;
```

Why did we put the `buttonText` in it's own file? Because Wes thinks that is all the file is going to do, so that is the main export.

The `index.js` and `lib` folders may contain multiple functions, like you would have when building a larger app, and typically this is how Wes would organize them.

The next function is `randomItemFromArray`. That is a utility function so let's make a file called `utils.j` inside of the `lib` directory. People will often make an entire folder dedicated to utils, it doesn't matter, go with what you prefer. 

Wes likes to make a `utils.js` file and stick anything in there and then if it gets too large, we will break it up into separate functions. 

```
//lib/utils.js
//named export
export function randomItemFromArray(arr, not) {
  const item = arr[Math.floor(Math.random() * arr.length)];
  if (item === not) {
    console.log('Ahh we used that one last time, look again');
    return randomItemFromArray(arr, not);
  }
  return item;
}

```

Next up we have `handleClick`. Let's make another file in `lib` called `handlers.js`. Take the `handleClick` function out of `jokes.js` and put it there. 

```
//lib/handlers.js
//named export
async function handleClick() {
  const { joke } = await fetchJoke();
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}
```

At this stage of the refactor, the code will be pretty broken, so Wes approaches it either by going through the errors in the console, or by ESLint errors. Let's do it in the console. 

The first error we are seeing is that `handleClick` is not defined. 

![](@attachment/Clipboard_2020-05-29-07-16-29.png)

That is because we moved `handleClick` into our `handlers.js` module. If we need to access `handleClick` we need to import it. 

```
//jokes.js
import { handleClick } from "./lib/handlers.js";

const jokeButton = document.querySelector(".getJoke");
const jokeButtonSpan = jokeButton.querySelector(".jokeText");
const jokeHolder = document.querySelector(".joke p");
const loader = document.querySelector(".loader");

jokeButton.addEventListener("click", handleClick);
```

Now there seems to be no errors but when you click the button, we might get one. Let's try it. 

![](@attachment/Clipboard_2020-05-29-08-35-09.png) 7:19

We get another error logged in the console, this time `handlers.js` is complaining that `fetchJoke` is not defined.

![](@attachment/Clipboard_2020-05-29-08-36-19.png) 7:27

As you can see, we need the `fetchJoke` function within `handleClick`. So do we import `fetchJoke` in our `jokes.js` entry point or into our `handlers.js` module? The answer is you always import it where you need it, even if you have already imported it into another file.

So even if we imported `fetchJoke` in `jokes.js`  and tried to refresh the page and click the button, we would see get the error `fetchJoke` is not defined. 

Why is that? 
Even though we imported it into our entry, we still have to import it where we need it. 

There is no point of importing it into our entry file right now because we are not using it anywhere in the page. There is no sense in importing things into a file where they are not used.

You simply import it where you need it. So let's go ahead and do that in `handlers.js`. 

```
//lib/handlers.js
import { fetchJoke } from './index.js';
//named export
async function handleClick() {
  const { joke } = await fetchJoke();
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}
```

![](@attachment/Clipboard_2020-05-29-08-41-20.png) 8:54

Now we get an error that loader is not defined within `handlers.js`. 

We modified the `fetchJoke` function to accept a reference to the loader, but now we are calling it from a separate file, so how do we pass it?

Our `handleClick` now has to take an argument so we could do this...

```
//jokes.js
import { handleClick } from "./lib/handlers.js";

const jokeButton = document.querySelector(".getJoke");
const jokeButtonSpan = jokeButton.querySelector(".jokeText");
const jokeHolder = document.querySelector(".joke p");
const loader = document.querySelector(".loader");

jokeButton.addEventListener("click", () => handleClick(loader));

```


![](@attachment/Clipboard_2020-05-29-08-43-35.png) 9:32

It is still complaiing that it still not defined. That is because we have to modify our `handleClick` function to accept the `loader` reference as a parameter. 

```
//lib/handlers.js
import { fetchJoke } from './index.js';
//named export
async function handleClick(loader) {
  const { joke } = await fetchJoke();
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}
```

![](@attachment/Clipboard_2020-05-29-08-44-39.png) 9:43 

Now the loader shows up. 

Another way we could have done that is by adding `jokeButton.addEventListener('click', handleClick.bind(null, loader))` to `jokes.js`. We are passing null to `bind` because we don't care about `this`, we aren't using `this` so we don't care, and then we pass it the argument which is loader. 

We also could have done it as a regular function that will call 
handleClick. Let's use an anonymous function. 

```
jokeButton.addEventListner('click', function(){
  handleClick(loader);
});
```

Sometimes you have to pass around things like we are with the loader. We selected it in `jokes.js`, passed it to `handleClick`, and then from `handleClick` we passed it to `fetchJoke`. 

We could have also selected it right inside of `handleClick` as well, it is up to you.
 
![](@attachment/Clipboard_2020-05-29-19-45-28.png) 10:46

Now that the loader is showing up, let's move onto the error in the console complaining that `jokeHolder` is not defiend within `handlers.js`. 

We have a bit of a problem because handleClick needs the loader, the `jokeButtonSpan` and the `jokeHolder`. So do we modify `handleClick` to take two more arguments? 

Instead of doing that, let's solve the issue by creating another module that will do all of our selecting. 

Let's go into our `lib` folder and create a file called `elements.js`. 

Copy all our `querySelectors` from `jokes.js` and paste them into `elements.js`. Add an export infront of each. 


```
// elements.js

export const jokeButton = document.querySelector(".getJoke");
export const jokeButtonSpan = jokeButton.querySelector(".jokeText");
export const jokeHolder = document.querySelector(".joke p");
export const loader = document.querySelector(".loader");
```

Now we no longer have to pass the loader to lets modify the call to `handleClick` in `jokes.js`. 

Let's also import the `jokeButton`. 

```
//jokes.js
import { handleClick } from "./lib/handlers.js";
import { jokeButton } from "./lib/elements.js";

jokeButton.addEventListener("click", handleClick);
```

Now let's go to our handler and fix that file. 

WE no longer have to pass the loader to `handleClick` so let's remove that param.

Let's take the `loader`, `jokeHolder`, `jokeButtonSpan` and import them. 


```
//handlers.js
import { loader, jokeHolder, jokeButtonSpan } from "elements.js";
import { fetchJoke } from "./index.js";

export async function handleClick() {
  const { joke } = await fetchJoke();
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}

```

Now when you press the button, it will fetch a joke and display it but we get an error in the console. 

![](@attachment/Clipboard_2020-05-29-19-54-53.png) 12:31

It is complaining that `randomItemFromArray` is not defined in `handlers.js` so let's import that from our `utils.js`. 

```
// handlers.js
import { loader, jokeHolder, jokeButtonSpan } from "elements.js";
import { fetchJoke } from "./index.js";
import { randomItemFromArray } from "./utils.js";

export async function handleClick() {
  const { joke } = await fetchJoke();
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}

```

If we try it again, we get another error, this time about `buttonText` not being defined so let's import that. 

![](@attachment/Clipboard_2020-05-29-19-56-56.png) 12:53

```js
// handlers.js
import { loader, jokeHolder, jokeButtonSpan } from "elements.js";
import { fetchJoke } from "./index.js";
import { randomItemFromArray } from "./utils.js";
import buttonText from "../data/buttonText.js";

export async function handleClick() {
  const { joke } = await fetchJoke();
  jokeHolder.textContent = joke;
  jokeButtonSpan.textContent = randomItemFromArray(
    buttonText,
    jokeButtonSpan.textContent
  );
}

```

Now if you try it, it will work!

So in this lesson we choppedd up the code into separate files. 

Sometimes for beginners it may seem harder to do it this way because everything is in different files and you don't know where to look for things. 
That is where you need to get good at following the stack trace and seeing where errors go. 

It is much better for maintainability and shareability to go with this approach than having it all in one file. 


---

## 81 - Bundling and Building with Parcel

---

## 82 - using open source npm packages

---

## 83 - Security


