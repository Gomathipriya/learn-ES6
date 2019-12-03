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
