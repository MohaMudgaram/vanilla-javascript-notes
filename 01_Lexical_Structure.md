# Lexical Structure

```javascript
// Comments

// This is a single-line comment.

/* This is also a comment */  // and here is another comment.

/*
 * This is a multi-line comment. The extra * characters at the start of
 * each line are not a required part of the syntax; they just look cool!
 */
```

```javascript
// Literals

12               // The number twelve
1.2              // The number one point two
"hello world"    // A string of text
'Hi'             // Another string
true             // A Boolean value
false            // The other Boolean value
null             // Absence of an object
```

```javascript
// Identifiers

i
my_variable_name
v13
_dummy
$str
```

```javascript
// Reserved words

as      const      export     get         null     target   void
async   continue   extends    if          of       this     while
await   debugger   false      import      return   throw    with
break   default    finally    in          set      true     yield
case    delete     for        instanceof  static   try
catch   do         from       let         super    typeof
class   else       function   new         switch   var

// Reserved words in future

enum  implements  interface  package  private  protected  public
```

```javascript
// Unicode

const π = 3.14;
const sí = true;

let café = 1; // Define a variable using a Unicode character
caf\u00e9     // => 1; access the variable using an escape sequence
caf\u{E9}     // => 1; another form of the same escape sequence

console.log("\u{1F600}");  // Prints a smiley face emoji

const café = 1;  // This constant is named "caf\u{e9}"
const café = 2;  // This constant is different: "cafe\u{301}"
café  // => 1: this constant has one value
café  // => 2: this indistinguishable constant has a different value
```

```javascript
// Semicolons

a = 3;
b = 4;

a = 3; b = 4;

let a
a
=
3
console.log(a)

let a; a = 3; console.log(a);

let y = x + f
(a+b).toString()

let y = x + f(a+b).toString();

let x = 0                         // Semicolon omitted here
;[x,x+1,x+2].forEach(console.log) // Defensive ; keeps this statement separate

return
true;

return; true;

return true;
```
