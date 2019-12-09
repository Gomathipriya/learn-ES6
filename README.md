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
| ------------| -------------|
| V8          | Chrome/Opera |
| SpiderMonkey| Firefox      |
| Trident/Chakra | IE        |
| Chakra Core | Edge         |
| Nitro & Squirrel Fish | Safari       |

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

### Regular expressions

* Patterns used to match character combinations in strings
* Regular expressions are also objects
```
var re = /ab+c/;
var re = new RegExp('ab+c');

// The string:
var str = "Hello world!";

// Look for "Hello"
var patt = /Hello/g;
var result = patt.test(str);

// Look for "W3Schools"
patt2 = /W3Schools/g;
result2 = patt2.test(str);
```

### Functions

* block of code designed to perform a particular task
* parameters are listed inside the parentheses () in the function definition.
* arguments are the values received by the function when it is invoked.
* When JavaScript reaches a return statement, the function will stop executing.
*  Define the code once, and use it many times.


```
function myFunction(p1, p2) {
  return p1 * p2;   // The function returns the product of p1 and p2
}
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

### BOM & DOM

#### Browser Object Model (BOM)
* allows JavaScript to "talk to" the browser
* All global JavaScript objects, functions, and variables automatically become members of the window object.
* Even the document object (of the HTML DOM) is a property of the window object

```
window.document.getElementById("header");
same as
document.getElementById("header");

window.open() - open a new window
window.close() - close the current window
window.moveTo() - move the current window
window.resizeTo() - resize the current window
```
![BOM](/BOM.JPG)

##### Window.location

* used to get the current page address (URL) and to redirect the browser to a new page

```
window.location.href returns the href (URL) of the current page
window.location.hostname returns the domain name of the web host
window.location.pathname returns the path and filename of the current page
window.location.protocol returns the web protocol used (http: or https:)
window.location.assign() loads a new document

```
##### Window.history

* contains the browsers history
* history.back() - same as clicking back in the browser
* history.forward() - same as clicking forward in the browser

##### Popup Boxes

* Alert Box - to make sure information comes through to the user
* Confirm Box - used if you want the user to verify or accept something
* Prompt Box - used if you want the user to input a value before entering a page

```
window.alert("sometext");
window.confirm("sometext");
window.prompt("sometext","defaultText");
```
##### Timing Events

setTimeout(function, milliseconds)
Executes a function, after waiting a specified number of milliseconds.

setInterval(function, milliseconds)
Same as setTimeout(), but repeats the execution of the function continuously.

#### Document Object Model (DOM)
* a programming interface for HTML and XML documents
*  represents the page so that programs can change the document structure, style, and content
* an object-oriented representation of the web page, which can be modified with a scripting language

```
The HTML elements as objects
The properties of all HTML elements
The methods to access all HTML elements
The events for all HTML elements
```

* A property is a value that you can get or set (like changing the content of an HTML element). e.g. innerHTML
* A method is an action you can do (like add or deleting an HTML element). e.g. getElementById

```
document.getElementById("demo").innerHTML = "Hello World!";
```
![DOM](/DOM.JPG)
![FindHTMLElement](/FindHTMLElement.JPG)
![ChangingHtmlElement](/ChangingHtmlElement.JPG)
![AddDeleteElements](/AddDeleteElements.JPG)

### Event Handling

#### HTML Events

* An HTML web page has finished loading
* An HTML input field was changed
* An HTML button was clicked
```
<button onclick="this.innerHTML=Date()">The time is?</button>
```

#### Common HTML Events

| Event	       |  Description   |
| ------------ | ---------------|
| onchange	   | An HTML element has been changed |
| onclick	     | The user clicks an HTML element  |
| onmouseover	 | The user moves the mouse over an HTML element |
| onmouseout	 | The user moves the mouse away from an HTML element |
| onkeydown	   | The user pushes a keyboard key |
| onload	     | The browser has finished loading the page |

#### HTML DOM EventListener

```
window.addEventListener("resize", function(){
  document.getElementById("demo").innerHTML = Math.random();
});
```

#### Event propagation

* a way of defining the element order when an event occurs
* addEventListener(event, function, useCapture);
* default value is false, which will use the bubbling propagation, when the value is set to true, the event uses the capturing propagation

1. Event Bubbling
   the inner most element's event is handled first and then the outer

2. Event Capturing
   the outer most element's event is handled first and then the inner

```
document.getElementById("myP").addEventListener("click", myFunction, true);
```

### Closure

* combination of a function bundled together (enclosed) with references to its surrounding state
* gives you access to an outer function’s scope from an inner function
* Global variables can be made local (private) with closures.

```
var add = (function () {
  var counter = 0;
  return function () {counter += 1; return counter}
})();

add();
add();
add();

// the counter is now 3

```

### AJAX (Asynchronous JavaScript And XML)

* Read data from a web server - after the page has loaded
* Update a web page without reloading the page
* Send data to a web server - in the background

```
<div id="demo">
<h2>The XMLHttpRequest Object</h2>
<button type="button" onclick="loadDoc()">Change Content</button>
</div>

<script>
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("demo").innerHTML =
      this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
</script>
```

### JSON (JavaScript Object Notation)

* JSON is a syntax for storing and exchanging data.
* JSON is text, written with JavaScript object notation.
* JSON.stringify
* JSON.parse(text)

### Design Patterns
