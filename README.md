# learn-ES6

## JavaScript Overview

* Object based scripting language
* Makes a Website alive by being dynamic and interactive
* <script> inside HTML runs automatically on page load
* Then - LiveScript - Younger brother to Java - Now - FullyIndependent (ECMAScript)
* Latest version ES10 (June 2019) , Major version ES6 (June 2015), ES.Next (future proposals)

|   Client side scripting       |  Server side scripting       |
| Web browser                   | Server                       |
| Control Browser and DOM eg, mouse click,form input |  Communicate with DB, file manipulation  |

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

## Data types

* When adding a number and a string, JavaScript will treat the number as a string.
* JavaScript evaluates expressions from left to right. Different sequences can produce different results
```
  var x = 16 + 4 + "Volvo"; // 20Volvo
  var x = "Volvo" + 16 + 4; //Volvo164
```
* dynamic types - same variable can be used to hold different data types
```
  var x;           // Now x is undefined
  x = 5;           // Now x is a Number
  x = "John";      // Now x is a String
```
* primitive data - simple data value with no additional properties and methods.
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
