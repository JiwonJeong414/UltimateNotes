# JavaScript Basics

## JS Fundamentals

| code | meaning | JAVA Equivalent or Additional Notes |
| --- | --- | --- |
| console.log() | outputs a message to the web console | System.out.println(); |
| var | declares a variable **globally**, or locally to an entire function regardless of block scope | Ex: A var variable declared inside of a for loop would be accessible outside of the for loop |
| let | allows you to declare variables that are **limited** to the scope of a block statement | —> String, Integer, Boolean, Undefined, Null, Symbol. It is also important to mention that the let is **dynamic**. For example, you can switch an integer to a boolean. |
| const | Const is another keyword to declare a variable when you **do not want to change** the value of that variable for the whole program. However, constant does not stop us from modifying the contents of an array. | final |
| x++, x— | increments one, or decrements one | x++, x— |
| x += 10 | x = x + 10 | |
| >, >= ,<, <= | comparison operators | |
| x === y, x !== y | Strict Equality (Type + Value) | console.log(1 === 1); → true<br>console.log('1' === 1); → false |
| x == y, x != y | Lost Equality (Value) | console.log(1 === 1); → true<br>console.log('1' === 1); → true<br>console.log(true == 1); → true |
| x ** y | x power by y | |
| for loop vs while loop | In for loops, the loop variable is part of the loop itself, In while loops, you have to declare the variable externally. | |
| if & else | Conditional statements | Ternary Operators may be more efficient |
| break; continue; | breaks the loops, continues a loop | |
| typeof | a JavaScript keyword that will return the type of a variable when you call it | you can also do something like this typeof x === "string" or typeof x === "number" to find out if something is string or an integer. |

## Value vs Reference Types

### Value/Primitive Types
- Number
- String
- Boolean
- Symbol
- undefined
- null

### Reference Types
- Object
- Function
- Array

```javascript
// primitive type
let x = 10;
let y = x;

x = 20;

console.log(x); // 20
console.log(y); // 10

// reference type
let x1 = { value: 10 };
let y1 = x1; // both x1 & y1 are pointing to the same object in memory
// when we modify that object using either x1 or y1 the changes are immediately visible to the other variable

x1.value = 20;

console.log(x1); // { value: 20 }
console.log(y1); // { value: 20 }
```

<aside>
💡 **Primitives** are copied by their **value**
</aside>

<aside>
💡 **Objects** are copied by their **reference**
</aside>

## Dot Notation vs Bracket Notation

```javascript
let person = {
    name: 'Jiwon',
    age: 16
};

// Dot Notation --> default choice
person.name = 'John';

// Bracket Notation --> when we don't know what property to access
let selection = 'name';
person[selection] = 'Mary';
```

## Ternary Operators

The conditional (ternary) operator is the only JavaScript operator that takes three operands: a condition followed by a question mark ( ? ), then an expression to execute if the condition is truthy followed by a colon ( : ), and finally the expression to execute if the condition is false.

```javascript
let points = 110;
let type = points > 100 ? 'gold' : 'silver';
// if points is greater than 100, type = 'gold'; if points is less than or equal to 100, type = 'silver'
// ? = if
// : = else
```

## Math Object

Some useful methods:
- Math.random() // random # between 0-0.99
- Math.round(1.9) —> 2
- Math.max(1, 2, 3, 4, 5); —> 5
- Math.min(1, 2, 3, 4, 5); —> 1

## String Object

While String is a primitive type, it also has an object type

```javascript
// String primitive
const message = 'hi';

// String object
const another = new String('hi');
```

<aside>
💡 However, when we try to call a String object method from the a String primitive variable, JavaScript automatically wraps the primitive type into a String object.
</aside>

Some Useful String Methods:

```javascript
const message = 'This is my first message';

message.length // 24
message[0] // "T"
message.includes('my'); // true
message.startsWith('This'); // true
message.indexOf('my'); // 8
message.replace('first', 'second'); // This is my second message * note that this doesn't change the original string
message.toUpperCase(); // THIS IS MY FIRST MESSAGE
message.split(); // returns a string array ["This", "is", "my", "first", message"]
```

## Date Object

```javascript
const now = new Date() // without parameter --> current date time
const date1 = new Date('June 2 2022 9:00');

console.log(now.toDateString()); // Sat Jul 02 2022
console.log(now.toTimeString()); // 21:35:39 GMT-0700 (Pacific Daylight Time)
console.log(now.toISOString()); // 2022-07-03T04:35:39.460Z
// last one is for back-end developing
``` 