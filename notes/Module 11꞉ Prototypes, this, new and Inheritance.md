---
attachments: [Clipboard_2020-05-05-07-07-33.png, Clipboard_2020-05-05-07-08-27.png, Clipboard_2020-05-05-07-13-11.png, Clipboard_2020-05-05-07-17-20.png, Clipboard_2020-05-05-07-18-48.png, Clipboard_2020-05-05-07-21-30.png, Clipboard_2020-05-05-07-22-59.png, Clipboard_2020-05-05-07-26-24.png, Clipboard_2020-05-05-07-28-09.png, Clipboard_2020-05-05-07-30-04.png, Clipboard_2020-05-05-07-30-40.png, Clipboard_2020-05-05-07-34-51.png, Clipboard_2020-05-05-07-36-05.png, Clipboard_2020-05-05-07-38-40.png, Clipboard_2020-05-05-07-39-11.png, Clipboard_2020-05-05-20-01-34.png, Clipboard_2020-05-05-20-10-58.png, Clipboard_2020-05-05-20-17-59.png, Clipboard_2020-05-05-20-19-43.png, Clipboard_2020-05-05-20-24-17.png, Clipboard_2020-05-05-20-25-07.png, Clipboard_2020-05-05-20-29-08.png, Clipboard_2020-05-05-20-34-05.png, Clipboard_2020-05-05-20-35-44.png, Clipboard_2020-05-05-20-38-13.png, Clipboard_2020-05-06-05-23-33.png, Clipboard_2020-05-06-05-26-18.png, Clipboard_2020-05-06-05-28-24.png, Clipboard_2020-05-06-05-30-17.png, Clipboard_2020-05-06-05-33-56.png, Clipboard_2020-05-06-05-34-55.png, Clipboard_2020-05-06-05-37-07.png, Clipboard_2020-05-06-05-41-12.png, Clipboard_2020-05-06-05-42-38.png, Clipboard_2020-05-06-05-44-30.png, Clipboard_2020-05-06-05-46-09.png, Clipboard_2020-05-06-05-49-29.png, Clipboard_2020-05-06-05-50-45.png, Clipboard_2020-05-06-05-51-23.png, Clipboard_2020-05-06-05-52-37.png, Clipboard_2020-05-06-05-52-59.png, Clipboard_2020-05-06-06-02-50.png, Clipboard_2020-05-06-06-26-03.png, Clipboard_2020-05-06-06-28-15.png, Clipboard_2020-05-06-06-31-13.png, Clipboard_2020-05-06-06-32-31.png, Clipboard_2020-05-06-06-39-58.png, Clipboard_2020-05-06-06-44-42.png, Clipboard_2020-05-06-06-44-44.png, Clipboard_2020-05-06-06-47-51.png, Clipboard_2020-05-06-06-52-31.png, Clipboard_2020-05-06-06-53-11.png, Clipboard_2020-05-06-06-59-11.png, Clipboard_2020-05-06-07-02-46.png, Clipboard_2020-05-06-07-08-30.png, Clipboard_2020-05-06-19-44-56.png, Clipboard_2020-05-06-19-50-26.png, Clipboard_2020-05-06-19-52-09.png, Clipboard_2020-05-06-19-56-42.png, Clipboard_2020-05-06-19-57-19.png, Clipboard_2020-05-07-06-33-43.png, Clipboard_2020-05-07-07-02-13.png, Clipboard_2020-05-07-07-04-00.png, Clipboard_2020-05-07-07-05-10.png, Clipboard_2020-05-07-07-06-31.png, Clipboard_2020-05-07-07-08-00.png, Clipboard_2020-05-07-07-08-25.png, Clipboard_2020-05-07-07-18-33.png, Clipboard_2020-05-07-07-26-48.png, Clipboard_2020-05-07-07-29-04.png, Clipboard_2020-05-07-07-30-06.png, Clipboard_2020-05-07-07-46-18.png, Clipboard_2020-05-07-07-48-45.png, Clipboard_2020-05-07-07-55-14.png, Clipboard_2020-05-07-07-55-59.png, Clipboard_2020-05-07-07-57-22.png, Clipboard_2020-05-07-18-17-28.png, Clipboard_2020-05-07-18-19-40.png, Clipboard_2020-05-07-18-24-08.png, Clipboard_2020-05-07-18-35-47.png, Clipboard_2020-05-07-18-40-24.png, Clipboard_2020-05-07-18-43-46.png, Clipboard_2020-05-07-18-44-42.png, Clipboard_2020-05-07-18-51-42.png, Clipboard_2020-05-07-18-56-58.png, Clipboard_2020-05-07-19-02-22.png, Clipboard_2020-05-07-19-07-59.png, Clipboard_2020-05-07-19-10-48.png, Clipboard_2020-05-07-19-13-28.png, Clipboard_2020-05-07-19-15-21.png]
title: 'Module 11: Prototypes, this, new and Inheritance'
created: '2020-05-04T23:17:43.495Z'
modified: '2020-05-07T23:17:07.203Z'
---

# Module 11: Prototypes, `this`, `new` and Inheritance

## 60 - The New Keyword

This is the lesson on classes, prototypes, and then the keywords `this` and `new`.  

We are grouping these things together because they are all connected and are the foundation for what is often called **object-oriented programming** and another popular version is **functional programming**. 

Let's get started with the `new` keyword and understanding how that works. 

We will create a new file called `new-this.html` in our playground directory. 

Inside of the file we want to add our HTML base, and change the title to "New, This, Prototypes and Classes. Add a script tag within the body tag with a log of "it works" and open the HTML page to ensure it is working.

So what is the `new` keyword? We have already use it a couple of times like when we throw an error, create a date or create a new array using the new keyword. 

Let's talk about dates. Let's say we had a date that we assigned the value of AUgust 11 2025 to and logged it, you would see in the console a string of the date. 

```
const myDate = new Date('August 11, 2025');
console.log(myDate);
```

![](@attachment/Clipboard_2020-05-05-07-07-33.png) 1:54

If we did `console.dir(myDate);` instead, you will see that we have our date and inside of it we have a prototype of tons of different methods.

![](@attachment/Clipboard_2020-05-05-07-08-27.png) 2:03

Let's say you were to log `myDate.getFullYear()` you will see we get 2025 in the console. 

![](@attachment/Clipboard_2020-05-05-07-13-11.png) 2:21

Where did the `getFullYear()` method come from? The same thing when we create an array, we automatically have all these new methods like `pop`, `push`, `slice` and `splice`. Where do those all come from?

That is because when you create a date, an object, an array, a string, a number or any of those things, we are essentially creating a new object in javascript that is extendd off the constructor, or as Wes likes to refer to it as, the momma object. 

If we take a look at all of the types we have by entering them into the console, you will see that they are all just functions which once they are run with the new keyword infront of it, will return to you an object. 

![](@attachment/Clipboard_2020-05-05-07-17-20.png) 3:22

That is why we say in Javascript everything is an object. Even though a number is just a number, when we create a new number, we have all these methods that exist on it. So although the number is just a number, it is packed with all these methods for working with it. 

![](@attachment/Clipboard_2020-05-05-07-18-48.png) 3:52

Let's go back to the date example and continue.

Because we are creating an new Date, we have this variable `myDate` which is an instance of date. If you were to type into a console `typeof myDate`, it would return an object. But if you were to type `myDate instanceof Date` it would return true. 

![](@attachment/Clipboard_2020-05-05-07-21-30.png) 4:43

myDate is an object, but it is an instance of our special object that we have in the browser that is called a date.

The same thing happens with arrays. In the script tag, add `const name = ['wes','kait'];`.  If you try running `typeof` and `instanceof Array` in the console, you should see the same result -- names is an instance of an array but an object itself.

![](@attachment/Clipboard_2020-05-05-07-22-59.png) 5:30

With the array, it might be a bit confusing because you don't see the `new` keyword being used. Same thing when you create an object like `const wes = { name: 'wes'};`. 
Why are we able to use the instance if we aren't using the `new` keyword?  Because that way of making an array and objects are what are referred to as **literal syntax**. They are the same thing as doing 

```
const names = new Array('wes','kait');
const wes = new Object({name:'wes'});
```

![](@attachment/Clipboard_2020-05-05-07-26-24.png) 6:45

As you can see, the array and object look the same. The only difference is it is a shorter syntax. 

Some other things like dates don't have a literal syntax, which is why we have to put the `new` keyword infront of it. 

It's the same thing when you create an element. 

```
const span = dcument.createElement('span');
console.log(span);
```

If you tried to check whether `span` was an instance of an element you could do `span instaceof Element` which should return true because Element was the base one and span is the instance that we created.

![](@attachment/Clipboard_2020-05-05-07-28-09.png) 7:26

Why didn't we use `new Element`?  We can take a look at the span constructor by doing `span.constructor` in the console. What that will do is it gives us a single `HTML` span element. 

Let's check if these are true by entering the following into the console. 
```
span instanceof HTMLSpanElement;
span instanceof Node;
```

Both will return true. Why? Is it an element, is is a span, is it a node? We will learn more about this in classes but essentially things can start at a very basic like a node with text. Then it can go a little further and become an element, and have a tag and attributes. And then it can go even further and become a special kind of element like an image or div. In all of those cases, the element inherits the Node and the HTMLSpanElement inherits the Element. 

![](@attachment/Clipboard_2020-05-05-07-30-04.png) 8:22

That is what is referred to as **extending** which we will get into when we discuss classes.

So when using `document.createElement()` we do not need a `new` keyword because it does that under the hood. 

Let's build our own to get a better grasp on this. We will make a pizza. 

```
function Pizza(){
  console.log('Making a pizza');
}
```

What we have done is added the ability to make a new pizza. Let's create one and try it first without the `new` keyword. 

```
const pepperoniPizza = Pizza();
console.log(pepperoniPizza); 
```

If you refresh the page, you will see we get undefined. 

![](@attachment/Clipboard_2020-05-05-07-34-51.png) 10:01

That makes sense because the function did not return anything. 

Now let's add the new keyword like so `const pepperoniPizza = new Pizza()` and check the logs you will see that we get a pizza object with nothing is it because we haven't added anything to it yet. 

![](@attachment/Clipboard_2020-05-05-07-36-05.png) 10:17

What happens is when you use the `new` keyword on a function, it creates a new instance object of that function instead of whatever has been returned from that function. 

To reiterate, by using the `new` keyword in Javascript, that creates a new object, that is an instanc of whatever function you have made it from. That makes a lot more sense when we get into the `this` keyword, constructors and classes. 

We could take this a bit further and look at the constructor like so

```
console.log(pepperoniaPizza.constructor);
```

The constructor will tell us what function made it. 

![](@attachment/Clipboard_2020-05-05-07-38-40.png) 11:15

Same thing with our span. If we look at our constructor, we see that the thing that made the span was the `HTMLSpanElement` function. 

![](@attachment/Clipboard_2020-05-05-07-39-11.png) 11:34

If you were to type `pepperoniPizza instanceof Pizza` we would see true returned in the console.

---

## The `this` keyword. 

We will discuss the `this` key in this video and the next video which is about prototypes and prototypal inheritance. 

The `this` keyword in Javascript refers to the instance of an object that a function is bound. 

So what does that mean? Up to now Wes has told us that the `this` keyword is what is left of the dot when you are calling a method. 

Let's demo with some code. In our `new-this.html` file, within the body tag let's make two buttons.  

```
<button class="one">Button 1</button>
<button class="two">Button 2</button>
```

Now let's go to the bottom of the script tag and select both of the buttons. 

Next let's make a function called `tellMeAboutTheButton` that simply logs the `this` keyword. 

Then we will add an event listener to both buttons on the click event to call the function we just made. 

```
    function tellMeAboutTheButton() {
      console.log("outside", this);
    }

    button1.addEventListener("click", tellMeAboutTheButton);
    button2.addEventListener("click", tellMeAboutTheButton);
```

Now when we go and click on each button, the `this` keyword will be equal to each button that was clicked. 

![](@attachment/Clipboard_2020-05-05-20-01-34.png) 1:33

Now we can call that an instance. Why? because `button1` and `button2` are sinmply instances of the mama Button that exists in the browser. 

Whenever you make a new button, whether via HTML or it gets rendered to the DOM, or whether you use `document.createElement` it will create an new instance of the HTML button that is in the browser. 

The `this` keyword in our example is equal to the thing that is left of the dot. The method that was called was `addEventListener()` and the thing to the left of it was either `button1` or `button2` in our example. 

You will also hear that referred to as the `tellMeAboutTheButton` function being bound to the button. When something is "bound" to something, it means that the `this` keyword is going to be equal to whatever it was bound to. (You can change that with the `.bind()` method but we won't get into that here).

An important thing to know about the `this` keyword is that it is always scoped to a function. If you use an arrow function, for example if we converted `tellMeABoutTheButton` to an arrow function like so, watch what happens to `this`. 

```
const tellMeAboutTheButton = () => {
  console.log(this);
}
```

Now when you click the buttons, you will see the `Window` logged not the button. 

![](@attachment/Clipboard_2020-05-05-20-10-58.png) 3:05

The value of the `this` keyword does not change when you use an arrow function. The `this` keyword will be equal to whatever it was at a higher level function. (If there is no higher level function, it will be equal to the Window).

One use case for this is, lets say we bring tellMeAboutTheButton back to a regular function, and let's say after one second we want to update the text of the button to say something like "Good job". We can use `setTimeout()` to do that. 

The first argument of setTimeout is a callback function and the second argument is how long the timeout should be. Within the timeout we will set the textContent of the button the be equal to "You Clicked Me". 

```
const tellMeAboutTheButton = () => {
  console.log(this);
  setTimeout(function(){
    console.log(this);
    this.textContent = "You Clicked Me";
  }, 1000);
}
```

If you refresh the HTML page and try clicking on the buttons, you will see that nothing really happened. What is going on there? 

Let's log the value of `this` within the timeout, refresh the page and click the second button and then look at the console. You should see the button logged and then the window. 

![](@attachment/Clipboard_2020-05-05-20-17-59.png) 4:33

Why is that? Let's modify the logs to be a bit clearer. Replace the first log with `console.log('outside', this)` and the second one with `console.log('inside',this);`.

![](@attachment/Clipboard_2020-05-05-20-19-43.png) 4:53

As you can see, outside it is equal to the button but inside the timeout it is equal to the window. That is because everytime you create a new function, it will change what the value of `this` is equal to. 

If you need to be able to access the value of the `this` keyword within the `tellMeABoutTheButton` function, you can use an arrow function because it will know not to change. It will instead grab the value of whatever `this` is equal to within the `tellMeABoutTheButton` function. 

![](@attachment/Clipboard_2020-05-05-20-24-17.png) 5:47

```
 setTimeout(() => {
    console.log("inside", this);
    this.textContent = "You Clicked Me";
  }, 1000);
```

If you refresh the page you will see that the value of `this` remains the same now. 

![](@attachment/Clipboard_2020-05-05-20-25-07.png) 5:59

That is something about arrow functions that might come and bite you, so just know about that. 

That is what we now about the `this` keyword so far. 

The other thing we need to know about the `this` keyword is that it refers to the instance of the thing that was made. 

If we go up to the `Pizza` example further up in the file that we added in the last video, if we log `this` within the `Pizza` funciton, whenever and log `this`, whenever the pizza is made, we will have access to the pizza that was created. 

![](@attachment/Clipboard_2020-05-05-20-29-08.png) 6:48

We can do things like store information about the pizza that is being made inside of that pizza. When you make a pizza, you need to store information about it like what are the toppings, who is it for, and things like that. 

Let's go ahead and code that. 

We will modify the `Pizza()` function which is referred to as **constructor**, the function that makes an object is called a constructor. It will take in an array of toppings (default of which will be an empty array), and then it will take in a customer's name. 

Inside of the Pizza function we will save the toppings and customer like so:


```
function Pizza(toppings = [], customer) {
  console.log("Making a pizza");
  // save the toppings that were passed in, to this instance of pizza
  this.toppings = toppings;
  this.customer = customer;
}
```

You do also do other things like generate an id inside of the constructor. Let's add that. 

Wes likes to use this blog post by Tom Irish that Wes uses whenever he needs a random id to be generated. It's not guaranteed to be unique, but it is good enough for most use cases. This one gives you a random hex code. We will take the `#` sign off the method because we don't need it. 

![](@attachment/Clipboard_2020-05-05-20-34-05.png) 8:01

```
this.id = Math.floor(Math.random() * 16777215).toString(16);
```

Now when you refresh the page, you will see that in our pizza there is a bunch of information about that pizza. 

![](@attachment/Clipboard_2020-05-05-20-35-44.png) 8:33

The `toppings` and `customers` are empty and undefined because we haven't passed them in so let's update our `pepperoniPizza` to add some toppings and a customer and then add another pizza like so:


```
const pepperoniPizza = new Pizza(['pepperoni'], 'Wes Bos');
const canadianPizza = new Pizza(['pepperoni', 'mushrooms', onion'], 'Kait Bos');
```

If you refresh the page and open up the console, you will see our two pizzas with all the information we passed to the function. 

![](@attachment/Clipboard_2020-05-05-20-38-13.png) 9:40

The `this` keyword, when you are creating an object, is used to store information about that instance. This is a perfect example because pepperoniPizza is an instance of pizza, and it has it's own unique data that needs to stay with that pizza, like toppings, customer and id. The same thing goes for the canadian pizza, it is another instance with it's own information that stays with that pizza.

`this` is used for storing data and functionality on each of the instances. 

In the next video we will go into prototypal methods that can be shared amongst all the pizzas, because they always do the exact same thing. 

---

## 62 - Prototype Refactor of Gallery Exercise

In the next two videos we will refactor our gallery and slider exercises that we did earlier to take advantage of the prototype.

Open up `gallery.js` and save a copy of the file under he name `gallery-prototype.js`. Then go into your `index.html` file within the gallery exercise directory and modify the script src to point to the `gallery-prototype.js` file instead.

If you scroll to the bottom of the javascript page, you will see we have two variables `gallery1` and `gallery2`, and if we log them in the console, we will get undefined and undefined. 

```

const gallery1 =  Gallery(document.querySelector('.gallery1'));
const gallery2 =  Gallery(document.querySelector('.gallery2'));

console.log(gallery1, gallery2);
```

Why? because the `Gallery()` function doesn't actually return anything. 

![](@attachment/Clipboard_2020-05-06-05-23-33.png) 00:56

If however we change it to use the `new` keyword, it will automatically return an instance of that gallery. 

```
const gallery1 = new Gallery(document.querySelector('.gallery1'));
const gallery2 = new Gallery(document.querySelector('.gallery2'));
```

![](@attachment/Clipboard_2020-05-06-05-26-18.png) 1:06

Right now there is nothing in our Gallery nor in the prototype of it, but you will see as we add things to the prototype and to the instance, we will see them populate there. 

Let's go to the top of the file and go line by line. 
The way we are chekcing whether the parameter exists is fine, we can leave that alone. 

![](@attachment/Clipboard_2020-05-06-05-28-24.png) 1:25

The only thing we need to do is save the reference to the gallery div that was passed in because we will need it in our prototype method shortly. 

Add this line after the condition: `this.gallery = gallery;`. 

Now if you refresh the page, we should see both of our galleries logged, and you can see that those are instance properties because they differ in each one. 

![](@attachment/Clipboard_2020-05-06-05-30-17.png)  2:06

Now we need to go through all the variables we created. We just created them as variables inside of the closure, but because we are going to be moving all of the methods like `handleClickOutside` and `handleKeyUp()` will be moved to the prototype, they will no longer have access to the closure, meaning we need to surface the variables on our instance somehow. 

The way you can surface a variable on an instance is simply by saying `this.` the name of the variable. So we will change all those vairables and everywhere we have used them to `this.images` instead of `const images`. 

The easiest way that Wes has found to do that is to right click on a variable name in VSCode and select "Rename symbol" and then add `this.` next to image and remove the const, because we are not declaring a new variable, we are simply setting a property on the gallery instance. 

![](@attachment/Clipboard_2020-05-06-05-33-56.png) 2:48

![](@attachment/Clipboard_2020-05-06-05-34-55.png) 3:05

Now let's go through the rest of them.

```
this.gallery = gallery;
// select the elements we need
this.images = Array.from(gallery.querySelectorAll('img'));
this.modal = document.querySelector('.modal');
this.prevButton = this.modal.querySelector('.prev');
this.nextButton = this.modal.querySelector('.next');
```

We don't need the `let currentImage` variable anymore because wherever we set the `currentImage`, we will simply say `this.currentImage = el;` where we are setting the `currentImage` instead. So delete the let declaration of that variable. 

![](@attachment/Clipboard_2020-05-06-05-37-07.png) 3:57

As you can see, our gallery now has all these properties inside of it. 

Next we will share the rest of the functions amongst all the instances by moving them to the prototype. 

Select all these functions:

```
function openModal() {
    console.info('Opening Modal...');
    // First check if the modal is already open
    if (modal.matches('.open')) {
      console.info('Madal already open');
      return; // stop the function from running
    }
    modal.classList.add('open');

    // Event listeners to be bound when we open the modal:
    window.addEventListener('keyup', handleKeyUp);
    nextButton.addEventListener('click', showNextImage);
    prevButton.addEventListener('click', showPrevImage);
  }

  function closeModal() {
    modal.classList.remove('open');
    // TODO: add event listeners for clicks and keyboard..
    window.removeEventListener('keyup', handleKeyUp);
    nextButton.removeEventListener('click', showNextImage);
    prevButton.removeEventListener('click', showPrevImage);
  }

  function handleClickOutside(e) {
    if (e.target === e.currentTarget) {
      closeModal();
    }
  }

  function handleKeyUp(event) {
    if (event.key === 'Escape') return closeModal();
    if (event.key === 'ArrowRight') return showNextImage();
    if (event.key === 'ArrowLeft') return showPrevImage();
  }

  function showNextImage() {
    showImage(currentImage.nextElementSibling || gallery.firstElementChild);
  }
  function showPrevImage() {
    showImage(currentImage.previousElementSibling || gallery.lastElementChild);
  }

  function showImage(el) {
    if (!el) {
      console.info('no image to show');
      return;
    }
    // update the modal with this info
    console.log(el);
    modal.querySelector('img').src = el.src;
    modal.querySelector('h2').textContent = el.title;
    modal.querySelector('figure p').textContent = el.dataset.description;
    currentImage = el;
    openModal();
  }
```

Cut those functions out of the `Gallery()` function and add them right below the function. 

Now what we need to do is we need to change each of thoes functions to be on the prototype of the gallery.

We are going to remove the work `function` and we will put 

```
Gallery.prototype.openModal() {
    console.info('Opening Modal...');
    // First check if the modal is already open
    if (modal.matches('.open')) {
      console.info('Madal already open');
      return; // stop the function from running
    }
    modal.classList.add('open');

    // Event listeners to be bound when we open the modal:
    window.addEventListener('keyup', handleKeyUp);
    nextButton.addEventListener('click', showNextImage);
    prevButton.addEventListener('click', showPrevImage);
}
```

If you save an refresh, you will see that we now have access to the `openModal` function on the prototype of our galleries. Nothing will work yet but we will go through and fix them one by one. 

![](@attachment/Clipboard_2020-05-06-05-41-12.png) 5:09

Wes likes to use VSCode multi-cursor to refactor the methods all at once. His shortcuts are to hold down Click + Cmd and then put the cursor infront of every function name so you can edit them all at once. 

![](@attachment/Clipboard_2020-05-06-05-42-38.png) 5:23

```
Gallery.prototype.openModal() {
    console.info('Opening Modal...');
    // First check if the modal is already open
    if (modal.matches('.open')) {
      console.info('Madal already open');
      return; // stop the Gallery.prototype.from running
    }
    modal.classList.add('open');

    // Event listeners to be bound when we open the modal:
    window.addEventListener('keyup', handleKeyUp);
    nextButton.addEventListener('click', showNextImage);
    prevButton.addEventListener('click', showPrevImage);
  }

  Gallery.prototype.closeModal() {
    modal.classList.remove('open');
    // TODO: add event listeners for clicks and keyboard..
    window.removeEventListener('keyup', handleKeyUp);
    nextButton.removeEventListener('click', showNextImage);
    prevButton.removeEventListener('click', showPrevImage);
  }

  Gallery.prototype.handleClickOutside(e) {
    if (e.target === e.currentTarget) {
      closeModal();
    }
  }

  Gallery.prototype.handleKeyUp(event) {
    if (event.key === 'Escape') return closeModal();
    if (event.key === 'ArrowRight') return showNextImage();
    if (event.key === 'ArrowLeft') return showPrevImage();
  }

  Gallery.prototype.showNextImage() {
    showImage(currentImage.nextElementSibling || gallery.firstElementChild);
  }
  Gallery.prototype.showPrevImage() {
    showImage(currentImage.previousElementSibling || gallery.lastElementChild);
  }

  Gallery.prototype.showImage(el) {
    if (!el) {
      console.info('no image to show');
      return;
    }
    // update the modal with this info
    console.log(el);
    modal.querySelector('img').src = el.src;
    modal.querySelector('h2').textContent = el.title;
    modal.querySelector('figure p').textContent = el.dataset.description;
    currentImage = el;
    openModal();
  }
```

It won't even load now because we get these errors like `handleClickOutside is not defined`. 

![](@attachment/Clipboard_2020-05-06-05-44-30.png) 6:10

If we go to line 29, you will see we are calling `showImage(e.currentTarget)`. Anytime we reference one of our functions, it needs to be changed to `this.showImage`. That is where ESLint becomes very helfpul. If you click ESLint at the bottom, you can see all of the problems. 

![](@attachment/Clipboard_2020-05-06-05-46-09.png) 6:49

Now we can go through them one by one and change them out.

```

Gallery.prototype.openModal = function() {
  console.info('Opening Modal...');
  // First check if the modal is already open
  if (this.modal.matches('.open')) {
    console.info('Madal already open');
    return; // stop the function from running
  }
  this.modal.classList.add('open');

  // Event listeners to be bound when we open the modal:
  window.addEventListener('keyup', this.handleKeyUp);
  this.nextButton.addEventListener('click', this.showNextImage);
  this.prevButton.addEventListener('click', this.showPrevImage);
};

Gallery.prototype.closeModal = function() {
  this.modal.classList.remove('open');
  // TODO: add event listeners for clicks and keyboard..
  window.removeEventListener('keyup', this.handleKeyUp);
  this.nextButton.removeEventListener('click', this.showNextImage);
  this.prevButton.removeEventListener('click', this.showPrevImage);
};

Gallery.prototype.handleClickOutside = function(e) {
  if (e.target === e.currentTarget) {
    this.closeModal();
  }
};

Gallery.prototype.handleKeyUp = function(event) {
  if (event.key === 'Escape') return this.closeModal();
  if (event.key === 'ArrowRight') return this.showNextImage();
  if (event.key === 'ArrowLeft') return this.showPrevImage();
};

Gallery.prototype.showNextImage = function() {
  console.log('SHOWING NEXT IMAGE!!!');
  this.showImage(
    this.currentImage.nextElementSibling || this.gallery.firstElementChild
  );
};
Gallery.prototype.showPrevImage = function() {
  this.showImage(
    this.currentImage.previousElementSibling || this.gallery.lastElementChild
  );
};

Gallery.prototype.showImage = function(el) {
  if (!el) {
    console.info('no image to show');
    return;
  }
  // update the modal with this info
  console.log(el);
  this.modal.querySelector('img').src = el.src;
  this.modal.querySelector('h2').textContent = el.title;
  this.modal.querySelector('figure p').textContent = el.dataset.description;
  this.currentImage = el;
  this.openModal();
};
```

Now that we have refactored everything (all our variables and methods) to be referenceable by `this.` and their name. 

Let's go through the app and find any issues that might be. We will first find all the bugs, make a list and then fix them. 

Let's click on an image, the modal should open fine, when we click the buttons, we get an error. If you try to click outside the modal to close it, that is also broken.

If you hit escape that is also broken. 

Let's tackle those so far, starting with the next/prev buttons being broken.

The error says `cannot read property 'nextElementSibling' of undefined. 

![](@attachment/Clipboard_2020-05-06-05-49-29.png) 8:16

The line that is throwing the error is 

```
this.showImage(
  this.currentImage.nextElementSibling || this.gallery.firstElementChild
);
```

`this.currentImage` is undefined. So what is the value of the `this` we have highlighted in the image below? 

![](@attachment/Clipboard_2020-05-06-05-50-45.png) 8:37

Let's add a log and open it up. As far as we know, `this` should always equal the instance of the gallery. 

![](@attachment/Clipboard_2020-05-06-05-51-23.png) 8:54

According to the log, `this` is equal to a button within our `showImage` method. Let's find where `showNextImage()` is called from. It is being called from within the `closeModal` function to remove the event listener. It is also being called from another method to add the event listener. 

![](@attachment/Clipboard_2020-05-06-05-52-59.png) 9:19

What is happening is we are listening for a click and when the click happens, the `showNextImage` function is running. 

However, like Wes has told us about passing callbacks to `addEventListener` and the keyword `this`? Whenever you pass a callback to an event listener, the `this` keyword will be equal to whatever is to the left of the dot. 

So how do we fix that? There are a few ways which we will go over now. 

A popular way in React word would be to make it an arrow function like so 

```
this.nextButton.addEventListener('click', () => this.showNextImage);
```

Now that works, but there is a problem with that which Wes will demonstrate once we get the Escape key working.

Let's refactor this method as well using an arrow function to get that working 

```
window.addEventListener('keyup', e=> this.handleKeyUp(e));
```

Now when you open the modal up, and hit the escape key, and repeat that a few times, when you click right, it will jump a few images instead of going to the next one. What is going on there? Everytime we close the modal, it is going one further down the slideshow. 

Everytime that we open it up, we are listening for another click on it already. The way we fixed that before is we just removed the eventlistener when we closed the modal. That way we added and removed it everytime that we opened and closed the modal. 

However what happens when you do what is highlighted in the image below is that you are creating another function, and in order to remove an event listener, you have to have reference to that function. 

![](@attachment/Clipboard_2020-05-06-06-02-50.png) 12:31

The other way we can fix that is by binding it to `this` when we have access to `this` inside of the gallery. 

It will get a bit complicated but don't sweat it if you don't get it right away. It took Wes a couple of years to get it. This will make sense eventualy (like the 7th or 8th time you build something this way). This is pretty common in React world. 

So now we need to bind our methos to the instanec when we need them.  We will do that for `handleKeyUp`, `showNextImage` and `showPrevImage` because they are the ones giving us trouble. 

```
this.showNextImage = this.showNextImage.bind(this);
```

What we are doing there is we are creating an instance property of the same prototype function, but bound with `this`. 

`bind()` allows us to explicitly supply what `this` will be equal to. Because in our constructor `this` is equal to the instance, we are creating a new function that has `this` bound to it. 

That allows us to now go to our `findNextIamge` function and simply just pass `showNextImage` without using an arrow function like so: 

```
this.nextButton.addEventListener('click', this.showNextImage);
```

Now the next button should work. The previous button won't work because we haven't fixed that yet. 

The benefit of doing that over doing it right in the eventlistener call directly as shown in the example below is that when we do it like below, we lose reference to the new function that was created, which stops us from being able to remove that event listener in the future. 

You always need to hold onto your functions when you create them so you can remove them in the future. 

```
this.nextButton.addEventListener('click', this.showNextImage.bind(this));
```

Let's do the same for `showPrevImage`. 

```
this.showPrevImage = this.showPrevImage.bind(this);
```

The escape key is also working, but only because we are passing the `e` like so `window.addEventListener('keyup', e=> this.handleKeyUp(e));` Modify that line of code like so: `window.addEventListener('keyup', this.handleKeyUp);`.

Now go to where we bound `this` for `showNextImage` and `showPrevImage` and we will do the same for handleKeyUp.

```
this.handleKeyUp = this.handleKeyUp.bind(this);
```

The last one is the click outside, which is the same problem. 

```
this.handleClickOutside = this.handleClickOutside.bind(this);
```

A lot of people don't like this method of doing it because it is a bit of a pain to figure out how to bind `this` in each context, so a lot of people prefer to just have a bunch of functions. It is not as explicit as when you have a bunch of functions so if you feel that way, then it may mean that the prototype way of coding is not for you. There are lots of people who to think that way. 

Wes is showing us all the approaches because there are some developers who think prototypes are the best way to work and it will come up on interviews. 

Now everything is working beautifully. 

If you feel like a challenge, feel free to try to refactor the slider one yourself. 

--- 

## 63 - Prototypes and Prototypal Inheritance

In the last video we learned that having a function and using the `new` keyword would return an object, that is an instance of that object. 

```
function Pizza(toppings = [], customer) {
    console.log("Making a pizza");
    // save the toppings that were passed in, to this instance of pizza
    this.toppings = toppings;
    this.customer = customer;
    this.id = Math.floor(Math.random() * 16777215).toString(16);
  }
    const pepperoniPizza = new Pizza(["pepperoni"], "Wes Bos");
    const canadianPizza = new Pizza(
      ["pepperoni", "mushrooms", "onion"],
      "Kait Bos"
    );

```

In the example above, both `canadianPizza` and `pepperoniPizza` are instances of the `Pizza` function. The way that we attach properties onto that instance is by saying `this.`propertyname. 

Let's say we want to add some functionality, like the abilitiy to count the number of slices left in the pizza. We can start with every pizza having 10 slices by adding this to our `Pizza` constructor function `this.slices = 10;`.

Now if you take a look at the pizza, you will see that ther are 10 slices in that pizza. 

![](@attachment/Clipboard_2020-05-06-06-26-03.png) 1:10

Now if we needed to make a method of the pizza like `eat()`, which takes away slices one at a time, you might think you coudl do something like this..

```
this.eat = function(){
  console.log('CHOMP');
  this.slices = this.slices - 1;
}
```

Now if you refresh the page and go to the console and call `eat()` on one of the pizzas, we will see "CHOMP". If you look at how many slices there are, you would get 9. 

![](@attachment/Clipboard_2020-05-06-06-28-15.png) 1:57

If you run it again, you will see we have 8. 

Lets go ahead and modify it so we do not run out of slices. Add this condition

```
this.eat = function(){
  if(this.slices > 0){
    this.slices = this.slices - 1;
    console.log(`CHOMP you have ${this.slices} left!`);
  }
  else {
    console.log('Sorry! No slices left');
  }
```

It might also be a good idea to return the new number of slices from the function (similar to how Array.prototype.push returns the number of items in an array after we add them. You would just add `return this.slices;`). 

If you call that a bunch of times in the console, you should see that it now works. 

![](@attachment/Clipboard_2020-05-06-06-31-13.png) 2:57

That works very well, however there is a downside to this which is that we are actually creating the `eat()` function once for every single pizza that is made. 

If you compared whether `pepperoniPizza.eat` and `canadianPizza.eat` are the same function, you would get false even though they look identical. 

![](@attachment/Clipboard_2020-05-06-06-32-31.png) 3:31

What is happening there is we are duplicating the functionality of the function once from every single pizza. That functionality looks identical for every single pizza so there is no need to be generating one per instance.

It does need to maintain it's own slice count, toppings, customer etc, but the functionality to eat a piece of pizza is the asme for every single pizza that is out there. 

Instead of putting functions on every single instance, we can put them on what is referred to as the **prototype**. 

You might be thinking, what is wrong wit the code we have now? It seems to be working so far. 

The problem comes when you have 20,000 pizzas. Then you have lots of instances of the pizza, and everytime you define a new function, that takes up memory in your computer and that is what causes websites and computers to go slow in many cases. 

It would be much more efficient to have one `eat()` function that is shared amongst all our pizzas. 

Let's pause on that for a second and look at some of the built in prototypes that we have. 

We have our `names` array which we have already delcared and we will create a new array called `numbers`. 

![](@attachment/Clipboard_2020-05-06-06-39-58.png) 5:13

Both of those arrays with have methods on them like `filter` for example. Every single time you make an array, the browser does not copy and paste the functionality inside of each one. 

Instead, the method actually lives in something called a prototype, which allows each of the arrays to share that functionality. 

If you checked for the equal of the `filter` method of numbers and names, you would get true because they are the exact same function. They don't just have the same functionality, they are the same function. 

![](@attachment/Clipboard_2020-05-06-06-44-44.png) 6:39 

Take our eat function, copy it and then remove those lines of code. Go further down the file, right below our Pizza function and then modify it liek so:

```
Pizza.prototype.eat = function() {
  if (this.slices > 0) {
    this.slices = this.slices - 1;
    console.log(`CHOMP you now have ${this.slices} left!`);
  } else {
    console.log(`Sorry! No slices left!`);
  }
};
```

Now every single time we make a pizza, we won't give it that function, but it will be available on the prototype. 

Let's test that it still works by calling `canadianPizza.eat()` in the console multiple times. Then try calling `pepperoniPizza.eat()` multiple times. It looks like it is working. 

However, if you log `pepperoniPizza` and look inside, you will see  customer, id, toppings (all of which are instance properties). But there is no eat functionality. However, if you open up the prototype, you will see it there. 

![](@attachment/Clipboard_2020-05-06-06-47-51.png) 7:31

That is what is referred to as the **prototype lookup**. If you put something on the prototype, and it doesn't exist on the instance, it will look for it in the mamma.

If we did `pepperoniPizza.toppings` that would be an instance but if we did `pepperoniPizza.eat`, what would first happen is it would look inside the Pizza constructor function for a proeprty called `eat`. 

What that means is that every time an instance is made, we have access to this eat function. 

One benefit of that is you can actually change the functions andthose changes will apply to every single pizza that is there. 

8:40

Let's do one more example with just the number. 

Add the following under our `eat` function. 

```
Pizza.prototype.size = 'Large';
```

Now if we go to our pepperoniPizza and look for the size, it will tell us "Large". 

![](@attachment/Clipboard_2020-05-06-06-52-31.png) 9:14

However, if we were to go into our `Pizza` function and add `this.size = "Medium";`, we will get "Medium". 

![](@attachment/Clipboard_2020-05-06-06-53-11.png) 9:15

It first checks for a property on the instance and if it doesn't exist, it will go to the prototype and look that up. 

(Get rid of the `this.size` because we don't actually need it). 

Now if we look at our `name` array by typing `name.` in the console, you will see a long list of methods that are available to us.

If we log `String.prototype` you will also see the methods available to us every single time that we create a new string. 

![](@attachment/Clipboard_2020-05-06-06-59-11.png) 10:15

All of the methods that you see already there are what is referred to as **built in** functions, meaning they just come with the language. You can actually add your own, but warning -- you should never do this. Wes is just demoing it to show us how that works. 

```
String.prototype.toUpperCase = function() {
  return 'YELLING';
}
```

Now if we run `name.toUpperCase()` in the console, it will return to us 'YELLING'. 

![](@attachment/Clipboard_2020-05-06-07-02-46.png) 11:56

That is because we overwrote the existing `toUpperCase` functionality on the prototype. 

Now when any string calls `toUpperCase()` that will run instead. You can see why it would be a bad idea to modify a built in, because on person might expect the method to do something one way, and then if you have changed something, the libaries on the page that are expecting toUpperCase to work will break. You should never modify built in for this reason. 

If you should never modify built-in functions, then why is that allowed? 

For new functionality that is added to the browser, like `Array.includes()`, might be missing from some older browsers. For those browsers, you can use something called a **polyfill**, which recreates the missing functionality. When the browser doesn't include it natively, you can **pollyfill** it by recreating the functionality in vanilla JS. 

You can also add your own methods. Again don't do this, but it's possible. 

Let's add this to our code right before our `Pizza` function constructor. 

```
String.prototype.sarcastic = function(){
  console.log(this);
}
```

Now if we refresh the page and open the console, let's try using that function. 

![](@attachment/Clipboard_2020-05-06-07-08-30.png) 15:16

As you can see, it logged `this` which is a string of "wes". 

What we can do is build out our sarcastic method similar to how we did in a previous example. 

```
String.prototype.sarcastic = function() {
  const sarcsatic = this.split('').map((char, i) => {
    if(i%2){
      return char.toUpperCase();
    }
    else {
      return char.toLowerCase();
    }
  }).join('');
  return sarcastic;
}
```

If it's an even character, we uppercase the letter, if it's an odd character, we lowercase the character. Then we join the text together and return it. 

Let's test if it works in the console. If you create a variable with a string and then call `.sarcastic()` on it, it will return the name with mixed case. 

![](@attachment/Clipboard_2020-05-06-19-44-56.png) 16:29

By adding a method to the prototype, it is then available on every instance of. Whether that is something that is built in, like a string, or something your own like pizza, you can add methods to the prototype of the pizza and every single one will get it. 

Let's do one more example. Let's make a description method. When someone calls `pizza.subscribe()`, I want it to tell you that this pizza is for the customer name with the toppings and there are x slices left. 

Feel free to pause the lesson here and try this exercise on your own. 

Here is how we would approach that. You would create the `describe()` function on `Pizza.prototype`. 

Within that we will simply return a string and use interpolations like so

```
Pizza.prototype.describe = function(){
  return `This pizza is for ${this.customer} with the toppings ${this.toppings.join(',')} and there are {this.slices} left.`;
}
```

Refresh the page and now in the console run `canadianPizza.describe()`. You should see the following 👇

![](@attachment/Clipboard_2020-05-06-19-50-26.png) 18:47

Now if you run `canadianPizza.eat()` a few times in the console and then call describe, you should see that you now have less slices left. 

![](@attachment/Clipboard_2020-05-06-19-52-09.png) 18:58

---

## 64 - Prototype Refactor of the Slider Exercise

This lesson is a bit easier because there is no removing of events so there is no binding that we need to deal with. 

Let's open up the slider exercise directory and open up the `index.js`. Let's take a copy of and call it `index-prototype.js` and then go to the `index.html` and modify the script's source tag to point to `index-prototype.js` and then navigate into that directory in the terminal and run `npm start` within the actual terminal window (not the console). 

Open the server up on your localhost and run the slider to make sure that it still works.

We have the sliders that we grabbed at the bottom. We will log them, like we did in the previous lesson. 

![](@attachment/Clipboard_2020-05-06-19-56-42.png) 1:05

You should the following in the console 

![](@attachment/Clipboard_2020-05-06-19-57-19.png) 1:18

Now we will do the same thing we did last time -- add a new keyword infront of it. That will create a new instance of the slider for each instance that we have. 

```
const mySlider = new Slider(document.querySelector(".slider"));
const dogSlider = new Slider(document.querySelector(".dog-slider"));

console.log(mySlider, dogSlider);
```

![](@attachment/Clipboard_2020-05-07-06-33-43.png) 1:31

As you can see we have our sliders now, and they each have the prototypes, and there is nothing in them yet. 

Let's start refactoring from the top of the file now. 

Here is what we are starting with:

```
function Slider(slider) {
  if (!(slider instanceof Element)) {
    throw new Error('No slider passed in');
  }
  // create some variables for working iwth the slider
  let prev;
  let current;
  let next;
  // select the elements needed for the slider
  const slides = slider.querySelector('.slides');
  const prevButton = slider.querySelector('.goToPrev');
  const nextButton = slider.querySelector('.goToNext');

  function startSlider() {
    current = slider.querySelector('.current') || slides.firstElementChild;
    prev = current.previousElementSibling || slides.lastElementChild;
    next = current.nextElementSibling || slides.firstElementChild;
    console.log({ current, prev, next });
  }

  function applyClasses() {
    current.classList.add('current');
    prev.classList.add('prev');
    next.classList.add('next');
  }

  function move(direction) {
    // first strip all the classes off the current slides
    const classesToRemove = ['prev', 'current', 'next'];
    prev.classList.remove(...classesToRemove);
    current.classList.remove(...classesToRemove);
    next.classList.remove(...classesToRemove);
    if (direction === 'back') {
      // make an new array of the new values, and destructure them over and into the prev, current and next variables
      [prev, current, next] = [
        // get the prev slide, if there is none, get the last slide from the entire slider for wrapping
        prev.previousElementSibling || slides.lastElementChild,
        prev,
        current,
      ];
    } else {
      [prev, current, next] = [
        current,
        next,
        // get the next slide, or if it's at the end, loop around and grab the first slide
        next.nextElementSibling || slides.firstElementChild,
      ];
    }

    applyClasses();
  }

  // when this slider is created, run the start slider function
  startSlider();
  applyClasses();

  // Event listeners
  prevButton.addEventListener('click', () => move('back'));
  nextButton.addEventListener('click', move);
}

const mySlider = Slider(document.querySelector('.slider'));
const dogSlider = Slider(document.querySelector('.dog-slider'));function Slider(slider) {
  if (!(slider instanceof Element)) {
    throw new Error('No slider passed in');
  }
  // create some variables for working iwth the slider
  let prev;
  let current;
  let next;
  // select the elements needed for the slider
  const slides = slider.querySelector('.slides');
  const prevButton = slider.querySelector('.goToPrev');
  const nextButton = slider.querySelector('.goToNext');

  function startSlider() {
    current = slider.querySelector('.current') || slides.firstElementChild;
    prev = current.previousElementSibling || slides.lastElementChild;
    next = current.nextElementSibling || slides.firstElementChild;
    console.log({ current, prev, next });
  }

  function applyClasses() {
    current.classList.add('current');
    prev.classList.add('prev');
    next.classList.add('next');
  }

  function move(direction) {
    // first strip all the classes off the current slides
    const classesToRemove = ['prev', 'current', 'next'];
    prev.classList.remove(...classesToRemove);
    current.classList.remove(...classesToRemove);
    next.classList.remove(...classesToRemove);
    if (direction === 'back') {
      // make an new array of the new values, and destructure them over and into the prev, current and next variables
      [prev, current, next] = [
        // get the prev slide, if there is none, get the last slide from the entire slider for wrapping
        prev.previousElementSibling || slides.lastElementChild,
        prev,
        current,
      ];
    } else {
      [prev, current, next] = [
        current,
        next,
        // get the next slide, or if it's at the end, loop around and grab the first slide
        next.nextElementSibling || slides.firstElementChild,
      ];
    }

    applyClasses();
  }

  // when this slider is created, run the start slider function
  startSlider();
  applyClasses();

  // Event listeners
  prevButton.addEventListener('click', () => move('back'));
  nextButton.addEventListener('click', move);
}

const mySlider = Slider(document.querySelector('.slider'));
const dogSlider = Slider(document.querySelector('.dog-slider'));
```

The condition that checks whether the parameter is an element or not is fine, we do not have to refactor that. 

The let variable declarations that come next need to be renamed to be `this.` the variable name. 

```
let prev;
let current;
let next;
```

Rename the variable and everywhere in the code that it is used. 

```
this.prev;
this.current;
this.next;
```

Now that we have done that, we actually do not need those declarations because there is no sense in making those variables when they are properties because properties can be added at any time. We were only declaring those variables so we had a closure where those variables were available. 

You can go ahead and delete those three variable declarations (but keep the references to them that you renamed elsewhere!)

```
// select the elements needed for the slider
const slides = slider.querySelector(".slides");
const prevButton = slider.querySelector(".goToPrev");
const nextButton = slider.querySelector(".goToNext");
```

The next three declarations you see above also need to be `this.`. Let's go ahead and rename those and everywhere they are being referenced. The prevButton however is only accessible inside of the constuctor when we add the event listener. They are not needed anywhere inside of the prototype method, so it's not necessary to put it on `this`. So `prevButton` and `nextButton` can stay variables but we will just rename `slides` like so:


```
// select the elements needed for the slider
this.slides = slider.querySelector(".slides");
const prevButton = slider.querySelector(".goToPrev");
const nextButton = slider.querySelector(".goToNext");
```

Now we will move all of the methods out of the `Slider()` constructor. Grab everything from the `startSlider` function all the way to where we have our event listeners and the call to startSlider and applyClasses. 

Your file should look like the following now: 

```
function Slider(slider) {
  if (!(slider instanceof Element)) {
    throw new Error("No slider passed in");
  }
  // create some variables for working iwth the slider
  let prev;
  let current;
  let next;
  // select the elements needed for the slider
  const slides = slider.querySelector(".slides");
  const prevButton = slider.querySelector(".goToPrev");
  const nextButton = slider.querySelector(".goToNext");

  // when this slider is created, run the start slider function
  startSlider();
  applyClasses();

  // Event listeners
  prevButton.addEventListener("click", () => move("back"));
  nextButton.addEventListener("click", move);
}

function startSlider() {
  current = slider.querySelector(".current") || slides.firstElementChild;
  prev = current.previousElementSibling || slides.lastElementChild;
  next = current.nextElementSibling || slides.firstElementChild;
  console.log({ current, prev, next });
}

function applyClasses() {
  current.classList.add("current");
  prev.classList.add("prev");
  next.classList.add("next");
}

function move(direction) {
  // first strip all the classes off the current slides
  const classesToRemove = ["prev", "current", "next"];
  prev.classList.remove(...classesToRemove);
  current.classList.remove(...classesToRemove);
  next.classList.remove(...classesToRemove);
  if (direction === "back") {
    // make an new array of the new values, and destructure them over and into the prev, current and next variables
    [prev, current, next] = [
      // get the prev slide, if there is none, get the last slide from the entire slider for wrapping
      prev.previousElementSibling || slides.lastElementChild,
      prev,
      current,
    ];
  } else {
    [prev, current, next] = [
      current,
      next,
      // get the next slide, or if it's at the end, loop around and grab the first slide
      next.nextElementSibling || slides.firstElementChild,
    ];
  }

  applyClasses();
}

const mySlider = new Slider(document.querySelector(".slider"));
const dogSlider = new Slider(document.querySelector(".dog-slider"));
console.log(mySlider, dogSlider);
```

Now we need to grab every function that we just moved out of the constructor and refactor it to live on the prototype. 

```

function Slider(slider) {
  if (!(slider instanceof Element)) {
    throw new Error("No slider passed in");
  }
  // create some variables for working iwth the slider
  this.prev;
  this.current;
  this.next;
  // select the elements needed for the slider
  this.slides = slider.querySelector(".slides");
  const prevButton = slider.querySelector(".goToPrev");
  const nextButton = slider.querySelector(".goToNext");

  // when this slider is created, run the start slider function
  this.startSlider();
  this.applyClasses();

  // Event listeners
  prevButton.addEventListener("click", () => this.move("back"));
  nextButton.addEventListener("click", this.move);
}

Slider.prototype.startSlider = function() {
  this.current =
    this.slider.querySelector(".current") || this.slides.firstElementChild;
  this.prev =
    this.current.previousElementSibling || this.slides.lastElementChild;
  this.next = this.current.nextElementSibling || this.slides.firstElementChild;
};

Slider.prototype.applyClasses = function() {
  this.current.classList.add("current");
  this.prev.classList.add("prev");
  this.next.classList.add("next");
};

Slider.prototype.move = function(direction) {
  // first strip all the classes off the current slides
  const classesToRemove = ["prev", "current", "next"];
  this.prev.classList.remove(...classesToRemove);
  this.current.classList.remove(...classesToRemove);
  this.next.classList.remove(...classesToRemove);
  if (direction === "back") {
    // make an new array of the new values, and destructure them over and into the prev, current and next variables
    [this.prev, this.current, this.next] = [
      // get the prev slide, if there is none, get the last slide from the entire slider for wrapping
      this.prev.previousElementSibling || this.slides.lastElementChild,
      this.prev,
      this.current,
    ];
  } else {
    [this.prev, this.current, this.next] = [
      this.current,
      this.next,
      // get the next slide, or if it's at the end, loop around and grab the first slide
      this.next.nextElementSibling || this.slides.firstElementChild,
    ];
  }

  this.applyClasses();
};


```

Now let's go ahead and fix the errors showing up in the text editor. 

The call to `startSlider` and `applyClasses` need to be chagned to `this.startSlider()` and `this.applyClasses()`. Same thing for the calls to the `move` function, they need to be `this.move`. 


```
// when this slider is created, run the start slider function
this.startSlider();
this.applyClasses();

// Event listeners
prevButton.addEventListener("click", () => this.move("back"));
nextButton.addEventListener("click", this.move);
```

Within `move` functino we need to change it to call `this.applyClasses()`.

Now let's go to our browser to refresh and see what errors we are getting. 


![](@attachment/Clipboard_2020-05-07-07-02-13.png) 4:41

The first one we see is `Cannot read property 'querySelector' of undefined`. The stack trace tells us it happened on line 63, however that is not helpful because that is the end of our file. Further down the stacktrace it mentions line 41 so let's check that, however that line is just a comment! So let's click on the error to see where it takes us. 

![](@attachment/Clipboard_2020-05-07-07-04-00.png) 5:14

Unfortunately that is not very helpful either. Sometimes you get these errors and it's hard to find where the error is even when the browser tries to give you a stack trace.

Let's just try to debug this ourselves. Let's look at everywhere that we are using querySelector.

![](@attachment/Clipboard_2020-05-07-07-05-10.png) 5:40

Those first three should be fine since we are passing in the slider. Where else are we using querySelector? Within our `startSlider` function and where we intialize the slider instances. 


![](@attachment/Clipboard_2020-05-07-07-06-31.png) 6:01

Wes thinks it might be the latter, which he will test by logging the slider parameter within the `Slider()`. We can tell it's not an issue with that because we can see the slider being logged to the console. 

It seems like the issue must be in our `startSlider` function when we try to access `this.slider`. 

![](@attachment/Clipboard_2020-05-07-07-08-25.png) 6:22

Let's throw a debugger in the first line of the `startSlider` function. 

Now when you refresh the page, the debugger should pause the execution of the code. If we look at the debug dev tools, we can see that at this point in time, the Slider is missing properties it needs, such as `this.slider`. 

Whenever the `startSlider()` function is running, `this.slider` does not yet exist. 

The reason for this is we never saved a reference to the slider that was passed in, so let's go ahead and do that. 

```
// select the elements needed for the slider
this.slides = slider.querySelector(".slides");
this.slider = slider;
```

Now if you refresh thae page you should no longer see that problem in the console. 

>index-prototype.js:41 Uncaught TypeError: Cannot read property 'classList' of undefined
>    at HTMLButtonElement.Slider.move (index-prototype.js:38)

On line 38 we are calling `this.prev.classList.remove(...classesToRemove);`. It is trying to tell us that `this.prev` is not defined. 

If we log what `this` is within our `move` function, we will see that it's the next button which is not working. The previous button actually works.

So let's go to where we have listened to our move. 

![](@attachment/Clipboard_2020-05-07-07-18-33.png) 8:22

The reason next is broken but previous is ot is that in next, we just pass a reference to that function, and it's being rebound. In the `prevButton` case, we are passing it an anonymous arrow function. 

We can solve this issue one of two ways. 

We can bind it with `this` and that will work. 

```
nextButton.addEventListener('click', this.move.bind(this));
```

The reason we are allowed to do that here is because we aren't removing the event listener so we dont need access to the new `this` that was bound. 

The other thing we can do is refactor it to an arrow function like so:

```
nextButton.addEventListener('click', () => this.move());
```

You can also do it as shown below.

```
// Event listeners
this.move = this.move.bind(this);
prevButton.addEventListener('click', () => this.move('back'));
nextButton.addEventListener('click', () => this.move());
```

We will stick to the arrow function in this case. The arrow function will have bound and not the `this.move` which is what we want, because `this.move` needs access to the instance in order to reference the previous, next and current dom elements.

The slider should be working well now if you refresh the page!

Now that we are done, let's just go over a few things. 

![](@attachment/Clipboard_2020-05-07-07-26-48.png) 10:09

Why did we not rename the buttons to live on `this` like `this.prevButton = slider.querySelector('.goToPrev');`?

It is because we do not need them anywhere outside of the constructor. If that is the case, keep them as regular variables and reference them when you need them inside of the function. 

One cool thing about this is if you take our `dogSlider`, we cannot access it in the console using Parcel. If we want to access it, we have to say something like 
`window.dogSlider = dogSlider` and then we have access to `dogSlider` in the console. 

The cool thing about that is now you can call the functions yourself like the move in the terminal to control the slider. 

![](@attachment/Clipboard_2020-05-07-07-29-04.png) 10:55

What we could do is at the bottom of the page add an event listener on the window's keyup event like below: 

![](@attachment/Clipboard_2020-05-07-07-30-06.png) 11:43

Now if you use your arrow keys you will see that it works. That is what is great about this, you can build something like this slider and then surface the functionality via methods and then let other people hook into your slider functionality and extend it with their own. 

---
## 65 -  bind, call and apply

This lesson will focus on the `bind`, `call` and `apply` functions, where are all used to change the scope of what `this` is equal to inside of a function or a method. 

Wes does not use these very often, but they are common interview questions so we will go over them so you have an understanding of how it works. 

Go into our `playground/` directory and add a file called `bind-call-apply.html`. We will get our HTML base going and then add a script tag within the body tag. 

We will start with a simple example of an object that has a method on it. We will create a person object on it with property of `name` and `sayHi`. The name can be your name, and `sayHi` will equal a function that logs Hey! with the person's name. 

```
const person = {
  name: 'Wes Bos',
  sayHi: function(){
    return 'hey ${this.name}';
  }
};
```

Let's change it shorthand, which is the exact same thing as above just shorter syntax for the `sayHi` property. 

```
const person = {
  name: 'Wes Bos',
  sayHi(){
    return 'hey ${this.name}';
  }
};
``` 

Let's open that in the browser and take a look at that in our console. 

![](@attachment/Clipboard_2020-05-07-07-46-18.png) 2:12

As you can see, it says "hey wes bos". Why is that? That is because `sayHi` is a method, and when a method is called, the way they get the `this` value is they look to the left of the dot to see what they are bound against.

The `sayHi` method will give us the object it was run against. This is no different than if we were to have  class or prototype. The `this` is going to be equal to whatever was to the left of the dot. 

Now if we were to take the `sayHi` method and put it in it's own variable, like so:

```
const sayHi = person1.sayHi;
```

When you run that, we will just see "hey " with no name.

![](@attachment/Clipboard_2020-05-07-07-48-45.png) 3:13

You can see if we call the `sayHi()` on the person object, we get the hey message returned with a name. But when we just call `sayHi()`, `this` is equal to the window because there is nothing that the method was bound to on the left hand side.

That is important. In Javascript, the `this` keyword is always defined by where the function is being called, and not where the function is being defined. 

So although we defined the `sayHi` function inside of an object, it's not bound to it unless we call it as a method of an object. 

We can use the `bind` keyword to change where the `this` keyword is equal to or what is it bound to.

Let's try that by binding the `sayHi` method back to the original person. 

```
const sayHi = person1.sayHi.bind(person);
```

This code tells Javascript to call a function `sayHi` and when it's called, it's `this` keyword is equal to whatever we pass to the `bind()` method. 

Now when you refresh the page, if you were to run `sayHi()`, you will see that it now says "hey wes bos" instead of just "hey".

That is because we have changed what `this` will be equal to by binding it to another object.

Why would that be useful? Somtimes you want to use a method of an object with some other information. Let's say we have a Jenna object that we crete like so:

```
const jenna = { name: 'Jenna'};
```

How would we use the `sayHi` method for this other object when `name` isn't being passed in as an argument?

![](@attachment/Clipboard_2020-05-07-07-55-14.png) 5:25

That is the difference between object oriented programming and functional programming. 

![](@attachment/Clipboard_2020-05-07-07-55-59.png) 5:35

Our `sayHi` method is object oriented. If it were to take an argument, that would be much more of a functional approach.

So if we are in this use case, what we can do is we can bind it to Jenna object like so:

```
const sayHi = person.sayHi.bind(jenna);
```

![](@attachment/Clipboard_2020-05-07-07-57-22.png) 5:57

`bind` is a method that lives on all functions and it says change the `this` keyword to be equal to, in this example, a different object.

You cuold also manually pass in a name like so:

```
const sayHi = person.sayHi.bind({name:'Harry'});
```

If you refresh the page and call `sayHi()` you will see "hey Harry" returned. 

Let's look at another example. 

stopped at 6:19

`doccument.querySelector` and `document.querySelectorAll` are kind of hard to type. Let's do an example using that. 

Let's say we wanted to make `$` a short hand for `document.querySelector` and $$ for `document.querySelectorAll`. You might think you could do something like this:

```
//QS Example

const $ = document.querySelector();
```

Now if you refresh the page, open the dev tools console and type `$` you will see that it is the querySelector function. If you try typing in `document.querySelector` it will be the exact same thing. In fact, they are identical. 

![](@attachment/Clipboard_2020-05-07-18-17-28.png) 7:01

Aside: sometiems you see that "[native code]" in the console. That means that is a function that has been implemented by the browser so we are not able to see how it works under the hood because it's implemented in whatever language it's written in. 

Now if you wanted to actually select something, you might think you would be able to just do `$('p')`. However, if you try that you will see that we get an error "Illegal invocation". 

![](@attachment/Clipboard_2020-05-07-18-19-40.png) 7:41

What is happening here? Somewhere under the hood in `document.querySelector` it needs to know where to look for the thing that you are selecting. 

Let's demonstrate the reason for that with an example. 

```
<div class="wrapper">
  <p>Hey im in a wrapper</p>
</div>
```

Now let's say we grabbed the wrapper and did the following:

```
const wrapper = document.querySelector('wrapper');
const p = wrapper.querySelector('p');
console.log(p);
```

![](@attachment/Clipboard_2020-05-07-18-24-08.png) 8:32

As you can see, that works. We got it. 

`querySelector` is a function and it needs to know what to look inside of for the selector. The reason it knows where to scope it to, either globally (the document) or in a subset of the DOM, which is the wrapper in our example, then it knows to look inside of the wrapper because it will look at what is left of the dot. 

 So when we try to log `$('p')`, it doesn't work because there is nothing to the left of the dot. We have taken away the object that it was called against and as a result it is not bound to anything. 

 The way that we can fix that is we can call `bind()` on it and manually pass it reference to the thing we want it to be equal to. 

 ```
 //by calling bind against querySelector, we say that when the $ funciton is run, use `document` as the `this` value. 
 const $ = document.querySelector.bind(document);
 ```

 Now if you try doing `console.log($('p'))`, you will see that it works now because it has been bound to the function. 


This piece of code, `document.querySelector.bind(document);` does not run the function, it return the function which you can then store in a variable, which in our example is `$`, `

You could also do that with `querySelectorAll`, like so:

```
const lookFor = document.querySelectorAll.bind(document);
console.log(lookFor('p'));
```

You would see that a NodeList is returned to us. 

![](@attachment/Clipboard_2020-05-07-18-35-47.png) 10:28

To reiterate: using `bind` will change the context of what `this` is eqaul to inside of a function or a method. 

`bind` is also useful to prep a function that has arguments sort of "pre-loaded". 

Let's demonstrate with an example. 

```
const bill = {
  total: 1000,
  calculate: function(taxRate){
    return this.total + (this.total * taxRate); 
  }
}

const total = bill.calculate(0.13);
console.log(total);
```

Let's refresh the page to check if it works. You should see 1130 in the console. 

![](@attachment/Clipboard_2020-05-07-18-40-24.png) 11:40

If you wanted to take that function and store it in an external variable, you could do

```
const calc = bill.calculate;
```

If you tried to call `calc` and pass it 0.13, you would see NAN in the console. 

```
console.log(calc(0.13));
```

![](@attachment/Clipboard_2020-05-07-18-43-46.png) 11:53 

Why? Because if we were to log `this` inside of the `calculate` method on our `bill` object, you would see that it is equal to the window.   

![](@attachment/Clipboard_2020-05-07-18-44-42.png) 12:01

The first time around it is equal to our bill object and the second time it was called it was equal to the window.

That is because `calc` is not bound to anything. We cuold just bind it to the original `bill` and that would work: 

```
const calc = bill.calculate.bind(bill);
```

You could also pass it it's own bill like so: 


```
const calc = bill.calculate.bind({total:500});
console.log(calc(0.13));
```

In the next example we will demonstrate how `bind` can be used to "pre-load" functions with some arguments that need to be called. 

Wes likes to think of this as the "check-in online" of functions. What that means is when you bind something, you can pass it additional arguments that line up with the arguments of the function or method. 

So if we wanted to pass the tax rate, we could do that in the arguments we pass to `bind` and not pass it when we call the `calc` function, as you see in the code below: 

```
const calc = bill.calculate.bind({total:500}, 0.06);
console.log(calc());
```

![](@attachment/Clipboard_2020-05-07-18-51-42.png) 13:07

As you can see, it still works! Why?

The additional arguments to `bind`, the first one will always be the `this` object, and then the additional ones will line up with the arguments that get passed. If `bill.calculate` took more arguments, like `tipRate`, we could pass another value as an argument.

Why is that helpful?

Sometimes, when you are generating functions, for example looping over a list of data, you have access to the data at the time of function creation, and then let's say later you want to call it.

Sometimes it's easier to pre-load the function by passing it what the arguments will be at call time when you are binding it. Then you can just go ahead and take the function and call it from wherever you want because you know the arguments are already included. 

#### `call` and `apply`

Let's move on to the two methods: `call` and `apply`. 

They work the exact same as `bind` does with one difference: they will call the function for you. 

![](@attachment/Clipboard_2020-05-07-18-56-58.png) 14:37 

##### `call`
Instead of returning, like you see happens above when we call `calc`, if we just duplicate the line of code where we are declaring `calc` and modify it like below, let's see what is returned..

```
const total2 = bill.calculate.call({total:500}, 0.06);
console.log(total2);
```

You will see we have 530 returned to us. 

What happened there?  `.bind` calls a function, which then needs to be called by itself. `call` does the same thing as `bind` but it will also run the function for you so you don't have to call it.

If you need to bind a function and call it later, use bind. 

If you need to bind a function that you want to call immediately you can use `call`. 

##### `apply`

![](@attachment/Clipboard_2020-05-07-19-02-22.png) 15:38

>Note: While the syntax of this function is almost identical to that of call(), the fundamental difference is that call() accepts an argument list, while apply() accepts a single array of arguments.

If you want to run one of the functions but you don't care what `this` is equal to, you can just pass null and then after you pass the additional arguments as an array. 

In our case, there is only one argument. 

```
const total3 = bill.calculate.apply({total:325}, [0.60]);
console.log(total3);
```

That is not very useful now that we have spread, because you could just spread into `call` but it's available if you need it. 

Let's add one more argument to our `bill` object. 


```
const bill = {
  total: 1000,
  calculate: function(taxRate){
    return this.total + (this.total * taxRate); 
  },
  describe(mealType,drinkType,taxRate){
    console.log(`Your meal of ${mealType} with a drink of ${drinkType} was ${this.calculate(taxRate)}`);
  }
}
```

Now we can try running the function in the console. 

```
bill.describe('pizza', 'beer', 0.13);
```
 
![](@attachment/Clipboard_2020-05-07-19-07-59.png) 17:52
 
As you can see the function works. 

Now if we wanted to run that with `call` and `apply` we could do the following.

```
const myMeal = bill.describe.call({total:342}, 'pizza','beer',0.13});
console.log(myMeal);
```

![](@attachment/Clipboard_2020-05-07-19-10-48.png)

Why do we pass an object as the first argument to `call`? Because that is what `this` will be equal to, and inside of `calculate` it looks for `this.total` so we need an object with a total property. 

The additional arguments are mealtype, drinktype and tax rate.

If you try running that, you will see that we get an error that "this.calculate is not a function". 

What is happening? 

![](@attachment/Clipboard_2020-05-07-19-13-28.png) 18:59

We called `this.calculate` but we didn't pass it the `this` that we wanted. Let's go modify the `myMeal` declaration like so that it has access to the `calculate` function.

```
const myMeal = bill.describe.call(bill, 'pizza','beer',0.13});
```

![](@attachment/Clipboard_2020-05-07-19-15-21.png) 19:08

Now it should be working for you.

If you were to `apply` that instead, we would pass all the arguments as one argument. 

```
const myMeal2 = bill.describe.apply(bill, ['pizza','beer',0.13]);
console.log(myMeal2);
```

That wraps up `call`, `bind`, and `apply`. 

When should you use them? When the `this`  value is different from what you have hoped. You won't always need it but it is helpful to know.































