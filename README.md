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


