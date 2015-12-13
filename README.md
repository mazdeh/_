# _
# An Introduction to Underscore.JS

If you're a JavaScript developer and have experience with Ruby or Python, or languages alike, you crave some sort of a utility library for your front end JS code -- well that's precisely what Underscore will do for you.

JavaScript is fairly boring when it comes to low level utilities such as `map`, `filter` `select` that you see in other languages -- and Underscore introduces over a 100 helper functions, without extending the built-in JavaScript objects, to give developers the opportunity to implement more complex front ends.

Underscore works across all browsers, and is super fast and efficient.


# Setup
Depending on what kind of a project you're working on, there would be different ways to include Underscore in your project. Sine my examples in this tutorial will be farily simple and I will not be needing a complex front end or a backend, I am going to just download the source from [here](underscorejs.org). You can also download the file `underscore.js` in this repo and include it in your directory.


To get things started, create a `index.html` file and include the underscore.js file in the `<head>`. Like below:
```html
<head>
<script src="underscore.js"></script>
</head>
```

Now after the closing `<body>` tag, inside a `<script>` tag, we'll be experimenting with underscore a little bit.

## Categories
Underscore's functionalities fall into 5 general categories:

1. Collections
2. Arrays
3. Objects
4. Functions
5. Utilities

I'll be providing a couple examples for each of the different categories.

# Collections (Arrays or Objects)
Let's say we have an array of strings like:
```js
var fruits = ['banana', 'apple', 'strawberry', 'blackberry', 'mango'];
```

### select
Now say we want to pick out all the fruit that have more than 5 characters from the `fruit` array.

Below is how we'd do it if we didn't know about underscore, in pure JavaScript:
```js
var minLength = 5, fruitFive = [];

for (i = 0; i <= fruit.length; i++) {
	if (fruits[i].length > 5) {
		fruitFive.push(fruit[i]);
	}
}

console.log(fruitFive);
```

A very simple blob of JS. Now see how Underscore would go about doing this:
```js
var minLength = 5, fruitFive = [];

fruitFive = _.select(fruits, function(fruit) { return fruit.length > minLength;});

console.log(fruitFive); // logs banana, strawberry, blackberry
```

As a developer that line makes my heart tingle a little bit. It is so elegant and nice. This is what Underscore is about -- and a lot more.


### each
Say you want to go through a list, or an array, applying a function to each of its elements -- you could simply use:
```js
_.each(fruits, function(fruit) {
	console.log(fruit);
}
```


# Arrays
JS does not have a good collection of built in array functions. Here are a few Underscore functions specifically for arrays.

### uniq
Wouldn't be amazing if JS provided a function that would get rid of all the duplicates in an array? Well, check this out:
```js
var nums = [1, 1, 2, 3, 4, 5, 5, 5, 4, 7, 10, 10, 10];
var unique = _.uniq(nums);

console.log(unique); // [1, 2, 3, 4, 5, 7, 10]
```

This is probably my favorite. And the great thing about `uniq` is that it keeps the original order of the array!

### range
The `range` function is very similar to that of Python - if you're familiar with that. Here's the structure:
```js
_.range = function(start, stop, step);
```

Pretty straightforward -- `start` is your starting number in the range. `stop` is the max number you want to go to, and `step` is how far apart you want each of the numbers in your range.

Here's a simple example:
```js
var fiver = _.range(10, 30, 5);
console.log(fiver); // [10, 15, 20, 25]
```

Keep in mind that the `start` and `stop` numbers are included in the range.

### rest
Also very handy -- return sthe rest of the elements in an array. Pass in an index to rest, and it will return the elements in the array from that index onward.

Here's an example:
```js
var array = [1, 2, 3, 4, 5, 6, 7, 8];

var restArray = _.rest(array, 3);
console.log(restArray); // [4, 5, 6, 7, 8]
```

### without
Pass in what you want removed from the array, and it returns a copy of the array with all those values removed.

```js
var without = _.without(array, 1, 5, 8);
console.log(without); // [2, 3, 4, 6, 7]
```

# Objects

### keys
Trying to iterate through an object and get all of the keys?
```js
var obj = {firstName: 'Vahid', lastName: 'Mazdeh', age: 23};

var keys = _.keys(obj);
console.log('_.keys example:', keys); // ["firstName", "lastName", "age"]
```

`keys` returns an array of the enumerable keys in the object.

You can get the values in an object in the same manner, but using `_.values(object)` instead.

### invert
Maybe not as frequently used, but a very powerful and cool function I think.
It returns a copy of the object where the keys have become the values, and the values the keys. For it to work, all the values in object should be unique and string serializable.
```js
var obj = {firstName: 'Vahid', lastName: 'Mazdeh', age: 23};

var inverted = _.invert(obj);
console.log('_.invert example:', inverted); // Object {23: "age", Vahid: "firstName", Mazdeh: "lastName"}
```

### extend
More useful than the previous.
`_.extend(destination, source)` It copies all the properties in the `source` object over to the `destination` object, and returns `destination`
```js
var destination = {firstName: 'Vahid', lastName: 'Mazdeh', age: 23};

var source = {homeTown: 'Boulder, CO'};

var extended = _.extend(destination, source);
console.log('_.extend example:', extended); // Object {firstName: "Vahid", lastName: "Mazdeh", age: 23, homeTown: "Boulder, CO"}
```

### defaults
Very useful when you need all your objects to have the same properties and default to certain values.

Here's an example:
```js
var objOne = {firstName: 'Vahid', lastName: 'Mazdeh', age: 23};

var defaults = {homeTown: 'Boulder, CO', occupation: 'Software Developer'};

_.defaults(objOne, defaults);
console.log('_.defaults example:', objOne); // Object {firstName: "Vahid", lastName: "Mazdeh", age: 23, homeTown: "Boulder, CO", occupation: "Software Developer"}
```

# Utilities
### template
The most important and useful of Underscore's utility functions is `template`. There are so many templating utilities out there, but none is as powerful and as small as Underscores.

`template` is great for when you have a lot of JSON that you need to calculate and render within the HTML.


It compiles JavaScript templates into functions that can be evaluated for rendering. 

Useful for rendering complicated bits of HTML from JSON data sources. 

To get a better idea of what we can do with the `template` utility function add the below code to a simple index.html file, inside the `<body>` tag:
```html
<h3>
</h3>

<script type="text/template" id="gooz">
	<h3>Hello <span style="color: green;"><%= data.firstName %></span>. Welcome to the Underscore.js Tutorial!</h3>
</script>
```

Underscore templates inside the html go inside a script tag, like above. We give the script tag an ID, so that we can grab it using jQuery later on, to resolve the template with our data.

Note: Make sure you include jQuery in your index file, or else this example will not work.

Now, inside a script tag after the closing `<body>` tag, we're going to resolve the template we just created, with the `_.template` utility funciton.

```js
data = {firstName: 'Prof. Anderson'};

var template = _.template($("#gooz").html());
$("h3").html(template);
```

Note: We are using jQuery to grab the underscor template within our html. Then we replace the `html()` of that empty `<h3>` tag with the resolved template data.


Templates can be used to inject values from a JSON file into the HTML, or to run some JavaScript code within the HTML, using `<% ... %>`. Your JS code inside these delimiters will be excuted and rendered inside the HTML.



### random
Works like the random function in Python. Returns a random integer between `min` and `max`.
```js
_.random(min, max);
```
Example:
```js
console.log(_.random(10, 700));
```


# Functions
Functions work on functions. This is a little more complicated, so let's take a look at an example.

### bind
Create a function bound to a given object (assigning `this`, and arguments, optionally).

```js
var context = { prefix: "Dr." };
var boundFunc = function(name) { 
	return this.prefix + " " + name;
};

var bindEm = _.bind(boundFunc, context);

console.log(bindEm('Ken Anderson'));
```

### once
Creates a version of the function that can only be called one time. Repeated calls to the modified function will have no effect, returning the value from the original call. Useful for initialization functions, instead of having to set a boolean flag and then check it later.

This is so useful if you've ever worked on a fairly more complex project. This funciton could save you a lot of performance when used right.

Here's a function that I only need to call once. All calls to this funciton after the first call should be completely ignored.
```js
var author = function(name) {
	$('hr').after($('<footer></footer>').text('This presentation was brought to you by '+ name +'. :) Thank you for a great semester.'));
}
```

Right now, if I call `author()` multiple times, we'd have multiple footer tags in our HTML.

So now we're going to try making this function ignore all calls to it after the first one by doing:
```js
var onlyOnce = _.once(author);
```

Now no matter how many times we call `onlyOnce()`, we'd only have one footer tag on our page.
```js
onlyOnce('Vahid Mazdeh');
onlyOnce('Vahid Mazdeh');
onlyOnce('Vahid Mazdeh');
```

Pretty useful for initialization functions!

---
This concludes our brief discussion of Underscore.js. Underscore has over 60 functions that are all pretty useful and we covered a few here. The source code for the underscore project is available at underscore.org.








