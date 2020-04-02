---
attachments: [Clipboard_2020-04-02-07-57-18.png, Clipboard_2020-04-02-08-00-37.png, Clipboard_2020-04-02-08-04-55.png, Clipboard_2020-04-02-08-13-52.png, Clipboard_2020-04-02-08-14-45.png, Clipboard_2020-04-02-08-15-45.png]
title: 'Module 8: Data Types'
created: '2020-04-02T11:47:12.050Z'
modified: '2020-04-02T12:15:47.908Z'
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
  '777': true
});
```

![](@attachment/Clipboard_2020-04-02-08-15-45.png) 4:29
