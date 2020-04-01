---
attachments: [Clipboard_2020-03-10-07-05-03.png, Clipboard_2020-03-10-07-05-06.png, Clipboard_2020-03-10-07-10-48.png, Clipboard_2020-03-10-19-08-05.png, Clipboard_2020-03-11-07-21-59.png, Clipboard_2020-03-11-07-24-38.png, Clipboard_2020-03-12-07-50-13.png, Clipboard_2020-03-12-19-05-43 (2).png, Clipboard_2020-03-12-19-12-10 (2).png, Clipboard_2020-03-12-19-17-45 (2).png, Clipboard_2020-03-12-19-18-25 (2).png, Clipboard_2020-03-12-20-25-30 (2).png, Clipboard_2020-03-12-20-26-56 (2).png, Clipboard_2020-03-13-09-27-49.png, Clipboard_2020-03-13-09-34-29.png, Clipboard_2020-03-13-09-35-10.png, Clipboard_2020-03-13-15-48-52.png, Clipboard_2020-03-13-16-04-27.png, Clipboard_2020-03-13-16-06-38.png, Clipboard_2020-03-28-18-26-22.png, Clipboard_2020-03-28-18-30-16.png, Clipboard_2020-03-30-20-43-56.png, Clipboard_2020-03-30-20-48-20.png, Clipboard_2020-03-30-20-51-22.png, Clipboard_2020-03-30-20-53-01.png, Clipboard_2020-03-30-20-55-34.png, Clipboard_2020-03-30-21-27-45.png, Clipboard_2020-03-31-18-20-36.png, Clipboard_2020-03-31-18-30-38.png, Clipboard_2020-03-31-18-33-04.png, Clipboard_2020-03-31-18-33-06.png, Clipboard_2020-04-01-18-49-14.png, Clipboard_2020-04-01-18-52-02.png, Clipboard_2020-04-01-18-55-27.png, Clipboard_2020-04-01-19-08-06.png, Clipboard_2020-04-01-19-14-22.png, Clipboard_2020-04-01-19-15-41.png, Clipboard_2020-04-01-19-22-05.png]
title: 'Module 7: Logic and Flow Control'
created: '2020-03-10T11:02:14.437Z'
modified: '2020-04-01T23:26:26.079Z'
---

# Module 7: Logic and Flow Control

## 37 - BEDMAS

If you know what BEDMAS is, skip this video.

![](@attachment/Clipboard_2020-03-10-07-05-06.png) 00:43

This video will be covering BEDMAS And the order of operations in which javascript runs. It is exactly the same as how mathimeticans use it. 

The order in which things run is that things in brackets go first, then we do exponents (which is sort of like the power of). 

We do have exponents in javascript. That looks like `2 ** 2` which is the equivalent of 2 to the power of 2.  `2 ** 10` is 2 to the power of 10.

Next is division, multiplication, addition and subtraction. 

Why is that useful? Open up `bedmas.html` and in the script tag, let's say we have the following..

```
const age = 10 * 5 - 2;
```

That evaluates to 48. Why? First we look for brackets -- there are none, then we move onto exponents, which there are also none of. We go to multiplication next, so 10 * 5 = 50 and then comes addition and subtraction so 50 - 2 = 48. 

Now what if we do..

```
const age2 = 10 * (5-2);
```

So first we evaluate what is in the brackets (5-2 = 3). Then we do exponents (there are none), and next comes multiplication so 10 * 3 = 30. 

This is useful in things like our `calculateBill()` function from previous lessons. 

![](@attachment/Clipboard_2020-03-10-07-10-48.png) 2:51

What is happening there is that all of the functions (`calculateBill(100)`, `calculateBill(20)`, `calculateBill(15)`) run first and equate to a value. 

So the `total` variable declaration is actuall evaluating the following:

`const total = 128 + (25.6 - 19.2)`

Because `calculateBill(100)` = 128 and `calculateBill(20)` = 25.6 and `calculateBill(15)` = 19.2

So in this case, the subtraction happens first (25.6 - 19.2) and then it's added to 128. 

That is order of operations. Next we will get into logic and flow control. If statements, truthy or falsy, equality using and and or, ternarry, switch statements, timers and intervals. 

--- 

## 38 - Flow Control - If Statements, Function Returns, Turthy, Falsy

If statements are the foundation of all logic in javascript. They expect Booleans, which are always either true or false, or they expect some sort of condition that is evaluated to true or false or truthy and falsy. 

First we will explain the mechanics of if statements using greater or less than operators firts, and the we will get deeper into other operators shortly.

At it's most basic, we have an if statement that looks like the following:

```
if( 10 > 2){
  console.log('Yep');
}
```

That is saying if 10 is greater than 2, console log "Yep". 

`if(10>2){console.log('Yep`);}` is the if statement. 

`(10 > 2)` is what is referred to as the **condition**. The condition is going to be evaluated to true or false. By evaluated, what we mean is that if you were to run that in the console (10 > 2) it would evaluate to true or false. 

There are the curly brackets which are opening and closing the block `{}`. Any code that needs to happen when the condition is true need to go within the block. 

We can also add an else if like so:

```
if( 10 > 2 ){
  console.log('Yep');
}
else if( 11 > 10){
  console.log('Yep')
}
```
You can also chain these else ifs as many times as you want. However, if the first one is true, even if the later ones are also true, they will never run. 

```
if( 10 > 2 ){
  console.log('Yep');
}
else if( 11 > 10){
  console.log('Yep')
}
else if (3 > 1) {
  console.log('Yep');
}
```

Although all three conditions above are true, the second and third blocks will never run because the first condition evaluates to true and runs. An if statement will look for the first condition that evaluates to true and then it only runs that block, it will skip the rest. 

If you wish to check for whether multiple things are true, you'd have to have three separate if statements rather than one big if else statement, like so:

```
if( 10 > 2 ){
  console.log('Yep');
}
if( 11 > 10){
  console.log('Yep')
}
if (3 > 1) {
  console.log('Yep');
}
```

Additionally, if nothing is matched, you can chain a `else{}` onto the if statment like so:

```
if ( age > 70){
  console.log('In your seventies');
}
else if ( age > 60){
  console.log('In your sixties');
}
else if (age > 50){
  console.log('In your 50s');
}
else {
  console.log("nothing was true");
}
```

"nothing was true" will be logge if age is less than 50. 

Notice that the `else` statement does not have parenthesis () like the if and else if statements. That is because else never has a condition. It is a catch all which runs if none of the conditions are true. It's similar to the default that we learne about in the switch statement. 

Let's say we take the following code :

```
const age = 100;
if ( age > 70){
  console.log('In your seventies');
}
else if ( age > 60){
  console.log('In your sixties');
}
else if (age > 50){
  console.log('In your 50s');
}
else {
  console.log("nothing was true");
}

```

If you run that in the console, what would you see? You should see "in your seventies". 

![](@attachment/Clipboard_2020-03-10-19-08-05.png) 4:39

Even though that the rest of the conditions are true, because the first condition is true, none of the other conditions are evaluated or run. That is important to keep in mind if you're working with multiple things that could be true. You need to be aware of the order of which you check your if statements. 

Now we will talk about if statements inside of a function, which is likely something you will come across and use to return different values. 

```
  function slugify(sentence, lowercase) {
      if(lowercase){
        return sentence.replace(/\s/g, '-').toLowercase();
      }
      else {
        return sentence.replace(/\s/g, '-');
      }
    }
```

We have this slugify function, which takes in a sentence and then takes in a Boolean, which is either going to be true of false based on whether we should lowercase it or not, and then we return that sentence but we call the .replace() method on it. 

You may be wondering about this line of code:

```
sentence.replace(/\s/g, '-').toLowercase();
```

This is a **regex**, which stands for regular expression. A regular expression is a way to match characters in a string. 

A regex always starts and closes with a forward slash `/` and then you type in different characters. 

In our case, we want to pass the space character which is `\s`. `g` stands for global, which means find them all, not just the first one. Then we replace it with the dash and call toLowercase. 

If you open the html page in a browser and type into the console `slugify('I am very cool')`, it will return "I-am-very-cool".  It puts dashes where spaces were. 

If you were to run that same code but pass a second argument of true, it will lowercase the sentence as well and return "i-am-very-cool". 

Some developers prefer to keep as much logic out of the brackets as possible because if you delete one by accident, it takes a long time to debug. What you can do is simplify the code by getting rid of the else statement and run the code like this: 

```
  function slugify(sentence, lowercase) {
      if(lowercase){
        return sentence.replace(/\s/g, '-').toLowercase();
      }
      return sentence.replace(/\s/g, '-');
    }
```

If you try calling `slugify('I am very cool')` again from the console, it will return the same thing. The reason for that is because of the return keyword within the `if(lowercase)` block. 

What does **return** mean? It means to return a value from a function, and stop that function from running. Whenever you return from a function, even if it's inside of an if statement, that function will stop running and the code that was previously within the else will never be reached. So rather than having an if else, we can have an if and then the else is assumed by putting it after the if condition. This is just personal preference, both approaches are completely valid. 

There is so many different ways we could have coded this functon. This is also a valid approach:


```
  function slugify(sentence, lowercase) {
    let slug  = sentence.replace(/\s/g, '-');
      if(lowercase){
        slug = slug.toLowercase();
      }
      return slug;
    }
```

Here we have assigned the slug variable, then based on the condition (whether lowercase is true or not) we update the slug variable and return it.

You could also do:


```
  function slugify(sentence, lowercase) {
    let slug  = sentence.replace(/\s/g, '-');
      if(lowercase){
        return slug.toLowercase();
      }
      return slug;
    }
```

The last two approaches to this function are better because we don't have to duplicate the regex in two places. 

### Operators

We talked briefly about the different equal signs (`=`, `==`, `===`).

As a refresher.. if you open the html page in the browser and try to type `age = 100;` in the console, you will get an error like the following:

![](@attachment/Clipboard_2020-03-11-07-21-59.png) 9:05

This is erroring out because the single value will set the value into a variable, and this is a const variable which you cannot do. 

If we do `age == 100`, we will get true. That is because double equals will check that the values are the same. So the value of age is 100, and the value of what we are comparing it against is 100. 

The gotcha with the `==` is that if we were comparing it against another value, such as `age == '100'` for example, it will return true because they are technically the same value but they are not the same type.

Using `===` will check if the type of age and the type of the value are the same. 

![](@attachment/Clipboard_2020-03-11-07-24-38.png) 10:02

Because of that, you should almost always use `===`. 

If that is the case, you may be wondering what is the purpose of having `==` in the language at all? Because of null and undefined.

Sometimes you want to check if a variable is null or undefined. 

`null === undefined` will return false.

`null == undefined` will return true.

Although that is the case, Wes has almost never had to use the `==` in his career because of something called **truthy** or **falsy**. 

We also have does not equal which is the bang (`!` is referred to as a bang in programming) and equals sign. 

You would do `name !== 'keith'` for example, which would return false if `name = 'wes'`. 

You could also do `!=`. 

For example 

```
10 !== '10' //returns true
```

```
10 != '10' //returns false
```

That is because 10 and '10' are different types, but the double equals ignores the type. 

We also have greater than and less than. You could check for example if `10 > 10` which would return false. You can do `10 >= 10` which would be true. 

Some people get confused and think you may need to use double equals when comparing greater than or equal or less than or equal (like `10 >== 10`, however that is not correct. Why? Because the greater than and less than operators only ever deal with numbers. So if you accidentally use a string, it will turn the string into a number at first but you shouldn't be doing that. 

Wes always tells people to think of the greater than and less than sign as a hungry aligator. That is how he remembers it. Is the hungry aligator pointed to the largest number? Then that is true. However, if the hungry aligator is pointing to the smaller number than it's false. 

Additionally we have and and or. 

Let's go back to the `if-statements.html` file. Let's say in this function, we also wanted to check if the persons name was scott because that also is a cool name we would use the or operator like so:

```js
if (name === "wes" || name === "scott") {
    console.log("Cool name!");
}
```

The or operator is comprised of two pipes like so: `||`. You would read that code like so:  If the name is equal to wes, OR the name is equal to scott, we console log "cool name". 

Now let's say we also wanted to check if the first name was wes and the last name was bos, then we don't use the or `||`, we use the and `&&` instead, like so: 

```
if(name === 'wes' && last === 'bos'){
  console.log("cool name);
}
```

We can also use BEDMAS here heavily. We can do something like

```
if(name === 'scott' || (name === 'wes' && last === 'bos')){
  console.log('Cool name!);
}
```

What this code will do is it will check the paranethesis. So name must equal scott and last must equal bos, in order for the whole thing to be true. 

![](@attachment/Clipboard_2020-03-12-07-50-13.png) 15:29

When you use the and operator, if any one of the conditions is false, then the entire thing will evaluate to false. Howevevr, when you use the || operator, if any of the conditions are true, it will always be true. 

Next we will talk about using functions with if statements. This is fairly common. 

If you had a string like `'awesome'` and you wanted to check if it contains the word wes you could use `'awesome'.includes('wes')` which would return true. You could also do `awesome.includes('scott')` which would return false. You can use that directly in an if statement like so: 

```
const name = 'wes';
if('awesome'.includes(name)){
  console.log('SUPER COOL AWESOME NAME');
}
```

So pretty often you have methods that return true or false nad pretty often you can use those directly inside. You can also put them in their own variable to make it easier to read like so:

```
const isAwesomeName = 'awesome'.includes(name);
if(isAwesomeName){
  console.log('SUPER COOL NAME");
}
```

Sometimes when you are working with a lot of conditions and a long if statement, it can make the code easier to read and follow if you break it up into multiple variables. 

Similarly we can make our own functions that return true or false and then use it, like in this example:

```
function nameIsAwesome(name){
  return 'awesome'.includes(name);
}
if(nameIsAwesome('wes')){
  console.log('COOL NAME WES');
}
```

Next we have a concept of **truthy** and **falsy**. 

Although Wes has said that if statements require a boolean but that wan't completely true because they will also accept truthy and falsy values.

For example is we do something like: 

```
const dog = 'snickers';
if(dog){
  console.log('You have a dog');
}
else {
  console.log('You don't have a dog');
}
```

If you run that in the browser, you will see "You have a dog" logged in the console.

However, if you were to change the dog variable declaration like so: `const dog = 'snickers'`, what would happen? We see "you don't have a dog"! 

Why is that? An empty string is not true, and it's not false. It's an empty string. So how come that if statement works? That is because if statements will take in number of different values and it will try to coerce them (turn them) into a boolean of true or false. Values that are truthy or falsy will also work. 

So what are examples of values that are truthy or falsy? Here is a list.

### Truthy or Falsy values

 * 0 //falsy
 * 1 //truthy
 * -10 //truthy
 * undefined variable //falsy
 * Variable set to null //falsy
 * a variable set to `"hello" - 10` NaN //falsy
 * empty string //falsy
 * full string //truthy
 * a string of "0" //truthy
 * empty array //truthy
 * empty object //truthy

0 (the number zero) is a falsy value because it will equate to false. Here is a quick example to demonstrate that. 

```
const score = 0;
if(score){
  console.log('There is a score already');
}
else {
  console.log('No score yet');
}
```

If you refresh the html page, you should see "no score yet" in the console. Why? Because zero equates to false. 

![](@attachment/Clipboard_2020-03-12-19-05-43.png) 21:03

1 (the number one) is a truthy value. If we were to change the score variable from the example about to  be `const score = 1;`, you will see "there is a score already" in the console. 

-10 (negative 10) is truthy.  If you change the value of the score to `const score = -10;`, you will be able to demonstrate that. This is because 0 is the only number that is falsy. All other numbers will be truthy. 

If you make score an undefined variable by modifying the code to be `let score;`, you will see that it says no score yet, meaning it's a falsy value. 

Note: We needed to modify the score varibale from a const to a let to make it undefined. Javascript does not support undefined const variables. 

Null is also a falsy value. 

A variable set to "hello" - 10 which would evaluate to NaN (not a number).
![](@attachment/Clipboard_2020-03-12-19-12-10.png) 22:38
Would it be truthy or falsy?  It will be falsy, meaning that NaN is falsy. 

An empty string is falsy. 

A full string is truthy. Any string with content in it will be true. 

A string of "0" is tricky because it's a string with content, but it is also zero and we learned that zero is false. Which is it actually? It is truthy! A string of anything, even a string with just an empty space like so `" "` will be true. Only a completely empty string `""` will be falsy.  

The next two we haveb't really covered yet: an empty array and empty object. 

An array can be shown like this:

```
let score = [1,3,6];
 ```

Would that be truthy or falsy? 

![](@attachment/Clipboard_2020-03-12-19-17-45.png) 24:21

The array with values is truthy. 

What about an array of nothing? will `let score = [];` will it be truthy or falsy?  

![](@attachment/Clipboard_2020-03-12-19-18-25.png) 24:26

An array with no values is truthy. 

If you ever need to check for something in an array, we would look for something called `.length` but we are getting a bit ahead of ourselves. The length is how you tell how many items are in an array. 

The last one is an empty object like so. `let score = {};`. An empty object is still truthy. 

If you want to check if there is anything in the object, you can use something called `Object.keys({})` which will turn it into an array and then you can chain .length on it like so `Object.keys({}).length`. 

We use a whole bunch in javascript which is why you often see if statments with things that you might not think are true or false, but that is simply because we are checking for it's existence (whether it is there or not). 

What we are going to do now is make an array with all of these different values and types and loop over them and show you with an if statement whether they are truthy or falsy.  We haven't gone over arrays yet, but an array is a list of things.  

```
const values = [[], [], -10, 1, 0, "", "full string", " ", undefined, NaN, null];
```
Now we will call `forEach` much like we did when we were working with DOM nodes. 

```
console.group('truthy or falsy values');
values.forEach(value => {
  console.log(value);
})
console.groupEnd('');
```

![](@attachment/Clipboard_2020-03-12-20-25-30.png) 27:41

Then within the foreach block we will add the following:

```
if(value) {
  console.log(value, 'is truthy');
}
else {
  console.log(value, 'is falsy');
}
```

![](@attachment/Clipboard_2020-03-12-20-26-56.png) 28:00


---

## 39 - Coercion, Ternaries and Conditional Abuse (16:00)39. Coercion, Ternaries and Conditional Abuse

Coercion can seem like an intimidating word but it's a pretty simple concept to understand. 

So far, we have learned that if you only need to use bang operator, that checks for the opposite. For exammple, if you wanted to check if someone is not cool, you might think you have to do the following:

```
const isCool = true;
if(isCool){

}
else{
  console.log('You are not cool')'
}
```

So in this situation where we are only ever using the else, that is because you want the opposite of a value. You could have done something like the following:

```
if(!isCool){
  console.log('You are not cool');
}
```

A bang in front of a boolean will always flip it. 
So if `isCool = true`, then `!isCool` would evaluate to false. 

In addition to flipping the boolean to the opposite, it will also does coercion. Coercion is when we force something that is of a different type, such as a string or number, or an object or anything like that. When we take that and cooerce it into a frue boolean. 

Let's do this example. if you type `name` into the console, it should return "wes" (because we assigned that variable in earlier excercises in this javascript file).
If you type `!name` in the console, it should return false. You will notice that `!name` took the string and turned it into a boolean by putting the bang in front of it. 

So when you use the bang, it will coerce the value into a real boolean. 

That is sort of the opposite because if we want to check if there is a name, if we want to take the fact that there is a name and make it into a real boolean, we can put double bang infront of it `!!` and that will coerce it into the simple existence into a Boolean of it exists or not. So `!!name` would return true. 

Here is another example:

Let's say you have a middle variable that is assigneed an empty string, like so `const middle ="";`. 

![](@attachment/Clipboard_2020-03-13-09-27-49.png) 2:45

When we put one bang infront of it, it gave us the opposite which was true. If we put two bangs, it gives us false. So if you ever see the ! and !! being used in the if statments, that is because someone is taking the fact tha tyou have a truthy or falsy value, and you are coercing it into a true boolean. 

Wes used to use that quite a bit, but now that he has a really good understanding of truthy and falsy values, he doesn't use this coercion method much. 

Coercion in general is the act of changing one type into another. 

### Ternary

Next up we have **ternary**. 

Wes likes to think of ternary's as shorthand if statements. They are helpful when you quickly want to run functoinality based on something being true or false. 

A ternary needs three things. 

1. A condition
2. What to do if it' true
3. What to do if it's false. 

For example:

```
const count = 2;
let word;
if(count === 1){
  word = 'item';
}else {
  word = 'items';
}
```

So if you had a sentence that said how many items in your cart for example, you could so something like:

```
const sentence = `You have ${count} ${word} in your cart`;
console.log(sentence);
```

![](@attachment/Clipboard_2020-03-13-09-34-29.png) 5:25 

If you changes the count to be 1, it would return the following sentence:

![](@attachment/Clipboard_2020-03-13-09-35-10.png) 5:26

The if statement that we wrote above is a bit verbose.. you first have to declare an empty variable and then update it so what we can do, if it's a simple if else like in this example, you can turn it into a shorthand if statement with **ternary**. 

Comment out the if statement that we wrote above, because we will be replacing it was a ternary statement. 


Like we mentioned above, for a ternary statement we need one condition, then we need what to do if that condition is true, and what to do if that condition is false. 

That would look like this:
```
const word = count === 1 ? 'item' : 'items';
```

If you run that in the console like so:

```js
const count = 0;
const word = count === 1 ? 'item' : 'items';
const sentence = `You have ${count} ${word} in your cart`;
console.log(sentence);
```

![](@attachment/Clipboard_2020-03-13-15-48-52.png) 6:55

You should see that it works. 

What this does is it puts the if statement where we have our condition (something that will be true or false) (`count === 1`) and then we have what to return if true (`'item'`), and finally what to return if false (`items`). 

That is useful when you need to do a quick if statement. 

We could even take the example above a step further and do the ternary function directly inside of the sentence like so:

```
const count = 0;
const word = count === 1 ? 'item' : 'items';
const sentence = `You have ${count} item${count === 1 ? '' : 's'} in your cart`;
console.log(sentence);
```

What we are doing here is saying if count is equal to 1, return nothing, and if it's not, return "s". That works exactly the same. 

We can also use these for running functions. 

For example, let's say you have a variable like `const isAdmin = true;`.  We can run a function based on if we have it or not, like so: 

```
isAdmin ? showAdminBar() : null;
```

So in that example, if the `isAdmin` variable is set to true, we would show the admin bar, otherwise we would do nothing which is why we are returning null. You could also return an empty string or anything really because it's not saving that variable anywhere, it's just checking if it's true. If it's true, it will run a function. 

It is important to note that both what happens when it's true and when it's false needs to be there for a ternary statement. `isAdmin ? showAdminBar();` would not be valid. You need to supply the false case. 

There is one trick you can do, the **and and trick**.
The neat thing about chaining stuff on conditoins is it will check along the way to make sure that things are true. For example let's say we had three functions and we wanted to make sure that all three functions are true before going ahead we can do an if statement like this:

```
function check1(){
  return true'
}
function check2(){
  return true;
}
function check3(){
  return true;
}

if(check1() && check2() && check3()){
  console.log('all checks passed');
}
```

If you run that in the browser, you will see "all checks passed" logged in the console. 

Now inside each function, add `console.log('Running check 1');` with the corresponding function number (running check 1, running check 2 etc). 

consWhat is cool about this is if you refresh in the console, you will see each one running in order..

![](@attachment/Clipboard_2020-03-13-16-04-27.png) 11:10

Now if we put an else like so, and make one of the checks fail (modify one to return false) like so:

```
function check2(){
  return false;
}
if(check1() && check2() && check3()){
  console.log('all checks passed');
}
else {
  console.log('Some checks failed');
}
```

When you run in the browser you will see the following:

![](@attachment/Clipboard_2020-03-13-16-06-38.png) 11:35

Did the third check never run? yes, that is true. If you run a condition, Javascript will do the following: it will check the first one, and then if it's okay, it will move to the next condition. If that is true, it will go onto the next one. However, if it any point one of them is false, javascript will give up and say that one is false, there is no reason I would keep checking because already know that the first one is false. Therefore it returns the condition as false, the third condition never runs and the else block will run.

That is sometimes referred to in Javascript as shortcircuiting. Meaning that we never finished what we wanted, but we knew it wouldn't work out anyway so we short circuited it and went directly to else. 

The way that works can be abused or used. Some people hate it, some love it. Wes personally likes it. 

Let's go back to the admin example to demonstrate what it can look like:

```
isAdmin ? showAdminBar() : null;
isAdmin && showAdminBar();
```

We can abuse it by using `isAdmin && showAdminBar();`

Javascript wil lsay, this is a condition so we are going to check if the first is true, and if it is true, we will go ahead and do the next one. However if it is false, it won't run `showAdminBar()`. 

This is abusing the condition chaining, meaning that if the first condition is true, the second will never run.  

You see that sort of thing in react because it's a bit hard to do if statements in react. 

You would do something like this React if you wanted to conditionally render the admin bar based on whether the `isAdmin` value is true or false. 

``` 
{isAdmin && <AdminBar/>}
```

### Blockless If Statements

If something is on the same line, you don't actually need the block in the if statement. 

For example, the following if statement is on multiple lines so it needs the `{}` block. 

```
if(isAdmin){
  showAdminBar();
}
```

However, you could refactor it to be on one line like so:

```
if(isAdmin) showAdminBar();
```

However, as soon as it goes onto another line, it is broken, so this would NOT be valid:

```
if(isAdmin)
showAdminBar();
```

Should you use blockless if statements? That is up to you to decide. Wes doesn't use it often but he definitely has in the past because it is very convenient to write one-liners. In most cases however Wes will use the blocks just in case someone else accidentally moves the if statement to multiple lines and breaks it. 

---

## 40 - Case Switch and Animating a Turtle with CSS Variables

We are going to talk about switch statements now. We already used a switch statement in our etch-a-sketch exercise. 

In this video we will go over them again and this time do an example where we animate a turtle. 

Open up `switch-statements.html` which is in the `/playground` folder.

Add an img tag like so:

```
<img src="./turtle.png" alt="Turt" class="turt">
```

Now add a script tag and within that script tag grab the turtle and console log it: 

```
<script>
  const turtle = document.querySelector(".turt");
  console.log(turtle);
</script>
```

It's a bit big so let's add `wdith="200"` to the image element. 

You should see the following when you load the html page:

![](@attachment/Clipboard_2020-03-28-18-30-16.png) 1:11

We want to make this turtle walk, and make it flip around when we hit the arrow keys.

First thing we will do is listen for the key down. What we will do is make a function called `handleKeyDown` which we will pass to the keydown event listener. 

In the handleKeyDown function, we will grab the event and console.log the event key like so:

```
function handleKeyDown(event) {
      console.log(event.key);
}
window.addEventListener("keydown", handleKeyDown);
```

We only care if it's an arrow key or not, so we will add code to check if the event key includes the word arrow and if it does not, we will just return which will exit out of the function like so:

```
if (!event.key.includes("Arrow")) { return; }
console.log(event.key);
```

If you refresh the html page and hit any key, you will see only the arrow keys are logged. That is because we are returning if the key is anything but an arrow key before logging.

So now we want to make the turtle move. Let's add declare two variables, x and y, right before the handleKeyDown variable and set both to zero.

```
 let x = 0;
 let y = 0;
 function handleKeyDown(event) {
    if (!event.key.includes("Arrow")) { return; }
```

Now within handleKeyDown, when they move right, we will decrease the x and vice versa. This is a use case for a switch statement. 

The way a switch works is you write `switch` and then you pass it the thing you are testing, so we will switch on the `event.key`. 

Then we have a block which will contain a whole bunch of different cases. This is a bit easier to look at than an if statment in some cases. The only downside is that they have to be clearly defined cases. There is no case like greater than 20, that is an if statement. 

```
  switch(event.key){
    case 'ArrowUp':
      y = y-1;
    case 'ArrowDown':
      y = y + 1;
    case 'ArrowLeft':
      x =  x + 1;
    case 'ArrowRight':
      x = x - 1;
  }
```

Note: You might notice that prettier isn't autofixing on save. That is because we are writing javascript within an html file. 

For each of the cases above, we need to add a break. If you do not break, then it will keep going down to each of the cases which will cause trouble. So in a switch statement you must always break after each of your cases. 

You should also always have a default case which will run if the condition doesn't match any of the cases. 

```
 switch(event.key){
    case 'ArrowUp':
      y = y-1;
      break;
    case 'ArrowDown':
      y = y + 1;
      break;
    case 'ArrowLeft':
      x =  x + 1;
      break;
    case 'ArrowRight':
      x = x - 1;
      break;
    default:
      console.log("That is not a valid move");
      break;
  }
```

Now that we have those variables, lets take the turtle and move him over. After the switch, let's add a `console.log(x,y)` and then refresh the html page, open the console and hit some of the arrow keys. 

![](@attachment/Clipboard_2020-03-30-20-43-56.png) 5:25

Oops! We made a mistake. In our switch statement, arrowleft should be `x = x -1;` and arrwRight should be ` x = x + 1`. 

```
case "ArrowLeft":
  x = x - 1;
  break;
case "ArrowRight":
  x = x + 1;
  break;
```

Modify the switch statements and try again. 

Now when you hit the up down left and right keys you should see the x and y variables changing in the console. 

![](@attachment/Clipboard_2020-03-30-20-48-20.png) 5:38

Now we need to convey the x and y values to the turtle somehow. 

What we are going to do is we are going to do this via css variables. Let's add a style tag right after the opening body tag. Grab the turtle class and add the following:

```html
<body>
    <style>
      .turt {
        position: relative;
        transform: translateX(10px) translateY(10px);
      }
    </style>
```

In the dev tools, if you manipulate the values of `translateX` and `translateY`, you will see that the turtle moves. 

![](@attachment/Clipboard_2020-03-30-20-51-22.png) 6:46

Now we are going to take those variables and put them into their own css variables like so:

```
 <style>
      .turt {
        position: relative;
        --x: 10px;
        --y: 10px;
        transform: translateX(var(--x)) translateY(var(--y));
      }
    </style>
```

Now if you modify the x or y variable values in the console, you will see that the turtle moves fine,. 

![](@attachment/Clipboard_2020-03-30-20-53-01.png) 7:21

Next we are going to update the x and y css variables with javascript. 

After the switch statement, we will grab our turtle and apply styles directly to it. 

```
turtle.style.background = 'red';
```

If you refresh the page and hit an arrow, you should see the following: 

![](@attachment/Clipboard_2020-03-30-20-55-34.png) 8:03

So if we want to apply a variable, we can't just do `turtle.style--x`. Instead we have to use what is called **square bracket notation**. We haven't looked at this yet, but we will get into it more when we look at arrays and objects.

For now, know that you can also access a property in two ways. 
One way is `turtle.style.background` while the other is `turtle.style['background']`. 

When you use the square bracket notation, you pass it a string. Those two ways are exactly the same. 

Let's try using the second approach to set our x and y css variables like so:

```
turtle.style["--x"] = `${x}px`;
turtle.style["--y"] = `${y}px`;
```

If you refresh the page and try hitting some arrow keys, you will notice that it does not work. 
That might be because css variables are not standard css attributes.

So let's say you also set a value for the css property "madeup" which doesn't exist. If you added the code `turtle.style['madeup'] = 'green';`, you will notice that it doesn't show up in the style tag. That is because only real css properties will be added.

So how do we apply custom CSS properties if it is not? We can reach for `setAttribute` which we were looking at before.

```
turtle.setAttribute("style", `--x: ${x}px; --y: ${y}px`);
```

Now if you refresh the HTML page and hit the arrow keys, you will notice that the turtle moves up down and left and right.

Let's set the x and y css variables to default at 0 instead of 10px. 

One other thing we could have is like a speed operator. Declare a speed variable in the javascritp code after the x and y variable declarations like so: 

`let speed = 5`; 

Now we will modify the code which updates the x and y valeus to multiple them by speed like so:

```
  turtle.setAttribute('style', `--x: ${x * speed}px; --y: ${y * speed}px`);
```

You will notice that now the turtle moves much more quickly.

We can also add a css transition, to make the turtle move a bit more smoothly. Add the following:

```html
...
     transition: transform 0.2s;
      }
    </style>
```

Feel free to increase the speed value to make the turtle go even faster. Wes set his to 50!

The last thing we are going to do is flip the turtle. So when we press the left arrow key, the turtle should be facing the other way. 

Let's add a javascript variable called flipped and set it to false like so: 

`let flipped = false;`

Now within the `ArrowLeft` switch statement, add `flipped=true;` before the break. When we hit the `ArrowRight` case, we will set `flipped = false;`. 

So to flip the turtle, we will go into the css transform and we will `rotateY` to flip the turtle.

In the css, we will add another variable called `--rotate: 0`. 

We will modfy the transform like so: 

```
--rotate: 0;
transform: rotateY(var(--rotate)) translateX(var(--x)) translateY(var(--y));
```

Now further down where we use setAttribute, we will modify the code like so. Note: because we are using backticks, we can move each variable to it's own line like so:

```
turtle.setAttribute('style',`
          --rotate: ${flipped ? '180deg': '0'}
          --x: ${x * speed}px; 
          --y: ${y * speed}px;
          `);
```

You might notice it looks a bit weird when we flip it. That is because we are rotating it before we move it. Let's modify the transform to move the rotateY to the end of the transform. The order there matters!

```
transform:  translateX(var(--x)) translateY(var(--y)) rotateY(var(--rotate));
```

Now when you hit the left arrow, the turtle should look left like so: 

![](@attachment/Clipboard_2020-03-30-21-27-45.png) 14:43

We could also rotate the turtle up and down. 

Let's modify the css rotate variable from `rotate` to `rotateX`. Modify that everywhere it's called in the code.

We will have another variable called `rotate` which we will set to 0. 

Modify the transform to take that variable like so:

```
<style>
      .turt {
        position: relative;
        --x: 0px;
        --y: 0px;
        --rotateX: 0;
        --rotate: 0;
        transform: translateX(var(--x)) translateY(var(--y))
          rotateY(var(--rotateX)) rotate(var(--rotate));
        transition: transform 0.2s;
      }
    </style>
```

We know that when we set `rotate(90)` , the turtle is pointing down, and when we do `rotate(-90)`, the turtle is going up. So we need another variable like flipped to keep track of that. Add a javascript variable called `rotate` and set it to 0. 

`let rotate = 0;`

In the `ArrowUp` case, add `rotate = -90`. In the `ArrowDown` case, add `rotate = 90;`. For `ArrowLeft` and `ArrowRight` we will set rotate to 0. 

Finally modify the setAttribute statement to update the rotate variable like so:

```

turtle.setAttribute('style', `
  --rotateX: ${flipped ? '180deg' : '0'};
  --x: ${x * speed}px;
  --y: ${y * speed}px;
  --rotate: ${rotate}deg;
`);
```

Now when you hit the arrow keys left, right, up and down the turtle should be facing in that direction and also move in that direction. 

---

## 41 - Intervals and Timers

In this video we will talk about timeouts and intervals. If you want to run something after 5 seconds, we would use a timeout. If you want to run something every 5 seconds, you would use an interval. They both work exactly the same way and we will dive into them both now.

So we have the `intervals.html` file which is in the `/playgrounds` folder. 

Add a script tag within the body tag. 

Now when you want to run something, you simply type `setTImeout`, which takes a couple of arguments. 

Where did `setTimeout()` come from anyway? Is that just a function that is available to us? The answer is yes. It is a globally scoped method. It is actually `window.setTimeout()` but as we will learn, we don't need to type window. when you are accessingly globally available APIs. 

Wes recommends now using window.setTimeout() and that is because you often want to run the same code you ran in the browser in node.js and node.js does not have a concept of a window. It does have timeout and interval however. 

`setTimeout` takes two things: a callback, and the number of miliseconds after which to run the callback. 

Often what you see is someone give setTImeout an anonymous function as the first argument, and then the number of miliseconds that it should run the anonymous function after. For example if you put 500 miliseconds, the function will run half a second after the javascript has started. 

Just in like `addEventListener, you can either pass in an anonymous function, or you can write a function outside of it. 

Create a function called buzzer that console logs ENNNGGG! as the buzzer sound. Now in the set timeout, instead of passing the anonymous function let's pass it a reference to the buzzer function instead, like so:

```js
function buzzer() {
  console.log("ENNNNGGGG");
}
setTimeout(buzzer, 500);
```

Now if you refresh the html page, you shoudl see ENNNNGG in the console after half a second. 

Let's try something to demonstate one interesting thing about timers. 

Modify the code like so:

```
function buzzer() {
  console.log("ENNNNGGGG");
}

console.log("Starting");
setTimeout(buzzer, 500);
console.log("Finishing!");
```

what is going to happen here? We are going to console log starting, wait for half a second and then do finishing?

Let's refresh the html page and see. 

![](@attachment/Clipboard_2020-03-31-18-20-36.png) 2:45

So what is happening there? The javascript will run, it will console log starting, set off the timer, queue it up which is basically saying "Ok I have this function called buzzer which I am going to run after 500 miliseconds, but I've got stuff to do so I'm going to keep going", so it moves on to the next line of code which is console logging "finishing". 

That is what is referred to as the **asynchronous** nature of JavaScript. 

As soon as it queues up the buzzer to be run after 500 miliseconds, it will go off onto the next line of code, and only come back to buzzer when it's time. That is why we call it a callback. Because we come back and call it at a later point in time. 

So that is good to know that even if you are trying to wait for 500 miliseconds, the rest of javascript will keep on running. 

Now, when we get into promises and async await, I will show you how to actually do that.  It is a pretty common thing to want to wait a couple of miliseconds before doing something. 

### Intervals 

Intervals work exactly the same. You write `setInterval()` and then it takes two arguments. You pass it a reference to a function like buzzer, and how often you'd like to run it, so let's say everyone 100 miliseconds you would write the following:

```
 setInterval(buzzer, 100);
```

![](@attachment/Clipboard_2020-03-31-18-30-38.png) 4:05

That will result in the interval running every 100 miliseconds.

There is one gotcha with intervals. 

Lets say you were using intervals to animate somethihng every 2 seconds or to check something every two seconds. 

What happens is that it doesn't actually run immediately. It only runs after the first 2 seconds have elapsed. There is no option to tell the interval to run right away, but also run again after two seconds. 

If we do want that sort of functionality, we can code our own interval. Let's create a function called `setImmediateInterval()` which will take two arguments: the function to run, and the number of miliseconds. 

```
function setImmediateInterval(funcToRun, ms) {
}

```

Within that function, we will call the function that is being passed as a argument right away. like so:

```
function setImmediateInterval(funcToRun, ms) {
    // right away call that function
    funcToRun();
}
```

If you are confused about where `funcToRun()` came from, don't worry, Wes will go over that again shortly. 

Next we will run a regular interval right after we call `funcToRun();` and we will pass the interval the arguments we received in `setImmediateInterval` which were the function to run on the interval, and how many seconds to wait before running the function. 

```js
function setImmediateInterval(funcToRun, ms) {
  // right away call that function
  funcToRun();
  setInterval(funcToRun, ms);
}
```

We are actually going to return `setInterval` so modify that line of code to be `return setInterval(funcToRun, ms);` instead. Wes will explain later why we added the return keyword, it has to do with stopping intervals from running. 

Now what we can do now is replace the code that we added earlier that was `setInterval(buzzer, 2000)` to instead be `setImmediateInterval(buzzer, 2000)`. 

```html
<script>
  function buzzer() {
    console.log("ENNNNGGGG");
  }
  console.log("Starting");
  setTimeout(buzzer, 500);
  console.log("Finishing!");

  function setImmediateInterval(funcToRun, ms) {
    // right away call that function
    funcToRun();
    return setInterval(funcToRun, ms);
  }

  setImmediateInterval(buzzer, 2000);
</script>
```

Now if you refresh the HTML page and open the console, you will notice ENGGG is immediately logged and then again after 2 seconds. 

Now we mentioned earlier that you might be a bit confused about where `funcToRun` came from. We have gone over this before but it's a big tripping point for people so we will go over it again. 

![](@attachment/Clipboard_2020-04-01-18-49-14.png) 6:16

In this scenario, we made a function (`setImmediateInterval()`) which takes a parameter of another function.

If you have a function and one of the arguments you pass is a function, it works exactly the same as when you are passing a number or a string. 

So in this instance, we just take the function that was passed in as an argument and we call it. 

![](@attachment/Clipboard_2020-04-01-18-52-02.png) 6:44

In the line of code above, we are passing the function buzzer as an argument to `setImmediateInterval`. 

Let's say we had another function called `sayHi`, which console logged "heyyy". We could call `setImmediateInterval` and pass it sayHi and an milisecond value of 200, like so:

```
setImmediateInterval(buzzer, 2000);
function sayHi() {
  console.log("Heeeyy");
}
setImmediateInterval(sayHi, 200);
```

If you refresh the HTML page and open the console, you will see something like this:

![](@attachment/Clipboard_2020-04-01-18-55-27.png) 7:05

So in both examples, Wes is passing a function and whenever it's called, it gets transformed into the parameter called funcToRun. We then have access to either run it, or pass it even one level further into our `setInterval()`. 

So timeouts and intervals are pretty straightforward. The biggest gotcha is that intervals will not run immediately, but as we saw, you can code your own function for that. 

The only other thing we need to know is if you want to clear a timer or interval, you must save the reference to that timer or interval. 

Let's do an example to demonstrate that. Let's first comment out all the code currently running timers or intervals. 

Next, let's make a function called `destroy()`, which runs after 5 seconds f someone doesn't click anywhere on the page and will destroy the webpage.  Let's set a timer to run destroy after two seconds.  

```
function destroy() {
  document.body.innerHTML = `<p>DESTROYED</p>`;
}

setTimeout(destroy, 2000);
```

If you refresh the page, you will see the text "DESTROYED" displayed after two seconds. 

![](@attachment/Clipboard_2020-04-01-19-08-06.png) 8:38

Now that it obviously not that intertesting, but you can imagine some scenario where something like this might happen like you have to hit the save button within an allotted period of time. 

Now what if we make the setTimeout to be 5 seconds and then we say if someone doesn't click within 5 seconds, we will run it, but if they do click within 5 seconds, we want to clear it. 

What we can do is add a click event listener on the window like so: 

```
  window.addEventListener("click", function() {
        console.log("You clicked! You saved the world!");
        // How do you stop the timer from running?!
      });
```

The question is how do we stop the timer from running? Well, what you can do is save reference to the timer when declaring it like so:

`const bombTimer = setTimeout(destroy, 5000);`

If you were to `console.log(bombTimer)`, what are we going to get? 

![](@attachment/Clipboard_2020-04-01-19-14-22.png) 9:49

You will see 2 in the console. What is this 2?? Well 2 is just a reference to all the current timers that are on the page. So to us it doesn't mean anything, but to the browser it does. 

If you were to look at the typeof when console logging our reference to bomb timer like so, you will see that it's just a regular number

```
console.log(typeof bombTimer);
```

![](@attachment/Clipboard_2020-04-01-19-15-41.png) 10:07

But if we save reference to that timer number in a variable, we can later call `clearTimeout()` and pass it a reference to that timer and what that will do is it will stop the timer from running. 

```
const bombTimer = setTimeout(destroy, 5000);

window.addEventListener("click", function() {
  console.log("You clicked! You saved the world!");
  // How do you stop the timer from running?!
  clearTimeout(bombTimer); // STOP THE TIMER FROM RUNNING
});
```

Now if you refresh the page, if you don't click anywhere for 5 seconds, you will see the destroy text. However, if you do click within the first 5 seconds, the page will never be destroyed. 

If for any reason you need to stop your timer, save reference to it in a variable. There is no other way to clear the timer other than having a saved reference to it in a variable which is a number. 

The intervals work exactly the same way. 

Let's create an interval that console logs the poop emoji and hehehe every 10 miliseconds like so:

```
setInterval(function() {
  console.log(`💩`);
  console.log("Hehehe");
}, 10);
```
If you refresh the HTML page and look at htte console, you will see tons of console logs. 

![](@attachment/Clipboard_2020-04-01-19-22-05.png) 11:33

Now if we wanted to clear that, we could save reference to it and then call `clearInterval()` and pass it the reference. 

```
  const poopInterval = setInterval(function() {
      console.log(`💩`);
      console.log("Hehehe");
    }, 10);
```

If you refresh the page and open the console, you can type into the console `clearInterval(poopInterval)` and that should stop the interval from running. 

One thing Wes often likes to do is run the interval every 100 miliseconds, but after 3 seconds we want to stop it entirely. 

If we wanted to clear that after five seconds, we could simply make a setTimeout that you pass an anonymous function that called clearInterval(poopInterval) after 3 seconds like so: 

```
setTimeout(function() {
  clearInterval(poopInterval);
}, 3000);
```

If you refresh the page, you will see the console logs stop after 3 seconds because we have cleared it. 

--- 


