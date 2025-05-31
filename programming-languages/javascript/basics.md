# JavaScript Fundamentals

## Introduction

<aside>
💡 JAVASCRIPT is not related to JAVA. It is merely a marketing maneuver by the company to create a sense of familiarity as JAVA was extremely popular at the time. However, JAVASCRIPT has similar syntax & features like JAVA but focuses more on web designing.
</aside>

<aside>
💡 ES6 introduces us to many great features like arrow functions, template strings, class destruction, Modules… and more.

JAVASCRIPT implements the standard called ES6 (Basically the terms 'ES6 & JAVASCRIPT' are used interchangeably. From what I understand, **ES6 merely adds more features to JS ← oversimplified though**)
</aside>

## Basic Syntax

| code | meaning | JAVA Equivalent or Additional Notes |
| --- | --- | --- |
| console.log() | outputs a message to the web console | System.out.println(); |
| var | declares a variable **globally**, or locally to an entire function regardless of block scope  | Ex: A var variable declared inside of a for loop would be accessible outside of the for loop |
| let | allows you to declare variables that are **limited** to the scope of a block statement, or expression on which it is used.  | —> String, Integer, Boolean, Undefined, Null, Symbol.  It is also important to mention that the let is **dynamic**. For example, you can switch an integer to a boolean.  |
| const | Const is another keyword to declare a variable when you **do not want to change** the value of that variable for the whole program. However, constant does not stop us from modifying the contents of an array. | final  |
| x++, x— | increments one, or decrements one | x++, x— |
| x += 10 | x = x + 10 |  |
| >, >= ,<, <= |  |  |
| x === y, x !== y | Strict Equality (Type + Value) | console.log(1 === 1); → true
console.log('1' === 1); → false |
| x == y, x != y | Lost Equality (Value) | console.log(1 === 1); → true
console.log('1' === 1); → true
console.log(true == 1); → true |
| x ** y | x power by y |  |

<aside>
💡 For JavaScript, when dividing, if the value returned is a decimal, the value returned also turn into a double (if not it stays an integer). For example, console.log(62 / 10); would return 6.2. So unlike in JAVA, we instead use the **Math.floor()** function to round down to the nearest ones place. Ex: Math.floor(1.3) would equal to 1.
</aside>

<aside>
💡 console.error() displays an error message of your choice. Ex: console.error('Invalid syntax'); // Invalid syntax error
</aside> 