# Types, Values, and Variables

```javascript
// Integer Literals

// Decimal

0
3
10000000

// Hexadecimal

0xff       // => 255: (15*16 + 15)
0xBADCAFE  // => 195939070

// Octal

0b10101  // => 21:  (1*16 + 0*8 + 1*4 + 0*2 + 1*1)

// Binary

0o377    // => 255: (3*64 + 7*8 + 7*1)

```

```javascript
// Floating-Point Literals

[digits][.digits][(E|e)[(+|-)]digits]

3.14
2345.6789
.333333333333333333
6.02e23        // 6.02 × 10²³
1.4738223E-32  // 1.4738223 × 10⁻³²


```

```javascript
// Separators in Numeric Literals

let billion = 1_000_000_000;   // Underscore as a thousands separator.
let bytes = 0x89_AB_CD_EF;     // As a bytes separator.
let bits = 0b0001_1101_0111;   // As a nibble separator.
let fraction = 0.123_456_789;  // Works in the fractional part, too.


```

```javascript
// Math object

Math.pow(2,53)           // => 9007199254740992: 2 to the power 53
Math.round(.6)           // => 1.0: round to the nearest integer
Math.ceil(.6)            // => 1.0: round up to an integer
Math.floor(.6)           // => 0.0: round down to an integer
Math.abs(-5)             // => 5: absolute value
Math.max(x,y,z)          // Return the largest argument
Math.min(x,y,z)          // Return the smallest argument
Math.random()            // Pseudo-random number x where 0 <= x < 1.0
Math.PI                  // π: circumference of a circle / diameter
Math.E                   // e: The base of the natural logarithm
Math.sqrt(3)             // => 3**0.5: the square root of 3
Math.pow(3, 1/3)         // => 3**(1/3): the cube root of 3
Math.sin(0)              // Trigonometry: also Math.cos, Math.atan, etc.
Math.log(10)             // Natural logarithm of 10
Math.log(100)/Math.LN10  // Base 10 logarithm of 100
Math.log(512)/Math.LN2   // Base 2 logarithm of 512
Math.exp(3)              // Math.E cubed

// ES6

Math.cbrt(27)    // => 3: cube root
Math.hypot(3, 4) // => 5: square root of sum of squares of all arguments
Math.log10(100)  // => 2: Base-10 logarithm
Math.log2(1024)  // => 10: Base-2 logarithm
Math.log1p(x)    // Natural log of (1+x); accurate for very small x
Math.expm1(x)    // Math.exp(x)-1; the inverse of Math.log1p()
Math.sign(x)     // -1, 0, or 1 for arguments <, ==, or > 0
Math.imul(2,3)   // => 6: optimized multiplication of 32-bit integers
Math.clz32(0xf)  // => 28: number of leading zero bits in a 32-bit integer
Math.trunc(3.9)  // => 3: convert to an integer by truncating fractional part
Math.fround(x)   // Round to nearest 32-bit float number
Math.sinh(x)     // Hyperbolic sine. Also Math.cosh(), Math.tanh()
Math.asinh(x)    // Hyperbolic arcsine. Also Math.acosh(), Math.atanh()


```

```javascript
// Number object

Infinity                    // A positive number too big to represent
Number.POSITIVE_INFINITY    // Same value
1/0                         // => Infinity
Number.MAX_VALUE * 2        // => Infinity; overflow

-Infinity                   // A negative number too big to represent
Number.NEGATIVE_INFINITY    // The same value
-1/0                        // => -Infinity
-Number.MAX_VALUE * 2       // => -Infinity

NaN                         // The not-a-number value
Number.NaN                  // The same value, written another way
0/0                         // => NaN
Infinity/Infinity           // => NaN

Number.MIN_VALUE/2          // => 0: underflow
-Number.MIN_VALUE/2         // => -0: negative zero
-1/Infinity                 // -> -0: also negative 0
-0

// The following Number properties are defined in ES6
Number.parseInt()       // Same as the global parseInt() function
Number.parseFloat()     // Same as the global parseFloat() function
Number.isNaN(x)         // Is x the NaN value?
Number.isFinite(x)      // Is x a number and finite?
Number.isInteger(x)     // Is x an integer?
Number.isSafeInteger(x) // Is x an integer -(2**53) < x < 2**53?
Number.MIN_SAFE_INTEGER // => -(2**53 - 1)
Number.MAX_SAFE_INTEGER // => 2**53 - 1
Number.EPSILON          // => 2**-52: smallest difference between numbers

let zero = 0;         // Regular zero
let negz = -0;        // Negative zero
zero === negz         // => true: zero and negative zero are equal
1/zero === 1/negz     // => false: Infinity and -Infinity are not equal
```

```javascript
// Binary Floating-Point and Rounding Errors

let x = .3 - .2;    // thirty cents minus 20 cents
let y = .2 - .1;    // twenty cents minus 10 cents
x === y             // => false: the two values are not the same!
x === .1            // => false: .3-.2 is not equal to .1
y === .1            // => true: .2-.1 is equal to .1
```

```javascript
// Arbitrary Precision Integers with BigInt

1234n                // A not-so-big BigInt literal
0b111111n            // A binary BigInt
0o7777n              // An octal BigInt
0x8000000000000000n  // => 2n**63n: A 64-bit integer

BigInt(Number.MAX_SAFE_INTEGER)     // => 9007199254740991n
let string = "1" + "0".repeat(100); // 1 followed by 100 zeros.
BigInt(string)                      // => 10n**100n: one googol

1000n + 2000n  // => 3000n
3000n - 2000n  // => 1000n
2000n * 3000n  // => 6000000n
3000n / 997n   // => 3n: the quotient is 3
3000n % 997n   // => 9n: and the remainder is 9
(2n ** 131071n) - 1n  // A Mersenne prime with 39457 decimal digits


1 < 2n     // => true
2 > 1n     // => true
0 == 0n    // => true
0 === 0n   // => false: the === checks for type equality as well
```

```javascript
// Dates and Times

let timestamp = Date.now();  // The current time as a timestamp (a number).
let now = new Date();        // The current time as a Date object.
let ms = now.getTime();      // Convert to a millisecond timestamp.
let iso = now.toISOString(); // Convert to a string in standard format.
```

```javascript
// CHARACTERS, CODEPOINTS, AND JAVASCRIPT STRINGS

let euro = "€";
let love = "❤";
euro.length   // => 1: this character has one 16-bit element
love.length   // => 2: UTF-16 encoding of ❤ is "\ud83d\udc99"

""  // The empty string: it has zero characters
'testing'
"3.14"
'name="myform"'
"Wouldn't you prefer O'Reilly's book?"
"τ is the ratio of a circle's circumference to its radius"
`"She said 'hi'", he said.`

// A string representing 2 lines written on one line:
'two\nlines'

// A one-line string written on 3 lines:
"one\
 long\
 line"

// A two-line string written on two lines:
`the newline character at the end of this line
is included literally in this string`

<button onclick="alert('Thank you')">Click Me</button>

'You\'re right, it can\'t be a quote'

```

| Sequence    | Character represented                                                                                                       |
| ----------- | --------------------------------------------------------------------------------------------------------------------------- |
| `\0`        | The NUL character (`\u0000`)                                                                                                |
| `\b`        | Backspace (`\u0008`)                                                                                                        |
| `\t`        | Horizontal tab (`\u0009`)                                                                                                   |
| `\n`        | Newline (`\u000A`)                                                                                                          |
| `\v`        | Vertical tab (`\u000B`)                                                                                                     |
| `\f`        | Form feed (`\u000C`)                                                                                                        |
| `\r`        | Carriage return (`\u000D`)                                                                                                  |
| `\"`        | Double quote (`\u0022`)                                                                                                     |
| `\'`        | Apostrophe or single quote (`\u0027`)                                                                                       |
| `\\`        | Backslash (`\u005C`)                                                                                                        |
| `\x`*nn*    | The Unicode character specified by the two hexadecimal digits *nn*                                                          |
| `\u`*nnnn*  | The Unicode character specified by the four hexadecimal digits *nnnn*                                                       |
| `\u{`*n*`}` | The Unicode character specified by the codepoint *n*, where *n* is one to six hexadecimal digits between 0 and 10FFFF (ES6) |

```javascript
// Working with Strings

let msg = "Hello, " + "world";   // Produces the string "Hello, world"
let greeting = "Welcome to my blog," + " " + name;

s.length

let s = "Hello, world"; // Start with some text.

// Obtaining portions of a string
s.substring(1,4)        // => "ell": the 2nd, 3rd, and 4th characters.
s.slice(1,4)            // => "ell": same thing
s.slice(-3)             // => "rld": last 3 characters
s.split(", ")           // => ["Hello", "world"]: split at delimiter string

// Searching a string
s.indexOf("l")          // => 2: position of first letter l
s.indexOf("l", 3)       // => 3: position of first "l" at or after 3
s.indexOf("zz")         // => -1: s does not include the substring "zz"
s.lastIndexOf("l")      // => 10: position of last letter l

// Boolean searching functions in ES6 and later
s.startsWith("Hell")    // => true: the string starts with these
s.endsWith("!")         // => false: s does not end with that
s.includes("or")        // => true: s includes substring "or"

// Creating modified versions of a string
s.replace("llo", "ya")  // => "Heya, world"
s.toLowerCase()         // => "hello, world"
s.toUpperCase()         // => "HELLO, WORLD"
s.normalize()           // Unicode NFC normalization: ES6
s.normalize("NFD")      // NFD normalization. Also "NFKC", "NFKD"

// Inspecting individual (16-bit) characters of a string
s.charAt(0)             // => "H": the first character
s.charAt(s.length-1)    // => "d": the last character
s.charCodeAt(0)         // => 72: 16-bit number at the specified position
s.codePointAt(0)        // => 72: ES6, works for codepoints > 16 bits

// String padding functions in ES2017
"x".padStart(3)         // => "  x": add spaces on the left to a length of 3
"x".padEnd(3)           // => "x  ": add spaces on the right to a length of 3
"x".padStart(3, "*")    // => "**x": add stars on the left to a length of 3
"x".padEnd(3, "-")      // => "x--": add dashes on the right to a length of 3

// Space trimming functions. trim() is ES5; others ES2019
" test ".trim()         // => "test": remove spaces at start and end
" test ".trimStart()    // => "test ": remove spaces on left. Also trimLeft
" test ".trimEnd()      // => " test": remove spaces at right. Also trimRight

// Miscellaneous string methods
s.concat("!")           // => "Hello, world!": just use + operator instead
"<>".repeat(5)          // => "<><><><><>": concatenate n copies. ES6

let s = "hello, world";
s[0]                  // => "h"
s[s.length-1]         // => "d"
```

```javascript
// Template Literals

let s = `hello world`;

let name = "Bill";
let greeting = `Hello ${ name }.`;  // greeting == "Hello Bill."

let errorMessage = `\
\u2718 Test failure at ${filename}:${linenumber}:
${exception.message}
Stack trace:
${exception.stack}
`;

`\n`.length            // => 1: the string has a single newline character
String.raw`\n`.length  // => 2: a backslash character and the letter n

```

```javascript
// Pattern Matching and Regular Expressions

/^HTML/;             // Match the letters H T M L at the start of a string
/[1-9][0-9]*/;       // Match a nonzero digit, followed by any # of digits
/\bjavascript\b/i;   // Match "javascript" as a word, case-insensitive

let text = "testing: 1, 2, 3";   // Sample text
let pattern = /\d+/g;            // Matches all instances of one or more digits
pattern.test(text)               // => true: a match exists
text.search(pattern)             // => 9: position of first match
text.match(pattern)              // => ["1", "2", "3"]: array of all matches
text.replace(pattern, "#")       // => "testing: #, #, #"
text.split(/\D+/)                // => ["","1","2","3"]: split on nondigits

```

```javascript
// Boolean Values

a === 4

if (a === 4) {
    b = b + 1;
} else {
    a = a + 1;
}

// False - Falsy Values
undefined
null
0
-0
NaN
""  // the empty string

if (o !== null) ...

if (o) ...

if ((x === 0 && y === 0) || !(z === 0)) {
    // x and y are both zero or z is non-zero
}

```

```javascript
// null and undefined

// I consider undefined to represent a system-level, unexpected, or error-like absence of value and null to represent a program-level, normal, or expected absence of value. I avoid using null and undefined when I can, but if I need to assign one of these values to a variable or property or pass or return one of these values to or from a function, I usually use null.





```

```javascript
// Symbols

let strname = "string name";      // A string to use as a property name
let symname = Symbol("propname"); // A Symbol to use as a property name
typeof strname                    // => "string": strname is a string
typeof symname                    // => "symbol": symname is a symbol
let o = {};                       // Create a new object
o[strname] = 1;                   // Define a property with a string name
o[symname] = 2;                   // Define a property with a Symbol name
o[strname]                        // => 1: access the string-named property
o[symname]                        // => 2: access the symbol-named property

let s = Symbol("sym_x");
s.toString()             // => "Symbol(sym_x)"

let s = Symbol.for("shared");
let t = Symbol.for("shared");
s === t          // => true
s.toString()     // => "Symbol(shared)"
Symbol.keyFor(t) // => "shared"

```

```javascript
// Global Ojects


/*
Global constants like undefined, Infinity, and NaN
Global functions like isNaN(), parseInt() and eval()
Constructor functions like Date(), RegExp(), String(), Object(), and Array()
Global objects like Math and JSON
*/
```

```javascript
// Immutable Primitive Values and Mutable Object References

let s = "hello";   // Start with some lowercase text
s.toUpperCase();   // Returns "HELLO", but doesn't alter s
s                  // => "hello": the original string has not changed

let o = { x: 1 };  // Start with an object
o.x = 2;           // Mutate it by changing the value of a property
o.y = 3;           // Mutate it again by adding a new property

let a = [1,2,3];   // Arrays are also mutable
a[0] = 0;          // Change the value of an array element
a[3] = 4;          // Add a new array element

let o = {x: 1}, p = {x: 1};  // Two objects with the same properties
o === p                      // => false: distinct objects are never equal
let a = [], b = [];          // Two distinct, empty arrays
a === b                      // => false: distinct arrays are never equal

let a = [];   // The variable a refers to an empty array.
let b = a;    // Now b refers to the same array.
b[0] = 1;     // Mutate the array referred to by variable b.
a[0]          // => 1: the change is also visible through variable a.
a === b       // => true: a and b refer to the same object, so they are equal.

let a = ["a","b","c"];              // An array we want to copy
let b = [];                         // A distinct array we'll copy into
for(let i = 0; i < a.length; i++) { // For each index of a[]
    b[i] = a[i];                    // Copy an element of a into b
}
let c = Array.from(b);              // In ES6, copy arrays with Array.from()

function equalArrays(a, b) {
    if (a === b) return true;                // Identical arrays are equal
    if (a.length !== b.length) return false; // Different-size arrays not equal
    for(let i = 0; i < a.length; i++) {      // Loop through all elements
        if (a[i] !== b[i]) return false;     // If any differ, arrays not equal
    }
    return true;                             // Otherwise they are equal
}

```

```javascript
// Type Conversions

10 + " objects"     // => "10 objects":  Number 10 converts to a string
"7" * "4"           // => 28: both strings convert to numbers
let n = 1 - "x";    // n == NaN; string "x" can't convert to a number
n + " objects"      // => "NaN objects": NaN converts to string "NaN"

```

| Value                           | to String                                                                                                             | to Number | to Boolean  |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------- | ----------- |
| `undefined`                     | `"undefined"`                                                                                                         | `NaN`     | `false`     |
| `null`                          | `"null"`                                                                                                              | **`0`**   | `false`     |
| `true`                          | `"true"`                                                                                                              | **`1`**   |             |
| `false`                         | `"false"`                                                                                                             | **`0`**   |             |
| `""` (empty string)             |                                                                                                                       | **`0`**   | **`false`** |
| `"1.2"` (nonempty, numeric)     |                                                                                                                       | `1.2`     | `true`      |
| `"one"` (nonempty, non-numeric) |                                                                                                                       | `NaN`     | `true`      |
| `0`                             | `"0"`                                                                                                                 |           | **`false`** |
| `-0`                            | `"0"`                                                                                                                 |           | **`false`** |
| `1` (finite, non-zero)          | `"1"`                                                                                                                 |           | `true`      |
| `Infinity`                      | `"Infinity"`                                                                                                          |           | `true`      |
| `-Infinity`                     | `"-Infinity"`                                                                                                         |           | `true`      |
| `NaN`                           | `"NaN"`                                                                                                               |           | **`false`** |
| `{}` (any object)               |                                                                                                                       |           | `true`      |
| `[]` (empty array)              | `""`                                                                                                                  | **`0`**   | `true`      |
| `[9]` (one numeric element)     | `"9"`                                                                                                                 | **`9`**   | `true`      |
| `['a']` (any other array)       | *use join() method*                                                                                                   | `NaN`     | `true`      |
| `function(){}` (any function)   | *see [§3.9.3](https://learning.oreilly.com/library/view/javascript-the-definitive/9781491952016/ch03.html#objtoprim)* | `NaN`     | `true`      |

```javascript
// Conversions and Equality

null == undefined // => true: These two values are treated as equal.
"0" == 0          // => true: String converts to a number before comparing.
0 == false        // => true: Boolean converts to number before comparing.
"0" == false      // => true: Both operands convert to 0 before comparing!

Number("3")    // => 3
String(false)  // => "false":  Or use false.toString()
Boolean([])    // => true

x + ""   // => String(x)
+x       // => Number(x)
x-0      // => Number(x)
!!x      // => Boolean(x): Note double !

let n = 17;
let binary = "0b" + n.toString(2);  // binary == "0b10001"
let octal = "0o" + n.toString(8);   // octal == "0o21"
let hex = "0x" + n.toString(16);    // hex == "0x11"

let n = 123456.789;
n.toFixed(0)         // => "123457"
n.toFixed(2)         // => "123456.79"
n.toFixed(5)         // => "123456.78900"
n.toExponential(1)   // => "1.2e+5"
n.toExponential(3)   // => "1.235e+5"
n.toPrecision(4)     // => "1.235e+5"
n.toPrecision(7)     // => "123456.8"
n.toPrecision(10)    // => "123456.7890"

parseInt("3 blind mice")     // => 3
parseFloat(" 3.14 meters")   // => 3.14
parseInt("-12.34")           // => -12
parseInt("0xFF")             // => 255
parseInt("0xff")             // => 255
parseInt("-0XFF")            // => -255
parseFloat(".1")             // => 0.1
parseInt("0.1")              // => 0
parseInt(".1")               // => NaN: integers can't start with "."
parseFloat("$72.47")         // => NaN: numbers can't start with "$"

parseInt("11", 2)     // => 3: (1*2 + 1)
parseInt("ff", 16)    // => 255: (15*16 + 15)
parseInt("zz", 36)    // => 1295: (35*36 + 35)
parseInt("077", 8)    // => 63: (7*8 + 7)
parseInt("077", 10)   // => 77: (7*10 + 7)


```

```javascript
// Object to Primitive Conversions

/*
The JavaScript specification defines three fundamental algorithms for converting objects to primitive values:

prefer-string
This algorithm returns a primitive value, preferring a string value, if a conversion to string is possible.

prefer-number
This algorithm returns a primitive value, preferring a number, if such a conversion is possible.

no-preference
This algorithm expresses no preference about what type of primitive value is desired, and classes can define their own conversions. Of the built-in JavaScript types, all except Date implement this algorithm as prefer-number. The Date class implements this algorithm as prefer-string.
*/
```

```javascript
// The toString() and valueOf() methods

({x: 1, y: 2}).toString()    // => "[object Object]"

[1,2,3].toString()                  // => "1,2,3"
(function(x) { f(x); }).toString()  // => "function(x) { f(x); }"
/\d+/g.toString()                   // => "/\\d+/g"
let d = new Date(2020,0,1);
d.toString()  // => "Wed Jan 01 2020 00:00:00 GMT-0800 (Pacific Standard Time)"

let d = new Date(2010, 0, 1);   // January 1, 2010, (Pacific time)
d.valueOf()                     // => 1262332800000

```

```javascript
// Declarations with let and const

let i;
let sum;

let message = "hello";
let i = 0, j = 0, k = 0;
let x = 2, y = x*x; // Initializers can use previously declared variables

const H0 = 74;         // Hubble constant (km/s/Mpc)
const C = 299792.458;  // Speed of light in a vacuum (km/s)
const AU = 1.496E8;    // Astronomical Unit: distance to the sun (km)

for(let i = 0, len = data.length; i < len; i++) console.log(data[i]);
for(let datum of data) console.log(datum);
for(let property in object) console.log(property);

for(const datum of data) console.log(datum);
for(const property in object) console.log(property);

const x = 1;        // Declare x as a global constant
if (x === 1) {
    let x = 2;      // Inside a block x can refer to a different value
    console.log(x); // Prints 2
}
console.log(x);     // Prints 1: we're back in the global scope now
let x = 3;          // ERROR! Syntax error trying to re-declare x

let i = 10;
i = "ten";

```

```javascript
// Variable Declarations with var

var x;
var data = [], count = data.length;
for(var i = 0; i < count; i++) console.log(data[i]);

```

```javascript
// Destructuring Assignment

let [x,y] = [1,2];  // Same as let x=1, y=2
[x,y] = [x+1,y+1];  // Same as x = x + 1, y = y + 1
[x,y] = [y,x];      // Swap the value of the two variables
[x,y]               // => [3,2]: the incremented and swapped values

// Convert [x,y] coordinates to [r,theta] polar coordinates
function toPolar(x, y) {
    return [Math.sqrt(x*x+y*y), Math.atan2(y,x)];
}

// Convert polar to Cartesian coordinates
function toCartesian(r, theta) {
    return [r*Math.cos(theta), r*Math.sin(theta)];
}

let [r,theta] = toPolar(1.0, 1.0);  // r == Math.sqrt(2); theta == Math.PI/4
let [x,y] = toCartesian(r,theta);   // [x, y] == [1.0, 1,0]

let o = { x: 1, y: 2 }; // The object we'll loop over
for(const [name, value] of Object.entries(o)) {
    console.log(name, value); // Prints "x 1" and "y 2"
}

let [x,y] = [1];     // x == 1; y == undefined
[x,y] = [1,2,3];     // x == 1; y == 2
[,x,,y] = [1,2,3,4]; // x == 2; y == 4

let [x, ...y] = [1,2,3,4];  // y == [2,3,4]

let [a, [b, c]] = [1, [2,2.5], 3]; // a == 1; b == 2; c == 2.5

let [first, ...rest] = "Hello"; // first == "H"; rest == ["e","l","l","o"]

let transparent = {r: 0.0, g: 0.0, b: 0.0, a: 1.0}; // A RGBA color
let {r, g, b} = transparent;  // r == 0.0; g == 0.0; b == 0.0

// Same as const sin=Math.sin, cos=Math.cos, tan=Math.tan
const {sin, cos, tan} = Math;

// Same as const cosine = Math.cos, tangent = Math.tan;
const { cos: cosine, tan: tangent } = Math;

let points = [{x: 1, y: 2}, {x: 3, y: 4}];     // An array of two point objects
let [{x: x1, y: y1}, {x: x2, y: y2}] = points; // destructured into 4 variables.
(x1 === 1 && y1 === 2 && x2 === 3 && y2 === 4) // => true

let points = { p1: [1,2], p2: [3,4] };         // An object with 2 array props
let { p1: [x1, y1], p2: [x2, y2] } = points;   // destructured into 4 vars
(x1 === 1 && y1 === 2 && x2 === 3 && y2 === 4) // => true

// Start with a data structure and a complex destructuring
let points = [{x: 1, y: 2}, {x: 3, y: 4}];
let [{x: x1, y: y1}, {x: x2, y: y2}] = points;

// Check your destructuring syntax by flipping the assignment around
let points2 = [{x: x1, y: y1}, {x: x2, y: y2}]; // points2 == points
```
