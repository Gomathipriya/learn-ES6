# learn-ES6

## JavaScript Overview

* Object based scripting language
* Makes a Website alive by being dynamic and interactive
* <script> inside HTML runs automatically on page load
* Then - LiveScript - Younger brother to Java - Now - FullyIndependent (ECMAScript)
* Latest version ES10 (June 2019) , Major version ES6 (June 2015), ES.Next (future proposals)

|   Client side scripting       |  Server side scripting        |
| ------------------------------| ------------------------------|
| Web browser                   | Server                        |
| Control Browser and DOM eg, mouse click,form input |  Communicate with DB, file manipulation     |

### JavaScript Engine

* Helps to execute JS on browser(embeded in browser) and server
* Read/Parse script -> convert/compile script to machine language -> machine code executes faster to provide result
* Different JSEngines

| Engine      | Browser      |
| V8          | Chrome/Opera |
| SpiderMonkey| Firefox      |
| Trident/Chakra | IE        |
| Chakra Core | Edge         |
| Nitro & Squirrel Fish | Safari      |

### Advantages

* Less server interaction - validation of input on client side
* Immediate feedback - No need to reload the page
* Increased interactivity
* Rich UI

### Notes

* Different tabs or Windows dont know each other, we can open one page from another but not accessing JS across both (different site/domain/port)
* Above can be achieved by "Same Origin Policy" - Special JS - Both the pages agree for data exchange
[gmail cant access user account info related to youtube and vice versa ]
* CORS ( Cross Origin Resource Sharing) - receive data from other sites/domain. Can be done by explicit agreement in HTTP headers

## Object Oriented JavaScript

![OOPS](/OOPS.jpg)

namespace - specific name to refer
encapsulation - Wrapping properties and functions within single unit
abstraction - creating simple model for complex things ( most important aspect)
polymorphism - more than one form 
inheritance - reuse or inherit certain properties from others

### Data types

* When adding a number and a string, JavaScript will treat the number as a string.
* JavaScript evaluates expressions from left to right. Different sequences can produce different results
```
  var x = 16 + 4 + "Volvo"; // 20Volvo
  var x = "Volvo" + 16 + 4; //Volvo164
```
* dynamic types - infer variable types at runtime 
```
  var x;           // Now x is undefined
  x = 5;           // Now x is a Number
  x = "John";      // Now x is a String
```
* Weakly typed -  allow types to be inferred as another type - same variable can be used to hold different data types 
* primitive data - simple data value with no additional properties and methods - immutable.
```
typeof "John"              // Returns "string"
typeof 3.14                // Returns "number"
typeof true                // Returns "boolean"
typeof x                   // Returns "undefined" (if x has no value)
```
* Complex Data
```
typeof {name:'John', age:34} // Returns "object"
typeof [1,2,3,4]             // Returns "object" (not "array", see note below)
typeof null                  // Returns "object"
typeof function myFunc(){}   // Returns "function"
```
* Statically typed means the type is enforced  - eg Typescript
```
int x = 5
string y = 'abc'
```

### Variables

* containers for storing data values.
* must be identified with unique names - identifiers - case-sensitive
* Declaration - Creating a variable in JavaScript 
* Definition - assigning a value to a variable
* re-declare a JavaScript variable will not lose its value
* If you put a number in quotes, the rest of the numbers will be treated as strings, and concatenated
* local variable - declared inside block or function - accessible within the function or block only
```
function abc(){  
var x=10;//local variable  
}  
```
* global variable - accessible from any function - declared outside the function or declared with window object
```
var data=200;//gloabal variable  
function a(){  
alert(window.data);//accessing global variable 
console.log(data);  
}  
function b(){  
console.log(data);  
}  
a();//calling JavaScript function  
b(); 
```
* To declare JavaScript global variables inside function - use Window Object
```
function m(){  
window.value=100;//declaring global variable by window object  
}  
```

Note: declare all variables at the beginning of a script

### Use Strict

* JavaScript code should be executed in "strict mode".
* helps to write cleaner code, like preventing from using undeclared variables.
* using undeclared variable or object is not allowed
* "this" object that called the function. If the object is not specified, functions in strict mode will return undefined and functions in normal mode will return the global object (window)

```
// note: no "use strict" in this example
num = 5; // the variable "num" is created if it didn't exist
alert(num); // 5

"use strict";
num = 5; // error: num is not defined

"use strict";
function myFunction() {
  alert(this); // will alert "undefined"
}
myFunction();
```

### Hoisting

* the variable declaration is moved to the top of the function or global code
```
bla = 2;
var bla;

// ...is implicitly understood as:

var bla;
bla = 2;

function do_something() {
  console.log(bar); // undefined
  var bar = 111;
  console.log(bar); // 111
}

// ...is implicitly understood as:

function do_something() {
  var bar;
  console.log(bar); // undefined
  bar = 111;
  console.log(bar); // 111
}
```

Note: recommended to always declare variables at the top of their scope - so it's clear which variables are function scoped (local) and which are resolved on the scope chain

### String

* length - returns the length of a string
* indexOf() - returns the index of (the position of) the first occurrence of a specified text in a string
```
var txt = "Hello World!";
var sln = txt.length; // 12
txt.indexOf("World"); //6
```
https://www.w3schools.com/jsref/jsref_obj_string.asp
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String

### Array

* JavaScript does not support arrays with named indexes.It supports only numbered indexes.
* map method takes in an array, and creates a new array with the results of calling a function for every element in that array
* Array.filter() is another useful method. It works by creating a new array from the original of all the elements in that array that pass a test implemented by the provided function
```
a = [1, 2, 3];

b = a.map(function(x) { return x*x; });  // b is [1, 4, 9]
```
* reduce takes in an array, applies a function against something called an accumulator (more on that in a second), and each element in the array, and reduces it down to a single value.
eg adding up numbers in an array

```
a = [5, 4, 3, 2, 1];

smallvalues = a.filter(function(x) { return x < 3 });   // [2, 1]
```
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array

### Objects

* Objects are mutable: They are addressed by reference, not by value.

```
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}

var x = person;
x.age = 10;           // This will change both x.age and person.age
```

### Prototype 

* All JavaScript objects inherit properties and methods from a prototype:
  Date objects inherit from Date.prototype
  Array objects inherit from Array.prototype
* Object.prototype is on the top of the prototype inheritance chain
* allows to add new methods to objects constructors

```
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

Person.prototype.nationality = "English";
```
