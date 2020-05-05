---
attachments: [Clipboard_2020-05-05-07-07-33.png, Clipboard_2020-05-05-07-08-27.png, Clipboard_2020-05-05-07-13-11.png, Clipboard_2020-05-05-07-17-20.png, Clipboard_2020-05-05-07-18-48.png, Clipboard_2020-05-05-07-21-30.png, Clipboard_2020-05-05-07-22-59.png, Clipboard_2020-05-05-07-26-24.png, Clipboard_2020-05-05-07-28-09.png, Clipboard_2020-05-05-07-30-04.png, Clipboard_2020-05-05-07-30-40.png, Clipboard_2020-05-05-07-34-51.png, Clipboard_2020-05-05-07-36-05.png, Clipboard_2020-05-05-07-38-40.png, Clipboard_2020-05-05-07-39-11.png]
title: 'Module 11: Prototypes, this, new and Inheritance'
created: '2020-05-04T23:17:43.495Z'
modified: '2020-05-05T11:40:01.032Z'
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
