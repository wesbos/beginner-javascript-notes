---
attachments: [Clipboard_2020-05-27-06-59-50.png, Clipboard_2020-05-27-07-05-17.png, Clipboard_2020-05-27-07-15-19.png, Clipboard_2020-05-27-07-18-36.png, Clipboard_2020-05-27-07-19-13.png, Clipboard_2020-05-27-07-19-33.png, Clipboard_2020-05-27-07-21-39.png, Clipboard_2020-05-27-07-22-53.png, Clipboard_2020-05-27-07-23-08.png, Clipboard_2020-05-27-15-20-43.png, Clipboard_2020-05-27-16-49-29.png, Clipboard_2020-05-27-17-06-30.png, Clipboard_2020-05-27-17-18-32.png, Clipboard_2020-05-27-17-26-13.png, Clipboard_2020-05-27-19-15-20.png, Clipboard_2020-05-27-19-28-13.png, Clipboard_2020-05-27-19-38-57.png, Clipboard_2020-05-27-19-40-30.png, Clipboard_2020-05-27-19-41-43.png, Clipboard_2020-05-27-19-41-58.png, Clipboard_2020-05-27-20-04-41.png, Clipboard_2020-05-27-20-05-09.png, Clipboard_2020-05-27-20-10-27.png, Clipboard_2020-05-27-20-13-19.png]
title: Module 14 - ES Modules and Structuring Larger Apps
created: '2020-05-27T10:45:39.129Z'
modified: '2020-05-28T00:19:14.477Z'
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

Let's go back to our `modules` folder and create a new file called `currencies.js` and paste that object within but put an `export` infront of it. 

stopped at 25:20

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

```

---

## 79 -  Currency Module Refactor

---

## 80 - Currency Modules Refactor 2 

---

## 81 - Dad Jokes Modules Refactor

---

## 82 - Bundling and Building with Parcel

---

## 83 - using open source npm packages

---

## 84 - Security


