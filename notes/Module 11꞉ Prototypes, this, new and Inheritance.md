---
attachments: [Clipboard_2020-05-05-07-07-33.png, Clipboard_2020-05-05-07-08-27.png, Clipboard_2020-05-05-07-13-11.png, Clipboard_2020-05-05-07-17-20.png, Clipboard_2020-05-05-07-18-48.png, Clipboard_2020-05-05-07-21-30.png, Clipboard_2020-05-05-07-22-59.png, Clipboard_2020-05-05-07-26-24.png, Clipboard_2020-05-05-07-28-09.png, Clipboard_2020-05-05-07-30-04.png, Clipboard_2020-05-05-07-30-40.png, Clipboard_2020-05-05-07-34-51.png, Clipboard_2020-05-05-07-36-05.png, Clipboard_2020-05-05-07-38-40.png, Clipboard_2020-05-05-07-39-11.png, Clipboard_2020-05-05-20-01-34.png, Clipboard_2020-05-05-20-10-58.png, Clipboard_2020-05-05-20-17-59.png, Clipboard_2020-05-05-20-19-43.png, Clipboard_2020-05-05-20-24-17.png, Clipboard_2020-05-05-20-25-07.png, Clipboard_2020-05-05-20-29-08.png, Clipboard_2020-05-05-20-34-05.png, Clipboard_2020-05-05-20-35-44.png, Clipboard_2020-05-05-20-38-13.png]
title: 'Module 11: Prototypes, this, new and Inheritance'
created: '2020-05-04T23:17:43.495Z'
modified: '2020-05-06T00:40:36.808Z'
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

































































































