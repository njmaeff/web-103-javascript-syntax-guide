# Javascript Syntax Guide

## JavaScript Comments

In javascript, there are inline and multiline comments. You may use comments to document parts of your code.

```javascript
/*
* this is a multiline comment
*/


// this is an inline comment

```

## JavaScript Data Types

Datatypes are used with variables to store information for use in the program.

```javascript

const isNull = null // null is a value and (typeof null === "object") is true.

const isTrue = true // booleans are used for logic and branching

const nintyNine = 99 // numbers are used for logic and counting

const apple = "apple" // strings are meant for outputs

const orange = { // object are good for storing related data
    type: "fruit",
    color: "orange",
}

const fruits = ["apple", "orange", "banana"] // arrays are good for collections

```

## JavaScript Functions & Parameters
Functions are how you can group operations and re-use them across code. A function also has its own variable scope.

```javascript
const tree = "pine"

function cedarTree() {
    const tree = "cedar" // the function has its own variable scope so this is safe.

    // a function may return a value to the caller
    return tree // returns "cedar", not "pine".
}

// calling the function
console.log(cedarTree()) // logs the returned value from the function "cedar"
```
A function may have inputs separated by a comma, changing what the function returns or how it behaves.

```javascript

function addTwo(myNumber) {
    
    return 2 + myNumber
}

console.log(addTwo(4)) // 2 + 4 == 6
console.log(addTwo(6)) // 2 + 6 == 8

function multiply(number1, number2) {
    
    return number1 * number2
}

console.log(multiply(2, 4)) // call function with parameters 2 * 4 == 8
```


## JavaScript Variables 
Variables are how you store things for use in later statements and operations. You can make constant variables (only be assigned once) and mutable variables, which may change value over time.

### Constants
JavaScript constants are great for storing values that never need to change. If you try to re-assign a constant, you will get a visible runtime error.

```javascript
const fruit = "apple"; // assign a value to the variable.

fruit = "orange"; // this will produce runtime error and log to the console.
```

### Mutable Variables (Variables which can be re-assigned)
Mutable variables are fantastic for things like counters and sums.

```javascript
let fruit = "apple"; // asign a value to the variable.
var tree = "cedar"; // asign a value to the variable.


fruit = "orange"; // this is perfectly fine
tree = "pine"; // this is perfectly fine
```

`var` is different than let in the following way. Var declarations are all function scoped, meaning any declarations inside block statements like `if/else` and `try/catch` are accessible outside the block after they are assigned. When using let, you can also only use the variable name once in the scope, or else you will get a parse error.

```javascript

function logCedar() {

    if (true) {
        var tree = 'cedar';
    }
    // the tree variable is available outside the block

    console.log(tree); // outputs 'cedar';
    
}


// the tree variable is not available outside the block
function logCedar2() {

    
    if (true) {
        let tree = 'cedar';
    }
    console.log(tree); // runtime error;
    
}

// only use `let` once
function logPine() {
    
    let tree = 'cedar';
    let tree = 'pine'; // parse error
    
}
```

## JavaScript Comparison Statements
Comparison operators are the drivers behind conditional logic (program branching). They are used within boolean statements.

### Comparison Operators
```javascript
// less than
1 < 2 // true

// less than or equal
1 <= 1  // true

// greater than
2 > 1 // true

// greater than or equal
2 >= 2 // true

// is equal to (with type coercion)
1 == "1" // true

// is not equal to (with type coercion)
1 != "1" // false


// is equal with strict comparison
1 === "1" // false

// is not equal with strict comparison
1 !== "1" // true
```


## JavaScript Boolean Statements
The two boolean statements are `if/else` and `switch`.

If statements

```javascript
// If statement
const x = 5;

if (x > 4) {
    console.log("Success!"); // this runs
}

// if with else statement
if (x > 6) {
    console.log("Success!"); // this does not run
}
else {
    console.log("Oh no!"); // this runs
}


// if with else if statement, then else
if (x > 6) {
    console.log("Success!"); // this does not run
} else if (x >= 5) {
    console.log("Kind of success!"); // this runs
} else {
    console.log("Oh no!"); // this does not run
}
```


Switch statements are great for matching strings. If you do not break after hitting a case statement, the switch statement will continue to run until it hits the default case.

```javascript
const fruit = "apple";

switch (fruit) {
    case "orange":
        console.log("I'm an orange!"); // this does not run
        break;

    case "apple":
        console.log("I'm an apple!"); // this runs then breaks the statement
        break;

    default:
        // hits if none of the above match
        console.log("I'm neither an apple nor an orange!");
        break;
}

switch (fruit) {
    case "orange":
        console.log("I'm an orange!"); // this does not run
        break;

    case "apple":
        console.log("I'm an apple!"); // this runs

    default:
        console.log("I'm neither an apple nor an orange!"); // this runs too because we did not break from apple
        break;
}
```

## Javascript Arrays
Javascript arrays store an ordered collection of items, and a value may be accessed (indexed) using their order number. There are also several helper methods on the array which make it easy to do certain operations.

```javascript
// array literal with all string elements
const fruits = [
    "apple", // index 0
    "orange", // index 1
    "banana" // index 2
];

const apple = fruits[0] // access apple by using index 0

fruits[0] = "grapes" // change the value at index 0 from apple to grapes

fruits[3] = "pear" // add a new fruit pear at index 3

```

Helpfull array properties and methods
```javascript
const fruits = [
    "apple", // index 0
    "orange", // index 1
    "banana" // index 2
];

fruits.length === 3 //  true

// remove last element from the array
fruits.pop() // "banana"

fruits.push("banana") // add "banana" to the end of the array


// remove first element from the array
fruits.shift() // "apple"
fruits.unshift("apple") // add "apple" to the beginning of the array

// take a section of the array
fruits.slice(0, 2) // ["apple", "orange"]

// insert elements and optionally delete items at a certain index
fruits.splice(1, 0, "grapes"); // ["apple", "grapes", "orange", "banana"]

// iterate over element with their index
fruits.foreach(function (fruit, index) {
    console.log(fruit, index) // logs "apple 0" "orange 1" "banana 2"
})

// take each element and the return value replaces the element in the array
fruits.map(function (fruit, index) {
    return fruit + index
}) // ["apple0", "orange1", "banana2"] 
```

## JavaScript Objects
Javascript objects are containers that hold related properties and values. A property is a unique string defined on the object to access the value. Values may be any type discussed so far and functions (called methods on an object).

```javascript
const chickenPizza = {

    // object properties can be any literal type including objects
    ingredients: ["cheese", "chicken", "peppers", "onions"],
    cookTime: 40,
    difficulty: "easy",
    isTasty: true,
    crust: {
        type: "thin",
        glutenFree: false
    },

    // object method
    addBarbequeSauce(){
        this.ingredients.push("barbeque sauce") // adds an ingredient to the end of the ingredient value array
    }
};

// accessing an object property
chickenPizza.cookTime // 40

// changing an object property
chickenPizza.cookTime = 30;

// calling a method on an object
chickenPizza.addBarbequeSauce();
```

## JavaScript Loops
Javascript loops are great for operating on arrays. 

With `for` loop, you must provide an initial condition (index in the below example), a conditional which will terminate the loop, and an increment expression.
With the `while` loop, you must provide a conditional that terminates the loop. 

The below two loops are equivelent.
```javascript
const fruits = ["apple", "orange", "banana"];

// for loop
for (let index = 0; index < fruits.length; index++) {
    console.log(fruits[index]); // logs apple, orange, banana
}

index = 0
while (index < fruits.length) {
    console.log(fruits[index]); // logs apple, orange, banana
    index++
}

```