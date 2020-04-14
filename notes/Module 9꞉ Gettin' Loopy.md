---
attachments: [Clipboard_2020-04-13-18-40-09.png, Clipboard_2020-04-13-18-42-05.png, Clipboard_2020-04-13-18-44-15.png, Clipboard_2020-04-13-18-47-12.png, Clipboard_2020-04-13-18-51-19.png, Clipboard_2020-04-13-19-54-31.png, Clipboard_2020-04-13-20-01-24.png, Clipboard_2020-04-13-20-03-31.png, Clipboard_2020-04-13-20-04-13.png, Clipboard_2020-04-13-20-05-28.png, Clipboard_2020-04-13-20-09-22.png, Clipboard_2020-04-13-20-11-27.png]
title: 'Module 9: Gettin'' Loopy'
created: '2020-04-13T22:24:51.247Z'
modified: '2020-04-14T00:24:13.334Z'
---

# Module 9: Gettin' Loopy

## 49 Looping and Iterating - Array .forEach

Let's talk about looping and iterating. There are a few different ways to loop in Javascript and we will cover them all.

The most common way you are going to loop over something in javascript is looping over an array. Most of the looping also works the exact same way. 

We use a method that lives on our array, and we pass it a callback, exactly like we did in the previous video. The callback function will run once for every item in the array, giving us access to each individual item.

Open up the `array-looping-methods-START.html` file, which contains all the practice data we will be using for these exercises. Most of it is the same as the last video with the addition of a students array.

```
 const toppings = ['Mushrooms ', 'Tomatoes', 'Eggs', 'Chili', 'Lettuce', 'Avocado', 'Chiles', 'Bacon', 'Pickles', 'Onions', 'Cheese'];
```

If you wanted to loop out over every single one of the toppings in th array and log them to the console, or display them to the user, the very basic loop we have is the `.forEach()`. You should recognize it from previous exercises we did when we were adding event listeners to multiple elements.

What we do is we take toppings and use the `forEach` method on it, passing it a callback function that will run once for each item in the array. We can define our function outside or inline. 

```
function logTopping(topping){
  console.log(topping);
}
toppings.forEach(logTopping)
```

![](@attachment/Clipboard_2020-04-13-18-40-09.png) 10:06

If you refresh the page, you will see that we are logging every single one of the toppings as we loop over them. 

One thing Wes likes to do is throw a debugger into the foreach and take a look at the dev tools. Modify the code like so to add the debugger:

```
function logTopping(topping){
  console.log(topping);
  debugger;
}
```

When you refresh the HTML page, the debugger should open once it hits the first item in the array. 

![](@attachment/Clipboard_2020-04-13-18-42-05.png) 9:52

As you can see, the debugger is in paused state. We have access to the callstack, what function we are in, in our case it tells us we are in `logTopping`. 

Below it tells us what the `topping` variable is equal to which is "Mushrooms". It also tells us the value of the `this` variable which is equal to the Window. 

If you click the symbol shown in this image twice: ![](@attachment/Clipboard_2020-04-13-18-44-15.png) 9:24 
it runs again. Now we have are on thet "Tomatoes" item. You can click all the way through the array. 

As you know, we can also inline the function like shown below and it will give us the exact same thing.

```
toppings.forEach(topping => {
  console.log(topping);
})
```

One thing you might be having trouble with is where is this `topping` variable shown highlighted below is coming from? You may be wondering if it's a special keyword because it is a singular of toppings which is the name of the variable that holds the `toppings` array. 

![](@attachment/Clipboard_2020-04-13-18-47-12.png) 8:25

If you remember back to when we learned about arguments and placeholders we said that arguments were the actual values and the parameters were the placeholders.

When we define the function, we put a placeholder, a **parameter** in there, and then when the foreach loop is called, javascript will slot the appropriate array item value into our parameter variable, whatever we may have called it.

To capture the argument, we simply define the function with a parameter. How do we know that? We can look at the `forEach()` docs on MDN. 

![](@attachment/Clipboard_2020-04-13-18-51-19.png) 4:30 / 7:22

In our case, we chose to name the currentValue parameter `topping`. 

We also have the ability to get the index and the array, so let's take a look at what that looks like. Modify the code like so:

```
function logToppping(topping, index, array){
  console.log(topping,index, array);
}
toppings.forEach(logTopping);
```

When you refresh the HTML page and open the console, you will see that for each item in the array, the actual item was logged, the index and also the original array. 

![](@attachment/Clipboard_2020-04-13-19-54-31.png) 4:52

Why would you need to pass the original array? Because  if you need to grab something from the original array, you can. 

Let's do a quick example where we have to loop over each topping and:
 - log the topping
 - log the next topping if there is one
 - log the previous topping if there is one
 - if it's the last item in the array, log "goodbye"

The first one is easy, you simply add `console.log(topping)`. 

Let's do the next topping. We have the index already and the original array, which we will rename because `array` is a bad parameter name. We also won't name it `toppings` because we already have a `toppings` array that lives outside of this function. Let's rename it to `originalArray` instead so now it's `function logTopping(topping,index,originalArray)`.  

So let's add  `console.log(originalArray[index])` and refresh the HTML page. 

![](@attachment/Clipboard_2020-04-13-20-01-24.png) 6:26

So now if we try adding 1 to the index like so `console.log(originalArray[index + 1])` we should get the next one. 

Let's also add a console.log to break up and see when it's looping. Modify the code like so:


```
function logTopping(topping, index, originalArray){
  console.log(topping);
  console.log(originalArray[index + 1]);
  console.log('--------🍕-----');
}
```

When you refresh the HTML page, you should see the following:

![](@attachment/Clipboard_2020-04-13-20-03-31.png) 6:49

If you scroll all the way to the bottom, you will see that when we get to the last one, the next index returns undefined. 

![](@attachment/Clipboard_2020-04-13-20-04-13.png) 6:57

What we can do to check whether the next topping exists or not is add the following code:

```
const nextTopping = originalArray[index + 1];
if(nextTopping){
  console.log(nextTopping);
}
```

Now if you refresh the page and look at the console, you will see that for the last item, we are not logging the next one because it doesn't exist. 

![](@attachment/Clipboard_2020-04-13-20-05-28.png) 7:22

We can go a bit further and make it a bit easier to understand using a ternary function. 

```
const nextTopping = originalArray[index + 1];
nextTopping ? console.log(nextTopping) : null;
```

That works just the same. Instead of putting null, you could put an empty string, it doesn't matter as long as you put something there. 

Now let's do the previous topping. Let's move the `prevTopping` and `nextTopping` variables to the top of the function and use the ternary operator to console log the previous topping like so:

```
const nextTopping = originalArray[index + 1];
const prevTopping = originalArray[index - 1];

prevTopping ? console.log(prevTopping) : null;
nextTopping ? console.log(nextTopping) : null;
 console.log('--------🍕-----');
```

![](@attachment/Clipboard_2020-04-13-20-09-22.png) 8:25

Now the first and last topping should only have two items logged while all the other items have three items logged.

Next if it's the last item in the array we need to log "goodbye". How can we do that? 

Let's use `.length` on the array and a ternary statement. 

```
index === array.length - 1 ? console.log('Goodbye') : console.log("getting the next topping");
```

![](@attachment/Clipboard_2020-04-13-20-11-27.png) 9:21

Let's break down what we did exactly in that last example. Sometimes it helps to make it more readable if you put part on it's own line like so:

```
index === originalArray.length - 1
? console.log("Goodbye")
: console.log('Getting the next topping');
```

So the condition we are checking is `index === originalArray.length - 1`. We also have access to the index of the currrent item in the `index` variable, and we can get the index of the last item in the array by doing `originalArray.length - 1`. So all this line does is check whether the current index matches the last index. 

If it does, we log "goodbye" and if it doesn't, we log "getting the next topping". 

You could use an if statement instead of the ternary statement, it would work just as well.

We can also use the && hack we learned about earlier. We can say

```
index === originalArray.length && console.log('Goodbye');
```

Why does that work? Because if the first statement is true, it will keep going for the next one and if it is false, it will shortcircuit and never get to the second one. That is what we referred to as abusing conditionals in our previous videos.

That wraps up the `forEach` method. It is a bit different than the other looping methods because it doesn't return any values. Notice how when we loop over each of our items we don't store our results in a variable like below

```
const result = toppings.forEach(logTopping);
```

When you loop over an array with `forEach` it doesn't actually return anything to you. It goes off and does some work for every item that is in that array. 

Let's see how that is different from what Wes likes to call the 'Big Three' which are: 
- Map
- Filter
- Reduce

---

## 50 - 



