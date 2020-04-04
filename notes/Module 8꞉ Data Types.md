---
attachments: [Clipboard_2020-04-02-07-57-18.png, Clipboard_2020-04-02-08-00-37.png, Clipboard_2020-04-02-08-04-55.png, Clipboard_2020-04-02-08-13-52.png, Clipboard_2020-04-02-08-14-45.png, Clipboard_2020-04-02-08-15-45.png, Clipboard_2020-04-02-18-06-00.png, Clipboard_2020-04-02-18-27-02.png, Clipboard_2020-04-03-19-28-22.png, Clipboard_2020-04-03-19-32-22.png, Clipboard_2020-04-03-19-36-31.png, Clipboard_2020-04-03-19-54-54.png, Clipboard_2020-04-03-20-03-21.png, Clipboard_2020-04-03-20-07-10.png, Clipboard_2020-04-04-17-57-58.png, Clipboard_2020-04-04-17-59-38.png, Clipboard_2020-04-04-18-08-40.png, Clipboard_2020-04-04-18-09-10.png, Clipboard_2020-04-04-18-13-12.png, Clipboard_2020-04-04-18-13-53.png, Clipboard_2020-04-04-18-15-41.png, Clipboard_2020-04-04-18-19-58.png, Clipboard_2020-04-04-18-25-38.png]
title: 'Module 8: Data Types'
created: '2020-04-02T11:47:12.050Z'
modified: '2020-04-04T22:29:53.387Z'
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

Often what happens is we will try to select that input from the form. 

```
  const nameInput = document.querySelector('[name="first"]');
  const name = nameInput.value;
  console.log(name);
```

We are going to set a value on the input so that it is there on page load. Modify the code like so:

```html
 <input type="text" name="first" value="Wes" />
```

Now, if that input was not on the page, we would get an error "cannot read property of null". 

stopped at 17:37
