---
attachments: [Clipboard_2020-04-02-07-57-18.png, Clipboard_2020-04-02-08-00-37.png, Clipboard_2020-04-02-08-04-55.png, Clipboard_2020-04-02-08-13-52.png, Clipboard_2020-04-02-08-14-45.png, Clipboard_2020-04-02-08-15-45.png, Clipboard_2020-04-02-18-06-00.png, Clipboard_2020-04-02-18-27-02.png, Clipboard_2020-04-03-19-28-22.png, Clipboard_2020-04-03-19-32-22.png, Clipboard_2020-04-03-19-36-31.png, Clipboard_2020-04-03-19-54-54.png, Clipboard_2020-04-03-20-03-21.png, Clipboard_2020-04-03-20-07-10.png, Clipboard_2020-04-04-17-57-58.png, Clipboard_2020-04-04-17-59-38.png, Clipboard_2020-04-04-18-08-40.png, Clipboard_2020-04-04-18-09-10.png, Clipboard_2020-04-04-18-13-12.png, Clipboard_2020-04-04-18-13-53.png, Clipboard_2020-04-04-18-15-41.png, Clipboard_2020-04-04-18-19-58.png, Clipboard_2020-04-04-18-25-38.png, Clipboard_2020-04-04-18-39-42.png, Clipboard_2020-04-04-18-46-34.png, Clipboard_2020-04-04-18-55-17.png, Clipboard_2020-04-04-18-56-31.png, Clipboard_2020-04-06-14-43-10.png, Clipboard_2020-04-06-14-49-10.png, Clipboard_2020-04-06-17-54-59.png, Clipboard_2020-04-06-19-27-38.png, Clipboard_2020-04-06-19-29-28.png, Clipboard_2020-04-06-20-09-03.png, Clipboard_2020-04-06-20-20-27.png, Clipboard_2020-04-06-20-22-30.png, Clipboard_2020-04-06-20-29-15.png, Clipboard_2020-04-06-20-33-24.png, Clipboard_2020-04-06-20-49-16.png, Clipboard_2020-04-06-20-49-53.png, Clipboard_2020-04-06-20-57-56.png, Clipboard_2020-04-06-21-04-35.png, Clipboard_2020-04-06-21-05-47.png, Clipboard_2020-04-06-22-42-28.png, Clipboard_2020-04-06-22-49-50.png, Clipboard_2020-04-06-22-49-53.png, Clipboard_2020-04-06-22-51-03.png, Clipboard_2020-04-06-22-53-06.png, Clipboard_2020-04-06-23-01-18.png, Clipboard_2020-04-06-23-03-08.png, Clipboard_2020-04-07-08-12-05.png, Clipboard_2020-04-07-08-14-02.png, Clipboard_2020-04-07-08-14-47.png, Clipboard_2020-04-07-08-17-27.png]
title: 'Module 8: Data Types'
created: '2020-04-02T11:47:12.050Z'
modified: '2020-04-07T12:22:17.922Z'
---

# Module 8: Data Types

## 41 - Objects

In this section of the course we will be learning about objects and arrays. In this video, we will focus on objects.

**Objects** are another fundamental building block of javascript, just like we have strings, numbers and booleans. Actually everything in Javascript is an object, as you soon will see. So, what are they?

Objects allow us to group together properties and values, or keys and values is what we often call it (throughout the course Wes will be saying properties and values). 

Objects have many uses from storing related data to storing functionality, all the way through to creating your own custom types.

Objects are used for when the order of the properties does not matter. That is very important to note. Let's do an example to demonstrate this. Open `objects.html` and add the following code in the body tag:

```
<script>
  const person = {
    name: "wes",
    age: 100
  };
  console.log(person);
</script>
```

Now if we console log the person object, what will we see? We will probably see the object displayed with the properties in the same order. 


![](@attachment/Clipboard_2020-04-02-07-57-18.png) 1:10

If you modify the code to swap out age and name so age comes first and then console log, you will see that the properties also changed order when we console logged it. However, just because the Javascript interpreter does that, never rely on the properties that you put into the object being in the same order.

### Creating an Object

Typically when you create an object, you are going to open up a curly bracket, and then go ahead and close that curly bracket like so:

```
const person = {
  
};
```

That is called the **object literal** syntax.

![](@attachment/Clipboard_2020-04-02-08-00-37.png) 1:30

You can also create an object like this:

```
const person = new Object({
  name: "wes",
  age: 100
});
```

You probably won't see that notation often or ever because the object literal syntax is much cleaner. 
In fact if you wanted to, you could create strings by doing `const name = new String('wes');` but we don't because it's simpler and shorter to use the **string literal syntax**. 

Note: we will talk about the new keyword in coming videos.

Let's talk about some of the keywords related to objects.

![](@attachment/Clipboard_2020-04-02-08-04-55.png) 2:31

The property is on the left, and then there is a colon and then we have the value on the right. The values of an object can be any type (string, function, boolean, other objects, arrays etc).

So for example let's say we have a variable, age which is set to 100 like so `const age = 100;`. 

Now we could swap out the harcoded age from our persons object and instead assign it the variable like so:

```
 const age = 100;
const person = new Object({
  name: "wes",
  age: age
});
```

If you console.log the person object now, you will see that age still shows the value of 100. That's a pretty common thing that we'll do. 

Now if you ever run into this situation where the property is the same name as the value variable that you're setting it to, you can simply get away with simply doing writing age like this:

```
 const age = 100;
const person = new Object({
  name: "wes",
  age
});
```

Age is both the property name and the value because the `age` variable is being used for the `age` property. That is the exact same thing as doing `age: age`.

The properties of an object pretty much follow the same rules as variables and Wes would recommend that you use the same rules as variables. However, you can go a bit further with the properties of an object. For example let's say we added one more property to our persons object..

```
 const person = new Object({
  name: "wes",
  age,
  "cool-dude": true
});
```

![](@attachment/Clipboard_2020-04-02-08-13-52.png) 4:07

As you can see, you can have a property with a dash in it, whereas you cannot have variables with dashes in them. 

Similarly you can also have spaces and numbers in your properties like so:

```js
 const person = new Object({
  name:'wes',
  age,
  'cool-dude': true,
  'really cool dude': false,
  '777': true,
});
```

![](@attachment/Clipboard_2020-04-02-08-15-45.png) 4:29

Also, you might notice that in the console the orders of the properties looks different from our code, which is expected and fine. 

After each property, you might notice that we add a comma. Wes recommends adding a comma after the last property in the object, even if there is nothing that comes after it. That is what is called a **trailing comma** or a **comma dangle**. 

It's not totally necessary, but putting a **trailing comma** on there will make sure that the next time you come around and add in a property, we can easily add it. What happens all the time is if you don't leave a trailing comma, the next time you go to add a property it's very easy to forget to include the comma.

If you forget to add a comma between properties, you will see an error similar to what is shown below. 

![](@attachment/Clipboard_2020-04-02-18-06-00.png) 5:37

Another reason is version control. Let's say someone else is coming in and editing your code. Instead of just adding a new property, they have to edit the line above to add a comma, and even though you only modified the line above by adding a comma, it will show up in git blame that you modified that line of code
 last. Git blame is a git functionality that shows who wrote which line of code. 

It used to be that comma dangles weren't supported, but now all modern browsers do support the comma dangle on object properties. 

Other things you can do is add nested properties or nested objects. For example we can create a property called clothing and assign it a sub object like so:

```
const person = new Object({
  name: "wes",
  age,
  "cool-dude": true,
  "really cool": false,
  "777": true,
  dog: "snickers",
  clothing: {
    shirts: 10,
    pants: 2
  }
});
```

![](@attachment/Clipboard_2020-04-03-19-28-22.png) 6:56

As you can see, now our persons object has a nested object called clothing which has shirt and pants properrties. You can nest objects as deep as you could possibly want. 

There is a gotcha about copying or cloning objects which we will talk about in just a second. 

You can add new properties to an object even after it has been created. You would use the dot notation to do that. For example if we wanted to add a job property to the person object we could simply add this line of code: `person.job = 'Web Developer'`

Now if you were to take a look at it in the console, you will see the job property has been added and is now part of the object. 

![](@attachment/Clipboard_2020-04-03-19-32-22.png) 7:35

Similarly if you were trying to overwrite a property, you could do that as well. For example is you add this line `person.age = 50;` and then refresh the html page and look at the console, you will see that age is now set to 50 even though when creating the object we set it to the variable age which was 100. 

![](@attachment/Clipboard_2020-04-03-19-36-31.png) 7:52

You might have noticed that the person object is a const variable, however we just went ahead and changed part of it. 

That is a gotcha in javascript. Const does not mean that the value of an object cannot be changed. Const means that the binding to that person cannot be changed. What does that mean?

To explain, let's rename the person variable to Wes. You code should now look like this:

```
const age = 100;
const wes = new Object({
name: "wes",
age,
"cool-dude": true,
"really cool": false,
"777": true,
dog: "snickers",
clothing: {
  shirts: 10,
  pants: 2
}
});
wes.job = "Web Developer";
wes.age = 50;
console.log(person);
```

Think about it like this.. Wes is Wes, he has been born and this object represents properties about him. Those properties can change as he grows up, however no one can ever replace him. No one can ever overwrite the binding to him. 

No one could ever come by and say "oh a new Wes was born" and create an object like this further down in the code:

```
wes = {
name: 'Westopher',
age: 12,
job: 'Web Master'
}
```

You can't do that. 

If you refresh the html page and open the console, you will see this error 

![](@attachment/Clipboard_2020-04-03-19-54-54.png) 9:00

Even if you put the keyword const infront of the second wes object, you will still get an error that says 
>Identifier 'wes' has already been declared.

That won't work because the binding to 'wes' has already been created. Even though properties on the wes object can change, the actual object itself will can never be overwritten entirely. 

If you do ever want to freeze the values in an object, what you can do is create a frozen object. You use the captial "O" Object and call `.freeze()` on it and pass the object to it that you want to freeze.

Add the following code at the bottom of the script tag:

```
const wesFroze = Object.freeze(wes);
```

That won't freeze the original object wes, but what it will do is return a new object, called `wesFroze` and that can never be changed. 

To demonstrate this, refresh the HTML page and then type wesFroze in the console. That should return the object. Now type in `wesFroze.age = 100` to try to overwrite the age, and hit enter (it should return 100). Now type in wesFrozen again and the object should be returned to you and the age property should still be set to 50. 

![](@attachment/Clipboard_2020-04-03-20-03-21.png) 9:57 

So if you ever want to make an object so it cannot be changed, you could do that with `Object.freeze()`. 

The word in programming that we use to describe something that cannot be changed is **immutable**. **Mutation** is changing a value. 

### Accessing Properties

Wes has already shown us one way to access properties, which is using the dot notation. For example to access the job property you would write `wes.job` which would return "Web Developer".

![](@attachment/Clipboard_2020-04-03-20-07-10.png) 10:35

stopped at 10:35

Just like when we looked at DOM elements, we have getters and setters, objects. That is the exact same thing with an object. In fact, a DOM element is just an object with a bit of extra functionality added to it. 

That is the first way, and that is typically the approach you will use in almost every use case. 

However, we have this other notation to access properties and that is with **square brackets**. 

Similarly to how you can access the property using the dot notation you can also use **square brackets**. You simply write the object name then a set of square brackets, and between the square brackets you give the property name in strings, like so: 

```js
console.log(wes.age);
console.log(wes["age"]);
```

Why do we have that? That seems like a much uglier way to access the properties. There are a few reasons. 

One reason is that this method allows us to pass a variable that is a string type to the square brackets instead of passing a string directly. Let's do an example. 

In the `person` object, add another property like so: 

```
const wes = new Object({
  name: "wes",
  propertyToCheck: "NEVER",
  age,
  "cool-dude": true,
  "really cool": false,
  "777": true,
  dog: "snickers",
  clothing: {
    shirts: 10,
    pants: 2
  }
});
```

Remove the square bracket console log we added above and add the following code instead:

```
console.log(wes.age);
const propertyToCheck = prompt("What do you want to check?");
console.log(propertyToCheck);
console.log(wes[propertyToCheck]);
```

As you can see, instead of passing `"age"` to the square brackets, we are passing the `propertyToCheck` variable instead. The value of propertyToCheck is assigned to whatever we enter into the prompt. Refresh the html page and you should see the following:

![](@attachment/Clipboard_2020-04-04-17-57-58.png) 12:27

If you open the console and then enter a proerty into the prompt such as age, you will see the value is logged. For example, if you were to type in clothing, it gives you the object that is the clothing. 

![](@attachment/Clipboard_2020-04-04-17-59-38.png) 12:32 

That is one reason: when the property of the object is stored in a variable, because you can't just write `wes.propertyToCheck` because the code will literally look for a property named `propertyToCheck` on the object, it will not be able to interpret that it is a variable. Let's test this out.. add the following line of code and refresh the HTML page:

```
console.log(wes.propertyToCheck);
```

You should see the word "NEVER" logged in the console. Wes asked us to add that property earlier to demonstrate this: if you use the dot notation, the code will assume you are looking for a property with that name, and it will not know it's a variable. If the property name is stored in a variable, you must use square brackets.

There is another reason, which sometimes the properties of your object are not referenceable via Javascript, you have to use a string. 

Comment out the following code as demonstrated below and refresh the html page. 

```js
//const propertyToCheck = prompt("What do you want to check?");
//console.log(propertyToCheck);
//console.log(wes[propertyToCheck]);
```

In the console, you can write `wes.age` and the age will be returned, however you CANNOT type `wes.cool-dude` for example because they are invalid property lookups. 

![](@attachment/Clipboard_2020-04-04-18-09-10.png) 13:39

So if that is the case for all three of those properties, (`777`, `really cool`, `cool-dude`) you would have to use square bracket notation to access them. 

So why is that there if it's not really a good idea? Well sometiems you get data that comes from another language, or you get data that comes from server side. If that's the case, you don't really have a whole lot of options so you have to use the square bracket notation in order to reference it.

To reference multiple levels deep, it's the same. For example you would write `wes.clothing.pants` to return the value of the pants property within the children object that is nested within the wes object. 

![](@attachment/Clipboard_2020-04-04-18-13-12.png) 14:26

The only gotcha there is if you try to access a property on an object that does not exist, such as `wes.jobs`, it will evaluate to undefined. 

![](@attachment/Clipboard_2020-04-04-18-13-53.png) 14:41

However, if you try to access a nested property on a property that does not exist, it will throw an error:  

![](@attachment/Clipboard_2020-04-04-18-15-41.png) 14:50

This is a very common error:

>VM181:1 Uncaught TypeError: Cannot read property 'main' of undefined
>    at <anonymous>:1:10

That is because there is no property that exists on that undefined value. Because `wes.jobs` is undefined, there are no properties that live inside of that. 

If that is the case, the you have to write the following to not throw an error:

```
wes,jobs ? wes.jobs.side : 'Jobs doesn't exist`;
```

![](@attachment/Clipboard_2020-04-04-18-19-58.png) 15:#0

There is a proposal and hopefully it will be out soon, which will allow us to do a deep check. It will allow us to do something like this  `wes?.jobs?.side`.

What that would do is the code would say does `wes` object exist? if so, check is the `jobs` property exists, if so, get the value of `side`. That would allow us to do many layers deep. 

It is often the case that we have to write code like this to safely check for the existence of a nested property:

```js
if(wes && wes.jobs ** wes.jobs.first){

}
```

Sometimes we don't know if any of the properties exist and instead have to check one by one or else we will run into the "cannot read property of undefined" error. 

NOTE: This currently does not exist. If you wish to see the status of it, search "Optional Chaining MDN".

We will often use an if statement like that when we are using inputs. To demonstrate, add the following code right after the opening body tag:

```html
<body>
<input type="text" name="first">
```

If you refresh the HTML page, you will see the input on the page: 

![](@attachment/Clipboard_2020-04-04-18-25-38.png) 16:58

Often what happens is we will try to select that input from the form like so:

```
  const nameInput = document.querySelector('[name="first"]');
  const name = nameInput.value;
  console.log(name);
```

We are going to set a value on the input so that it is there on page load. Modify the code like so:

```html
 <input type="text" name="first" value="Wes" />
```

When you refresh the page, you should see wes in the console. 
However, if you comment out that input and then refresh the page, you will get an error "cannot read property value of null". 

Why does that happen? 

Because we are assigning to the variable `nameInput` an html element that does not exist so `nameInput` is null. And then it checks for a property called `.value` on it. So if that were the case, and you run into this all the time, you had to do the following:

```
if (nameInput) {
  const name = nameInput.value;
}
```

However there we are making a scoped const variable which isn't very useful because it cannot be used outside the if block. To fix that you could do:

```js
const name = nameInput? nameInput.value : '';
```

That code is first checking whether nameInput exists. If it does, it gets the `value` property on it, and if it doesn't, the name variable evaluates to an empty string.

### Deleting a Property from an Object

To delete a property object you use the delete keyword. 

For example `delete wes.job;` will delete the job property. If you are curious if it worked or not, you can save the result in a variable or simply console log it and a delete will either return true or false based on whether it is deleted or not. 

Add the following code:

```
console.log(delete wes.job);
```

Now if you take a look, you will see it is undefined.

![](@attachment/Clipboard_2020-04-04-18-39-42.png) 19:19

Sometimes you will also see people setting values to be null or undefined. For example `wes.age = undefined;` or `wes.age = null;`. Those are not deleting the properties, they are simply setting them to be null or undefined (in some frameworks that will allow the code to just skip over it).

In an uncoming video, we will cover **loops** and **looping**. It is a pretty common thing to want to loop over the data that is in an object or an array. 


### Methods 

Now, let's talk about methods. We have already talked a lot about this. As we went over earlier, the difference between a method and a function is that a method is just a function that lives inside of an object. That is all we have learned so far. 

If we go back to our 'wes' object and add a property called `sayHello`, we can set it to a function, and that function could take in a greeting if you want (the funtion works the smae as any function that you would have) and from that we could return the greeting in a string and then the name like so:


```
const wes = new Object({
  name: "wes",
  propertyToCheck: "NEVER",
  age,
  "cool-dude": true,
  "really cool": false,
  "777": true,
  dog: "snickers",
  clothing: {
    shirts: 10,
    pants: 2
  },
  sayHello: function(greeting = "Hey") {
    return `${greeting} ${this.name}`;
  }
});

```

Now if you fresh the page, open the console and type in `wes.sayHello()` you should see "Hey wes" in the console. 

You can also try passing in a greeting like so: `wes.sayHello('Hello');`  which would return "Hello wes". 

![](@attachment/Clipboard_2020-04-04-18-46-34.png) 21:04

You may be working what is the `this` keyword that we use in the `sayHello` function when we call `${this.name}`. Like we have mentioned in the past, when you take a look at a method, and if you look to the left of the dot, `this` will always be equal to the left of the dot.

So in our case, `${this.name}` is going to be equal to "wes" because that is the value of the `name` property on our object. You can access the other properties using the this keyword too. 

The reason we use the `this` keyword instead of using `${wes.name}` within the `sayHello` function is because when we get into prototyping, you are going to see how you can use methods like `sayHello` on multiple people rather than just on a person named wes. 

We could create a person object that is a new instance of Wes or Scott and Kate etc. In that case, the `sayHello` method will exist on all of them, and we can reference the current person's name using `${this.name}`.

We will go into that a lot more in the future once we go into prototypes. For now, just know that when you have a function as a property on an object, that is referred to as a method of that object.

There also is a method shorthand similarly to how instead of having to write `age:age` for the age property we were able to just write `age`, the shorthand for the function consist of taking the function keyword away and the colon like this:

```
const wes = new Object({
  name: "wes",
  propertyToCheck: "NEVER",
  age,
  "cool-dude": true,
  "really cool": false,
  "777": true,
  dog: "snickers",
  clothing: {
    shirts: 10,
    pants: 2
  },
  sayHello(greeting = "Hey") {
    return `${greeting} ${this.name}`;
  }
});
```

That is just a shorthand, it does the exact same thing. It is **not** an arrow function.

However, you can add arrow functions. Let's add another property called `sneeze` like so:

```
sneeze: () => {
  console.log("AHHHH CHOOO");
}
```

That is still a method, however because it is an arrow function as a property on an object, we do not have access to the this keyword.

If you also try to console log the `this` keyword like so, you will see it evaluates to Window. 

```js
sneeze: () => {
  console.log("AHHHH CHOOO", this);
}
```

![](@attachment/Clipboard_2020-04-04-18-55-17.png) 22:58

If you were to change that, to a regular function, `this` would be equal to wes. 

![](@attachment/Clipboard_2020-04-04-18-56-31.png) 23:05

We will go into why that is later but the short answer for now is that arrow functions do not scope this to the thing they are called against, and the parent scope will inherit that. 

That is a high level overview of what objects are. In the next few videos we will get deeper into things you need to know, such as little gotchas before we can then dive into arrays. 

---

## 43 - Object Reference vs Values

An important thing to understand in Javascript is the difference between a reference and a value. 

We will use an example to highlight the differences.

Let's say we have the following two variables, both assigned the value of 'wes':

```
let name1 = 'wes';
let name2 = 'wes';
```

We can check if those variables are equal by adding this line of code `conosole.log(name1 === name2);`, which should return true because both values are identical in both value and type. 

However, what if we assign `name1` the value of scott, and then check if they are equal like so? 

```
let name1 = 'wes';
let name2 = 'wes';

console.log(name1 === name2);
name1 = 'scott';
console.log(name1 === name2);
```

That will return false, which is no surprise. 
Now, the question is, what if you set name1 to equal name2 like so? `name1= name2;`. 

Now if you console log again to check the comparison, it will return true. If you check the value of each variable, `name1` and `name2` will both return "wes". 

![](@attachment/Clipboard_2020-04-06-14-43-10.png) 1:18

If you were to take name2 and set it to name1, that is the same thing, both values would still equal "wes", like so:

`name2 = name1;` 1:28

Now the question is, if you change name2, like so `name2 = 'westopher';`, will name1 and name2 still be equal? We can check what both variables evaluate to by typing them into the console. 

![](@attachment/Clipboard_2020-04-06-14-49-10.png) 1:43

You will notice that `name1` is still "wes" while `name2` is "westopher", because we have not updated `name1`. 

So there are a couple of things to note in this excercise: 
 
1. The triple equals checks that both the type and the value are identical.

2. When we set one string variable to be another, the value is copied from one to another. Meaning that when we take `name1` and set it to `name2` (`name1 = name2;`), it just takes the value of `name2` and pastes it to `name1`. So when you update one of the variables, the one pointing to it does not update itself. You may be saying duh, obviously, that's how variables work. But now we will go over how that works for objects, because the example we did was with a string.

Let's demonstrate this with an object now. 

Create a `person1` variable and assign to it an object with first and last properties like so:

```
const person1 = {
  first: "wes",
  last: "bos"
};
```

Duplicate that code by copy and pasting and renaming the variable to `person2`. The only thing we want to change is `person2`. 

```
const person1 = {
  first: "wes",
  last: "bos"
};
const person2 = {
  first: "wes",
  last: "bos"
};
```

If you refresh the HTML page and open the console, if you try typing in `person1 === person2` you will see it is returning false. 
Why?

![](@attachment/Clipboard_2020-04-06-17-54-59.png) 3:01

You be thinking "it's the exact same object. It's an objects with the same contents inside of it, so why are we getting false when we are checkign them?". 

That is because when you are comparing objects, it is done by reference to the object itself, not the values inside of it. That means if they are two totally separate objects, they simply have the contents by change. So in our example, `person1` and `person2` are both objects but they are not the same, even though the contents inside of them are the same, they are not the same object. 

That is different from the contents of a string because a string can only have a value whereas an object and, as we will learn, arrays can have multiple things inside of them, whether they are property and values, or whether they are just straight up items.

Next thing we need to know about objects is that if you make a new person object like so:

```
const person3 = person1;
```

If refresh the HTML page and look at person3 in the console, you should see the following:

![](@attachment/Clipboard_2020-04-06-19-27-38.png) 4:17

Now if you go ahead and update person3's name as demonstrated below, what will you see in the console when we log `person3.first`?

```
const person3 = person1;
person3.first = 'Larry';
console.log(person3.first);
```

![](@attachment/Clipboard_2020-04-06-19-29-28.png) 4:34

You get Larry.

However, what if we console log `person1.name` as shown below? 

```js
const person1 = {
    first: "wes",
    last: "bos"
  };
  const person2 = {
    first: "wes",
    last: "bos"
  };
const person3 = person1l 
person3.first = 'Larry';
console.log(person3.first);
console.log(person1.first);
```

If you look at the person1 object, we have set "wes" as first and "bos" as last. So `person1.first` should be Wes, right?

WRONG! It returns Larry. 

![](@attachment/Clipboard_2020-04-06-20-09-03.png) 4:49 

If you try typing `person1`, `person2`, and `person3` in the console, you should see the following returned:

![](@attachment/Clipboard_2020-04-06-20-20-27.png) 5:03

What is going on there? We just updated `person3`, but for some reason, person1 was updated as well. 

In the console, let's try updating `person3.last` like so: `person3.last = 'Cool'`. So `person3.last` should now return "Cool", but what about `person1`? 

![](@attachment/Clipboard_2020-04-06-20-22-30.png) 5:23

So what the heck!? Why is `person1` being updated? The reason that it happens is a fundamental concept of Javascript, that will come and bite you in the butt if you don't understand it. 

The reason that it happens is that when objects and arrays are copied by reference, (like we did with `const person3 = person1;`), we are not taking a copy of it. We are simply creating a variable that references, or points to, the original variable instead of making a copy of it. 

That can lead to unexpected bugs down the road because you might think you're simply creating a copy of it, and then modifying it, but you are not. `person3` was never it's own object, it was just pointing at the original object.
The same thing works with Arrays and Maps and Sets which we will learn in the future. 

So what are your options as a developer when you want to take a copy instead of referencing? There are a couple of different ways you can copy and object. The easiest way to copy something is via something called a **spread**. 

A **spread** is a three dot operator and it's used for taking every single item in a object and spreading it into a new object. 
So instead of doing `const person3 = person1;`, you would do something like this:

```js
const person3 = { ...person1 };
```

What we are doing there is we are assigning the variable `person3` to a new object using the object literal syntax, and then using the spread operator within the object literal to copy person1. 

![](@attachment/Clipboard_2020-04-06-20-29-15.png) 7:14

If you console.log `person3`, you will see that it has the same properties as person1. That is because the spread operator will take every single item that is in an object and spread it into the next object. 

There is another way to do this, which is not as popular since spread has been introduced, but previously a lot of people used this method. You call `Object.assign()`, and start with an empty object, and then fold in the other object into it.

```js
const person3 = Object.assign({}, person1);
```

You probably won't see that all that much but if you do, know that is a way to take a copy of an object just like the spread. 

So if you use the spread operator and then try to change the value of `person3.first` to Larry, like so, what would you get? 

```
const person3 = {...person1};
person3.first = 'Larry';
```

If you refresh the HTMl page and then console.log `person3.first` and `person1.first`, you will see that only the value of `person3.first` was updated. 

![](@attachment/Clipboard_2020-04-06-20-33-24.png) 8:15

That is because this time we used the spread operator which gave us a copy of the person1 object, and not a reference like we did earlier. 

One thing to do note is that the spread operator only goes one level deep. That means that if we went up to `person1` and added a clothing object, then took a copy of that in person3 like so:

```
const person1 = {
  first: "wes",
  last: "bos",
  clothing: {
    shirts: 10,
    pants: 2
  }
};
const person3 = {... person1};
person3.first = Larry;
```

![](@attachment/Clipboard_2020-04-06-20-49-16.png) 8:59

If you try to update  `person3.clothing.shirts = 100;` and then view the object in the console, you will notice that `person3.clothing.shirts` does equal 100. However if you look at `person1`, you will notice that `person1.clothing.shirts` was also updated to be 100.

![](@attachment/Clipboard_2020-04-06-20-49-53.png) 9:11

We have the same problem. `person1.clothing.shirts` was also updated even though Wes just told us we can take a copy of an object with a spread operator. So what we need to take away from that is that the spread operator and the `Object.assign()` operator, they do what is called a **shallow** copy, meaning that they will only ever go one level deep when copying. 

If you do want to do a **deep clone** or a **deep copy** of an object, of all of the properties, there are a number of different ways to do it. 

The most popular way is most likely to use something called a **utility library**. 


### Lodash 

Wes most often uses https://lodash.com. 

Lodash is a library that you can include into your script. 

It has a lot of methods that are used when working with objects and arrays. One of those is for doing copies of objects. Let's take a look at the documentation by searching for the keyword clone on the website. 

![](@attachment/Clipboard_2020-04-06-20-57-56.png) 10:28

Based on the documentation we can see that `_.clone(value)` creates a shallow clone of a value. The documentation also provides an example of how to use the method. You would use it by calling  `_.`, which is where all the lodash methods live, and then calling `.clone()`.  That will just do a high level clone like we did with the spread operator earlier, so there is not much value in that.

There is another method called `_.cloneDeep`.

![](@attachment/Clipboard_2020-04-06-21-04-35.png) 11:00

Clone deep will also take a copy of any nested objects for us. 

How do you use that? Wes likes to use something called UNPKG (https://unpkg.com). If you navigate to `https://unpkg.com/lodash`, it will load the latest lodash, so we can just take that url and go up above the script that we need and add it. When you're loading Javascript that other code is dependent on, you need to load that first. 

Add the following within the body, after the input:

```
<script src="https://unpkg.com/lodash@4.17.15/lodash.js"></script>
```

Now if you type `_.` in your console, you will see that all of the lodash values are available to us.

Later when we cover modules, Wes will show us how to load just the ones you need, because it's unlikely you will need every method in the library but for simplicities sake, we are loading the entire library now. 

Further down in our code `const person3 = {... person1};`, where we were copying, comment that line out. Underneath it add:

```
const person3 = _.cloneDeep(person1);
person3.first = 'Larry';
person3.clothing.shirts = 100;
```

![](@attachment/Clipboard_2020-04-06-22-42-28.png) 12:29

As you can see, `person1.clothing.shirts` still equals 10, because we performed a deep clone using the lodash method and then modified the value only for the `person3` object because `person3` was no longer a reference to `person1`. 

Wes doesn't reach for this a lot of the time but that is mostly because the stuff he does can just be done by Javascript, but when you do have to do harder things like a deep clone, you can reach for a lodash method. 

Lodash also has methods for working with arrays. 

The `...` spread operator is also helpful when working with merging objects. 

To demonstrate that, we will do an example. Add the following code:

```
const meatInventory = {
  bacon: 2,
  sausage: 3.
};

const veggieInventory = {
  lettuce: 5, 
  tomatoes: 3,
};
```

So we have these two objects: `meatInventory` and `veggieInventory`, both of which have two properties each.

Now we want to merge these two objects and the easiest way to do that is to just make a new variable, an object literal, the dot dot dot followed by one of the objects you want to merge, and then a comma followed by a dot dot dot of the next object you want to merge, as so on, like so: 

```
const inventory = {...meatInventory, ...veggieInventory};
```

You can spread in as many objects as you want.

Now we have a new inventory property which you can see if you refresh the page, open the console and type in `inventory`. 

![](@attachment/Clipboard_2020-04-06-22-49-53.png) 13:41

You can also put some objects on their own line and add your own values in. 

For example you could do:

```
const inventory = {
  ..meatInventory, 
  ...veggieInventory,
  oysters: 10,
  };
```

And you can see that oysters will be added to it.

![](@attachment/Clipboard_2020-04-06-22-51-03.png) 13:58

You can mix and match the spreading. 
The only thing you really need to know about that is if there are duplicates (for example oyster could be an oyster mushroom or an oyster from the sea),  which one will win out?

Let's say we added oyster to `meatInventory` AND `veggieInventory` like so:

```
const meatInventory = {
  bacon: 2,
  sausage: 3.
  oyster: 10,
};

const veggieInventory = {
  lettuce: 5, 
  tomatoes: 3,
  oyster: 15,
};
const inventory = {
  ..meatInventory, 
  ...veggieInventory,
  };
```

![](@attachment/Clipboard_2020-04-06-22-53-06.png)  14:30

`oyster:15` wins out. Why? Because `veggieInventory` comes after in the spread, so the order of the spread does matter in this case. Similarly, if you were to type in:

```
const inventory = {
  ..meatInventory, 
  ...veggieInventory,
  bacon: 10,
  };
```

Bacon would be 10 because it would overwrite the value in the `meatInventory`.

Wes really likes the spread operator. It can also be used for arrays which we will learn about in the arry lessons. 

The last thing we are going to hammer home is that the concept of passing in via reference vs copy also applies to functions. 

So if you had a function `doStuff`, which took in an argument called data, and within the function we modified the value of data to be somethign else, like so:

```
function doStuff(data){
  data = 'something else';
}
```

ALl this function does is take in an argument, and changes that data for whatever reason. 

Now if we were to run that function and pass it our name1 variable which was set to "wes" way up in the code, if we were to take a look at that and console.log the data like so:

```
function doStuff(data){
  data = 'something else';
  console.log(data);
}
doStuff(name1);
```

If you refresh the page and type in `name1` in the console, it should still return "wes". What that means is when you passed in the `name1` variable to `doStuff`, you were only passing in the value of "wes", it doesn't actually reference to the external variable (which is good!).

Now, let's do that again with an object:

```js
function doStuff2(data){
  data.tomatoes = 1000000000l
  console.log(data);
}

doStuff(inventory);
```

![](@attachment/Clipboard_2020-04-06-23-01-18.png) 16:39

If you refresh the page and look in the console, you will see the value of data logged as shown above. 

However, if you type in `inventory`, which is the object that lives outside of the `doStuff2` function, you will see that it also contains the tomatoe property.

![](@attachment/Clipboard_2020-04-06-23-03-08.png) 16:50

That means that if you pass in an object to a function, and you modify that object, the external object will also be updated.

That is not the case for booleans, numbers and strings, but it is the case for objects and strings. 

That means that if you modify an object or an array that is passed into a function inside of the function, know that you may be accidentally modifying data that lives outside of it. That is a huge source of bugs, because when you pass in data as a reference, you may be unknowingly modifying data that lives outside of that function.

If that is the case, you make sure you pass it in as a copy. It may be the case that you want to modify external data, but sometimes you don't and it leads to bugs. 

---

## 44 - Maps

In the `/playgrounds` folder, open up `maps.html`. We are going to learn about this thing called a **map**. It is very similar to an object, however there are a couple of key differences.

We will cover: how does it work, what does it do and lastly why you would want to use one over an object or how to decide whether to use a map or an object.

The way you create a map is using the `new` keyword followed by `Map()` with a capital M.  

```
const myMap = new Map();
```

In order to add items to a map, we have the following APIs:
- set `.set()`
- has `.has()`
- delete `.delete()`

We will go through all of them. 

#### Set

Firstly, you take `myMap` and you `set()` it, to which you pass two arguments. The first is going to be what the key of the map will be, so let's call it a 'name' and then we set the value of it. 

```
myMap.set('name', 'wes');
console.log(myMap);
```

![](@attachment/Clipboard_2020-04-07-08-12-05.png) 1:06

As you can see in the console, we have our map and it gives us our entries, entries are the actual values in the map.

Now if you were to use the object notation that we are used to, something like `myMap.age = 100;`, you will notice that it's not actually added in the same spot. 

![](@attachment/Clipboard_2020-04-07-08-14-47.png) 1:33 

It is in the map, but it is a property on the map, not an actual entry in our map. 

So why is this useful?

Well, there are a couple of nice things about this API, apart from the fact that we have a `.set()` method and a `.has()` method and a `.delete()` method, one big benefit of a map is the keys can be any type other than just using a string or an allowed variable name. 

So instead of passing name as the key when we called `.set()` on `myMap`, we could pass a number like `myMap.set(100, 'This is a number');`

![](@attachment/Clipboard_2020-04-07-08-17-27.png) 2:09

As you can see, the entry has a key of 100. 

Previously we have only had the ability to add different types in the value portion of an object,  

stopped at 2:25
