# JavaScript Project

## JavaScript definitions

In this part you can learn about the different syntax veriations, what is DOM and many other JS definitions.

### DOMContentLoaded

'DOMContentLoaded': The document has finished loading (but not its dependent resources). DOM stands for "Document Object Model" A DOM is made when the web page is loaded and the browser creates a DOM.
The DOM is made so JS can interact and edit the HTML web page.
There are multiple DOM variants but the one you are using is called "HTML DOM".
Read more here: [JavaScript HTML DOM](https://www.w3schools.com/js/js_htmldom.asp)

### document

"document" is the owner of all objects in the webpage, it comes from DOM,

### function()

```js
document.addEventListener("DOMContentLoaded", function () {});
```

This is an anonymous self-invoking function (function without name).
Go to "Self-Invoking Functions section at [Function Definitions](https://www.w3schools.com/js/js_function_definition.asp)

### addEventListener()

To know more about how the method addEventListener() works we need to look at the syntax.

Syntax:

```js
document.addEventListener(event, function, Capture)
```

Your code:

```js
document.addEventListener("DOMContentLoaded", function () {});
```

This shows "DOMContentLoaded" being an event, which means that when the webpages content is loaded and has created a DOM event.

It will then invoke the function(). If the "DOMContentLoaded" event does not occur, let's say the page takes too long to load, the function() will not invoke.

A sidenote is that "invoke will execute and join on that task. execute and submit will push the task to a work queue to be worked on later."
[Stackoverflow - Difference between Execute , Submit and Invoke()](https://stackoverflow.com/questions/17881183/difference-between-execute-submit-and-invoke-in-a-forkjoinpool)

### Facts

A good to know fact is about "let" so here is how you could remember how its used:

It comes from the English word 'let'.
verb: "let", "letting". 1. to allow or permit:

```js
// Hey computer, can you please
let // this
  night = "wonderful";
```

[Source](https://stackoverflow.com/questions/33090193/linguistic-meaning-of-let-variable-in-programming)

### updateRatingDisplay()

Your code:

```js
function updateRatingDisplay(rating) {
  stars.forEach((star, index) => {
    if (index < rating) {
      star.classList.add("selected");
    } else {
      star.classList.remove("selected");
    }
  });
}

stars.forEach((star) => {
  star.addEventListener("click", function () {
    currentRating = this.getAttribute("data-value");
    updateRatingDisplay(currentRating);
  });
});
```

Let's break it down.

#### Array forEach()

```js
function updateRatingDisplay(rating) {}
```

This is a function called "updateRatingDisplay" that has a parameter "rating" which is undefined (it has no value)

```js
stars.forEach((star, index) => {});
```

'.forEach' method calls/iterates over each element in the 'stars' array.
'stars' is an array for all classes called ".star".
'index' is the index/value of the current element.

#### Regular and Arrow functions syntax

Is important to know that the syntax shown above is 'Regular functiosyntax' and you are using 'Arrow function syntax'.This means that it does not have it's own 'this' value.
To be more precise i have asked ChatGPT for a helping hand. So some of it is my own writing and some is not.

Arrow function syntax

```js
stars.forEach((star, index) => {
  // Function body
});
```

Regular function syntax

```js
array.forEach(function(currentValue, index, arr), thisValue) {
  // Function body
});

```

Arrow function syntax:

    Arrow functions do not have their own this. The value of this inside an arrow function is inherited from the enclosing lexical context (i.e., the scope in which the arrow function is defined).
    Arrow functions have a concise syntax, using =>, which makes them particularly suitable for short, simple functions like the one in your example.

"enclosing lexical context"
Lexical Scope: This refers to the scope that is determined at the time the code is written, based on where variables and functions are declared within the code.
Enclosing Context: This is the context (scope) in which the arrow function is defined. It is the scope that surrounds the arrow function definition.

Regular function syntax:

    Regular functions have their own this value, which is determined by how they are called. When using forEach, the thisValue parameter allows you to specify the value that this should refer to within the callback function.
    Regular functions have a more verbose syntax, using the function keyword.

Note that this is the same syntax w3schools uses [w3schools - jsref foreach](https://www.w3schools.com/jsref/jsref_foreach.aspIt)

So, when you use this inside an arrow function, JavaScript looks at the this value from the context in which the arrow function is defined, not from the context in which it is called.
Here's an example to illustrate:

```js
const obj = {
  name: "Alice",
  sayHello: function () {
    console.log("Hello, " + this.name); // Regular function syntax
  },
  sayHelloArrow: () => {
    console.log("Hello, " + this.name); // Arrow function syntax
  },
};

obj.sayHello(); // Outputs: Hello, Alice
obj.sayHelloArrow(); // Outputs: Hello, undefined
```

In the example above:

    Inside sayHello, this refers to the obj object because sayHello is a regular function called as a method of obj.
    Inside sayHelloArrow, this refers to the global this, because arrow functions inherit this from the enclosing lexical context, which in this case is the global scope. Therefore, this.name doesn't refer to obj.name, resulting in undefined.
