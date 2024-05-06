# Arrays

```javascript
// Creating Arrays

let empty = [];                 // An array with no elements
let primes = [2, 3, 5, 7, 11];  // An array with 5 numeric elements
let misc = [ 1.1, true, "a", ]; // 3 elements of various types + trailing comma

let base = 1024;
let table = [base, base+1, base+2, base+3];

let count = [1,,3]; // Elements at indexes 0 and 2. No element at index 1
let undefs = [,,];  // An array with no elements but a length of 2

let a = [1, 2, 3];
let b = [0, ...a, 4];  // b == [0, 1, 2, 3, 4]

let original = [1,2,3];
let copy = [...original];
copy[0] = 0;  // Modifying the copy does not change the original
original[0]   // => 1

let digits = [..."0123456789ABCDEF"];
digits // => ["0","1","2","3","4","5","6","7","8","9","A","B","C","D","E","F"]

let letters = [..."hello world"];
[...new Set(letters)]  // => ["h","e","l","o"," ","w","r","d"]

let a = new Array();

let a = new Array(10);

let a = new Array(5, 4, 3, 2, 1, "testing, testing");

Array.of()        // => []; returns empty array with no arguments
Array.of(10)      // => [10]; can create arrays with a single numeric argument
Array.of(1,2,3)   // => [1, 2, 3]

let copy = Array.from(original);

let truearray = Array.from(arraylike);

```

```javascript
// Reading and Writing Array Elements

let a = ["world"];     // Start with a one-element array
let value = a[0];      // Read element 0
a[1] = 3.14;           // Write element 1
let i = 2;
a[i] = 3;              // Write element 2
a[i + 1] = "hello";    // Write element 3
a[a[i]] = a[0];        // Read elements 0 and 2, write element 3

a.length       // => 4

let o = {};    // Create a plain object
o[1] = "one";  // Index it with an integer
o["1"]         // => "one"; numeric and string property names are the same

a[-1.23] = true;  // This creates a property named "-1.23"
a["1000"] = 0;    // This the 1001st element of the array
a[1.000] = 1;     // Array index 1. Same as a[1] = 1;

let a = [true, false]; // This array has elements at indexes 0 and 1
a[2]                   // => undefined; no element at this index.
a[-1]                  // => undefined; no property with this name.

```

```javascript
// Sparse Arrays

let a = new Array(5); // No elements, but a.length is 5.
a = [];               // Create an array with no elements and length = 0.
a[1000] = 0;          // Assignment adds one element but sets length to 1001.

let a1 = [,];           // This array has no elements and length 1
let a2 = [undefined];   // This array has one undefined element
0 in a1                 // => false: a1 has no element with index 0
0 in a2                 // => true: a2 has the undefined value at index 0

```

```javascript
// Array Length

[].length             // => 0: the array has no elements
["a","b","c"].length  // => 3: highest index is 2, length is 3

a = [1,2,3,4,5];     // Start with a 5-element array.
a.length = 3;        // a is now [1,2,3].
a.length = 0;        // Delete all elements.  a is [].
a.length = 5;        // Length is 5, but no elements, like new Array(5)


```

```javascript
// Adding and Deleting Array Elements

let a = [];      // Start with an empty array.
a[0] = "zero";   // And add elements to it.
a[1] = "one";

let a = [];           // Start with an empty array
a.push("zero");       // Add a value at the end.  a = ["zero"]
a.push("one", "two"); // Add two more values.  a = ["zero", "one", "two"]

let a = [1,2,3];
delete a[2];   // a now has no element at index 2
2 in a         // => false: no array index 2 is defined
a.length       // => 3: delete does not affect array length

```

```javascript
// Iterating Arrays

let letters = [..."Hello world"];  // An array of letters
let string = "";
for(let letter of letters) {
    string += letter;
}
string  // => "Hello world"; we reassembled the original text

let everyother = "";
for(let [index, letter] of letters.entries()) {
    if (index % 2 === 0) everyother += letter;  // letters at even indexes
}
everyother  // => "Hlowrd"

let uppercase = "";
letters.forEach(letter => {  // Note arrow function syntax here
    uppercase += letter.toUpperCase();
});
uppercase  // => "HELLO WORLD"

let vowels = "";
for(let i = 0; i < letters.length; i++) { // For each index in the array
    let letter = letters[i];              // Get the element at that index
    if (/[aeiou]/.test(letter)) {         // Use a regular expression test
        vowels += letter;                 // If it is a vowel, remember it
    }
}
vowels  // => "eoo"

// Save the array length into a local variable
for(let i = 0, len = letters.length; i < len; i++) {
    // loop body remains the same
}

// Iterate backwards from the end of the array to the start
for(let i = letters.length-1; i >= 0; i--) {
    // loop body remains the same
}

for(let i = 0; i < a.length; i++) {
    if (a[i] === undefined) continue; // Skip undefined + nonexistent elements
    // loop body here
}

```
