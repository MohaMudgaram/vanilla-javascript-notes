# Statements

```javascript
// Expression Statements

greeting = "Hello " + name;
i *= 3;

counter++;

delete o.x;

console.log(debugMessage);
displaySpinner(); // A hypothetical function to display a spinner in a web app.

Math.cos(x);

cx = Math.cos(x);
```

```javascript
// Compound and Empty Statements

{
    x = Math.PI;
    cx = Math.cos(x);
    console.log("cos(π) = " + cx);
}

; // Empty Statement

// Initialize an array a
for(let i = 0; i < a.length; a[i++] = 0) ;

if ((a === 0) || (b === 0));  // Oops! This line does nothing...
    o = null;                 // and this line is always executed.

for(let i = 0; i < a.length; a[i++] = 0) /* empty */ ;
```

```javascript
// Conditionals

if (expression)
    statement

if (username == null)       // If username is null or undefined,
    username = "John Doe";  // define it

// If username is null, undefined, false, 0, "", or NaN, give it a new value
if (!username) username = "John Doe";

if (!address) {
    address = "";
    message = "Please specify a mailing address.";
}

if (expression)
    statement1
else
    statement2

if (n === 1)
    console.log("You have 1 new message.");
else
    console.log(`You have ${n} new messages.`);

i = j = 1;
k = 2;
if (i === j)
    if (j === k)
        console.log("i equals k");
else
    console.log("i doesn't equal j");    // WRONG!!

if (i === j) {
    if (j === k)
        console.log("i equals k");
    else
        console.log("i doesn't equal j");    // OOPS!
}

if (i === j) {
    if (j === k) {
        console.log("i equals k");
    }
} else {  // What a difference the location of a curly brace makes!
    console.log("i doesn't equal j");
}

if (n === 1) {
    // Execute code block #1
} else if (n === 2) {
    // Execute code block #2
} else if (n === 3) {
    // Execute code block #3
} else {
    // If all else fails, execute block #4
}

if (n === 1) {
    // Execute code block #1
}
else {
    if (n === 2) {
        // Execute code block #2
    }
    else {
        if (n === 3) {
            // Execute code block #3
        }
        else {
            // If all else fails, execute block #4
        }
    }
}

switch(expression) {
    statements
}

switch(n) {
case 1:                        // Start here if n === 1
    // Execute code block #1.
    break;                     // Stop here
case 2:                        // Start here if n === 2
    // Execute code block #2.
    break;                     // Stop here
case 3:                        // Start here if n === 3
    // Execute code block #3.
    break;                     // Stop here
default:                       // If all else fails...
    // Execute code block #4.
    break;                     // Stop here
}

function convert(x) {
    switch(typeof x) {
    case "number":            // Convert the number to a hexadecimal integer
        return x.toString(16);
    case "string":            // Return the string enclosed in quotes
        return '"' + x + '"';
    default:                  // Convert any other type in the usual way
        return String(x);
    }
}
```

```javascript
// Loops

while (expression)
    statement

let count = 0;
while(count < 10) {
    console.log(count);
    count++;
}

do
    statement
while (expression);

function printArray(a) {
    let len = a.length, i = 0;
    if (len === 0) {
        console.log("Empty Array");
    } else {
        do {
            console.log(a[i]);
        } while(++i < len);
    }
}

for(initialize ; test ; increment)
    statement

initialize;
while(test) {
    statement
    increment;
}

for(let count = 0; count < 10; count++) {
    console.log(count);
}

let i, j, sum = 0;
for(i = 0, j = 10 ; i < 10 ; i++, j--) {
    sum += i * j;
}

function tail(o) {                          // Return the tail of linked list o
    for(; o.next; o = o.next) /* empty */ ; // Traverse while o.next is truthy
    return o;
}

let data = [1, 2, 3, 4, 5, 6, 7, 8, 9], sum = 0;
for(let element of data) {
    sum += element;
}
sum       // => 45

let o = { x: 1, y: 2, z: 3 };
for(let element of o) { // Throws TypeError because o is not iterable
    console.log(element);
}

let o = { x: 1, y: 2, z: 3 };
let keys = "";
for(let k of Object.keys(o)) {
    keys += k;
}
keys  // => "xyz"

let sum = 0;
for(let v of Object.values(o)) {
    sum += v;
}
sum // => 6

let pairs = "";
for(let [k, v] of Object.entries(o)) {
    pairs += k + v;
}
pairs  // => "x1y2z3"

let frequency = {};
for(let letter of "mississippi") {
    if (frequency[letter]) {
        frequency[letter]++;
    } else {
        frequency[letter] = 1;
    }
}
frequency   // => {m: 1, i: 4, s: 4, p: 2}

let text = "Na na na na na na na na Batman!";
let wordSet = new Set(text.split(" "));
let unique = [];
for(let word of wordSet) {
    unique.push(word);
}
unique // => ["Na", "na", "Batman!"]

let m = new Map([[1, "one"]]);
for(let [key, value] of m) {
    key    // => 1
    value  // => "one"
}

// Read chunks from an asynchronously iterable stream and print them out
async function printStream(stream) {
    for await (let chunk of stream) {
        console.log(chunk);
    }
}

for (variable in object)
    statement

for(let p in o) {      // Assign property names of o to variable p
    console.log(o[p]); // Print the value of each property
}

let o = { x: 1, y: 2, z: 3 };
let a = [], i = 0;
for(a[i++] in o) /* empty */;

for(let i in a) console.log(i);
```

```javascript
// Jumps

identifier: statement

mainloop: while(token !== null) {
    // Code omitted...
    continue mainloop;  // Jump to the next iteration of the named loop
    // More code omitted...
}

break;

for(let i = 0; i < a.length; i++) {
    if (a[i] === target) break;
}

break labelname;

let matrix = getData();  // Get a 2D array of numbers from somewhere
// Now sum all the numbers in the matrix.
let sum = 0, success = false;
// Start with a labeled statement that we can break out of if errors occur
computeSum: if (matrix) {
    for(let x = 0; x < matrix.length; x++) {
        let row = matrix[x];
        if (!row) break computeSum;
        for(let y = 0; y < row.length; y++) {
            let cell = row[y];
            if (isNaN(cell)) break computeSum;
            sum += cell;
        }
    }
    success = true;
}
// The break statements jump here. If we arrive here with success == false
// then there was something wrong with the matrix we were given.
// Otherwise, sum contains the sum of all cells of the matrix.

continue;

continue labelname;

for(let i = 0; i < data.length; i++) {
    if (!data[i]) continue;  // Can't proceed with undefined data
    total += data[i];
}

return expression;

function square(x) { return x*x; } // A function that has a return statement
square(2)                          // => 4

function displayObject(o) {
    // Return immediately if the argument is null or undefined.
    if (!o) return;
    // Rest of function goes here...
}

// A generator function that yields a range of integers
function* range(from, to) {
    for(let i = from; i <= to; i++) {
        yield i;
    }
}

throw expression;

function factorial(x) {
    // If the input argument is invalid, throw an exception!
    if (x < 0) throw new Error("x must not be negative");
    // Otherwise, compute a value and return normally
    let f;
    for(f = 1; x > 1; f *= x, x--) /* empty */ ;
    return f;
}
factorial(4)   // => 24

try {
    // Normally, this code runs from the top of the block to the bottom
    // without problems. But it can sometimes throw an exception,
    // either directly, with a throw statement, or indirectly, by calling
    // a method that throws an exception.
}
catch(e) {
    // The statements in this block are executed if, and only if, the try
    // block throws an exception. These statements can use the local variable
    // e to refer to the Error object or other value that was thrown.
    // This block may handle the exception somehow, may ignore the
    // exception by doing nothing, or may rethrow the exception with throw.
}
finally {
    // This block contains statements that are always executed, regardless of
    // what happens in the try block. They are executed whether the try
    // block terminates:
    //   1) normally, after reaching the bottom of the block
    //   2) because of a break, continue, or return statement
    //   3) with an exception that is handled by a catch clause above
    //   4) with an uncaught exception that is still propagating
}

try {
    // Ask the user to enter a number
    let n = Number(prompt("Please enter a positive integer", ""));
    // Compute the factorial of the number, assuming the input is valid
    let f = factorial(n);
    // Display the result
    alert(n + "! = " + f);
}
catch(ex) {     // If the user's input was not valid, we end up here
    alert(ex);  // Tell the user what the error is
}

// Simulate for(initialize ; test ;increment ) body;
initialize ;
while( test ) {
    try { body ; }
    finally { increment ; }
}

// Like JSON.parse(), but return undefined instead of throwing an error
function parseJSON(s) {
    try {
        return JSON.parse(s);
    } catch {
        // Something went wrong but we don't care what it was
        return undefined;
    }
}

```

```javascript
// Miscellaneous Statements

with (object)
    statement

document.forms[0].address.value

with(document.forms[0]) {
    // Access form elements directly here. For example:
    name.value = "";
    address.value = "";
    email.value = "";
}

let f = document.forms[0];
f.name.value = "";
f.address.value = "";
f.email.value = "";

function f(o) {
  if (o === undefined) debugger;  // Temporary line for debugging purposes
  ...                             // The rest of the function goes here.
}

```

```javascript
// Declarations

const TAU = 2*Math.PI;
let radius = 3;
var circumference = TAU * radius;

function area(radius) {
    return Math.PI * radius * radius;
}

class Circle {
    constructor(radius) { this.r = radius; }
    area() { return Math.PI * this.r * this.r; }
    circumference() { return 2 * Math.PI * this.r; }
}

import Circle from './geometry/circle.js';
import { PI, TAU } from './geometry/constants.js';
import { magnitude as hypotenuse } from './vectors/utils.js';

// geometry/constants.js
const PI = Math.PI;
const TAU = 2 * PI;
export { PI, TAU };

export const TAU = 2 * Math.PI;
export function magnitude(x,y) { return Math.sqrt(x*x + y*y); }
export default class Circle { /* class definition omitted here */ }

```
