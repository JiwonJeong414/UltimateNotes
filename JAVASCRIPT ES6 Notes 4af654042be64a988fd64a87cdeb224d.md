# JAVASCRIPT ES6 Notes

<aside>
💡 JAVASCRIPT is not related to JAVA. It is merely a marketing maneuver by the company to create a sense of familiarity as JAVA was extremely popular at the time. However, JAVASCRIPT has similar syntax & features like JAVA but focuses more on web designing.

</aside>

<aside>
💡 ES6 introduces us to many great features like arrow functions, template strings, class destruction, Modules… and more.

JAVASCRIPT implements the standard called ES6 (Basically the terms ‘ES6 & JAVASCRIPT’ are used interchangeably. From what I understand, **ES6 merely adds more features to JS ← oversimplified though**)

</aside>

<aside>
💡 Some Features specific to JS - ‘this’ keyword, filter, map & reduce

Some Features specific to ES6 - let & const, arrow functions, template literals, default parameters, object literals, rest & spread operators, destructuring assignment

</aside>

## JS Fundamentals

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
console.log(‘1’ === 1); → false |
| x == y, x != y | Lost Equality (Value) | console.log(1 === 1); → true
console.log(‘1’ === 1); → true
console.log(true == 1); → true |
| x ** y | x power by y |  |
| for loop vs while loop | In for loops, the loop variable is part of the loop itself, In while loops, you have to declare the variable externally. |  |
| if & else | Ternary Operators may be more efficient |  |
| break; continue; | breaks the loops, continues a loop |  |
| typeof | a JavaScript keyword that will return the type of a variable when you call it | you can also do something like this typeof x === “string” or typeof x === “number” to find out if something is string or an integer. |

<aside>
💡 For JavaScript, when dividing, if the value returned is a decimal, the value returned also turn into a double (if not it stays an integer). For example, console.log(62 / 10); would return 6.2. So unlike in JAVA, we instead use the **Math.floor()** function to round down to the nearest ones place. Ex: Math.floor(1.3) would equal to 1.

</aside>

<aside>
💡 console.error() displays an error message of your choice. Ex: console.error(’Invalid syntax’); // Invalid syntax error

</aside>

## Value vs Reference Types

Value/Primitive Types

- Number
- String
- Boolean
- Symbol
- undefined
- null

Reference Types

- Object
- Function
- Array

```jsx
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

### Conclusion

<aside>
💡 **Primitives** are copied by their **value**

</aside>

<aside>
💡 **Objects** are copied by their **reference**

</aside>

Another Example

```jsx
let number = 10;

function increase(number) {
 	number++;
}
// the value is copied into the parameter
increase(number);
console.log(number);
// 10
```

```jsx
let obj = 10;

function increase(obj) { 
	obj++;
}
//the parameter points to the same object defined above
increase(obj);
console.log(obj);
// {value: 11}
```

## Dot Notation, Bracket Notation

For getting the value of properties

```jsx
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

```jsx
let points = 110;
let type = points > 100 ? 'gold' : ' silver';
// if points is greater than 100, type = 'gold'; if points is less than or equal to 100, type = 'silver'
// ? = if
// : = else
```

> Extra: Write a program to find the smallest of three numbers using ternary operators
> 

`let min = x < y ? x < z ? x : z : y < z ? y : z;`

## Do…while, For…in, For… of Loops

 do while loop → very useful

- statements are executed at least once

```jsx
let i = 9;
do {
	if (i % 2 !== 0) console.log(i);
	i++;
} while (i <= 5);
```

For…in loop

- loops through the properties of an object.

```jsx
const person = {
	name: 'Jiwon',
	age: 16
};

for (let key in person)
	console.log(key, person[key]);
// name Jiwon
// age 16
```

For…of loop

- Ideal way to iterate over an array

```jsx
const colors = ['red', 'green', 'blue'];

for (let color of colors)
	console.log(color);

// red
// green
// blue
```

## Functions

A function is basically a set of statements that performs a task or calculates a value

```jsx
greet('Jiwon');

function greet(name) {
	console.log('Hello ' + name);
}

// Hello Jiwon
```

- Max of Two Numbers

```jsx
console.log(maxOfTwo(5, 1));

function maxOfTwo(a, b) {
  return a > b ? a : b;
}
```

- Determine if landscape

```jsx
function isLandscape(width, height) {
  return width > height;
}

// you can just write the conditional statement rather than writing an entire if statement or a terrnary operator
```

<aside>
💡 One of the confusing concepts in JavaScript is that functions are objects

</aside>

## Object Literals

In Java, **an object is created from a class** (class is a blueprint for objects)
Each **object** has an identity, a behavior and a state. The state of an object is stored in fields (variables), while methods (functions) display the object's behavior.

In JAVASCRIPT, we can manually create individual objects using Object Literals Syntax. For example:

```jsx
const circle = {
	radius:1,
	location: {
		x: 1,
		y: 1
	},
	isVisible: true,
	draw: function(){
		console.log('draw');
	}
}

// All of these are part of a circle object
```

When we create an object using the Object Literals Syntax, internally, the JavaScript engine uses the constructor function

```jsx
circle.constructor
--> f Object();
```

### Cloning an Object

This is an example of cloning an object:

```jsx
const circle = {
	radius: 1,
	draw() {
		console.log('draw');
	}
};

const another = Object.assign({}, circle); // the {} represents an empty object passed
```

Another Example:

```jsx
// spread operator
const another = {...circle};
```

### Math Object

- Website to find all the built-in objects in JavaScript
    
    [Math - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
    

Some useful methods:

- Math.random() // random # between 0-0.99
- Math.round(1.9) —> 2
- Math.max(1, 2, 3, 4, 5); —> 5
- Math.min(1, 2, 3, 4, 5); —> 1

### String Object

While String is a primitive type, it also has an object type

```jsx
// String primitive
const message = 'hi';

// String object
const another = new String('hi');
```

<aside>
💡 However, when we try to call a String object method from the a String primitive variable, JavaScript automatically wraps the primitive type into a String object.

</aside>

Some Useful String Methods:

> const message = ‘This is my first message’;
> 
- message.length // 24
- message[0] // “T”
- message.includes(’my’); // true
- message.startsWith(’This’); // true
- message.indexOf(’my’); // 8
- message.replace(’first’, ‘second’); // This is my second message * note that this doesn’t change the original string
- message.toUpperCase(); // THIS IS MY FIRST MESSAGE
- message.split(); // returns a string array [”This”, “is”, “my”, “first”, message”]

### Date Object

```jsx
const now = new Date() // without parameter --> current date time
const date1 = new Date('June 2 2022 9:00');

console.log(now.toDateString()); // Sat Jul 02 2022
console.log(now.toTimeString()); // 21:35:39 GMT-0700 (Pacific Daylight Time)
console.log(now.toISOString()); // 2022-07-03T04:35:39.460Z
// last one is for back-end developing
```

## Factory Functions

However, what if we want to change the value of an object depending on the parameter or create multiple objects w/ the same blueprints? Then, we use the factory function

```jsx
// Factory Function
function createCircle(radius) {
	return {
		// in JS, if our key & value are the same, we can simply put the key in		
		radius, // equivalent to radius: radius
		draw() { // equivalent to function draw()
			console.log('draw');
		}
}

const circle1 = createCircle(1);
const circle2 = createCirlce(2);
```

## Constructor Functions

Constructor Functions serves an equal purpose with the Factory Functions.

Both of these functions are equally good at creating objects but people who are familiar with JAVA, have easier time using the Constructor Function.

```jsx
// Constructor Function
function Circle(radius) {
	this.radius = radius; //since js is dynamic, we can add properties by using the this keyword
	// js will automatically add the radius property to our circle object
	this.draw = function() {
		console.log('draw');
	}
} 

const circle = new Circle(1);
```

<aside>
💡 Just want to emphasize the point that objects are dynamic in JS. For example, look the code below:

</aside>

```jsx
const circle = {
	radius: 1
};

circle.color = 'yellow';

console.log(circle);
// {radius: 1, color: "yellow}
// wecan also delete properties
delete circle.color;
```

## Template Literals

We have so far learned 

- Object Literals - {}
- Boolean Literals - true, false
- String Literals - ‘ ‘, “”

Starting from ES6, we have the Template Literals

Template literals are literals delimited with backtick (`) characters, allowing for multi-line strings, for string interpolation with embedded expressions, and for special constructs called tagged templates

Lets take writing an email as an example:

```jsx
const another = 
`Hi John,

Thank you for joining my mailing list

Regards,
Risabh`;
```

Also, with a template literal, adding placeholder is much easier

```jsx
const name = 'John';

const another = 
`Hi ${name}`;
```

## Arrays

We have learned that Arrays are Objects. So by using the dot notation, we can access the methods of an array

### Adding Elements

```jsx
const numbers = [3, 4];

// End
numbers.push(5, 6); // 3, 4, 5, 6
// Beginning
numbers.unshift(1, 2); // 1, 2, 3, 4, 5, 6
// Middle
numbers.splice(2, 0, 'a', 'b'); // 1, 2, a, b, 3, 4, 5, 6
```

<aside>
💡 Adding to the middle of an array is quite different. The first parameter represents the index where you want to add. The second parameter represents how many items you want to delete. Finally, the last parameter represents the items you want to add.

</aside>

### Finding Elements - Primitives

```jsx
const numbers = [1, 2, 3, 1, 4];

numbers.indexOf(1); // 0
numbers.lastIndexOf(1); // 3

numbers.indexOf(1, 2); // 3 (the second parameter represents which index the search will begin at)

console.log(numbers.includes(1)); // true
```

### Finding Elements - Reference Types

- Mozilla Guide
    
    [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
    

```jsx
const courses = [
	{ id: 1, name: 'a'},
	{ id: 2, name: 'b'},
];

const course = courses.find(function(course) {
	return course.name === 'a'; // returns the first element in the provided array that satisfies the provided testing function.
});

console.log(course); // { id: 1, name: 'a' }

const course = courses.findIndex(function(course) {
	return course.name === 'a'; // returns the first element in the provided array that satisfies the provided testing function.
});

console.log(course); // 0
```

### Arrow Functions

In ES6, to write the same code above using **Arrow Functions**

```jsx
const course = courses.find(course => course.name === 'a');
```

### Removing Elements

```jsx
const numbers = [1, 2, 3, 4];

// End
const last = numbers.pop(); // 1, 2, 3
// last = 4
// Beginning
const first = numbers.shift(); // 2, 3
// first = 1
// Middle 
numbers.splice(1, 1); // 2
```

### Emptying an Array

```jsx
let numbers = [1, 2, 3, 4];

numbers.length = 0;
```

### Combining & Slicing Arrays

```jsx
// Combining
const first = [1, 2, 3];
const second = [4, 5, 6];

const combined = first.concat(second); // 1, 2, 3, 4, 5, 6

// Sliced
const sliced - combined.slice(2, 4); // 3, 4
```

### The Spread Operator

Starting with ES6, there is another way to combine an array

```jsx
const first = [1, 2, 3];
const second = [4, 5, 6];

// Combining
const combined = [...first, ...second];
```

With the Spread Operator, we have more flexibility. Lets say we want to add an element between first & second

```jsx
const combined = [...first, 'a', ...second, 'b'];
```

To make a copy,

```jsx
const copy = [...combined];
```

### Iterating Array

```jsx
const numbers = [1, 2, 3];

// Option 1
for (let number of numbers)
	console.log(number);

// Option 2
numbers.forEach(function(number) {
	console.log(number);
});

// Option 3
numbers.forEach(number => console.log(number));
```

### Join Method

The join() method creates and returns a new string by concatenating all of the elements in an array

```jsx
const numbers = [1, 2, 3];
const joined = numbers.join(',');
console.log(joined); // 1,2,3
```

### Sorting Arrays

For Strings & Integers

```jsx
const numbers = [2, 3, 1];
numbers.sort(); // 1, 2, 3

numbers.reverse(); // 3, 2, 1
```

For Objects

```jsx
const courses = [
	{ id: 1, name: 'Node.js' },
	{ id: 2, name: 'JavaScript' },
];

console.sort(function(a, b) {
	// a < b => -1
	// a > b => 1
	// a === b => 0
	if(a.name < b.name) return -1;
	if(a.name > b.name) return 1;
	return 0;
});
```

### Debugging/Testing Arrays

Suppose you want to check if all values in the array are positive

```jsx
const numbers = [1, 3, 2];

const allPositive = numbers.every(function(value) {
	return value >= 0;
}); // true
```

For Checking at least one element in the array is positive

```jsx
const somePositive = numbers.some(function(value) {
	return value >= 0;
}); // true
```

### Filtering an Array

How to filter an array based on a search criteria

Lets suppose you only want to return the positive numbers

```jsx
const numbers = [1, -1, 2, 3];

const filtered = numbers.filter(value => value >= 0);

console.log(filtered); // [1, 2, 3];
```

### Mapping an Array

Lets say you want to construct some HTML markup using the element of an array

```jsx
const numbers = [1, 2, 3];

const items = numbers.map(n => '<li>' + n + '</li>');

console.log(items);
// <li>1</li>, <li>2</li>, <li>3</li>
```

What about mapping each value into an object?

```jsx
const items = numbers.map(n => ({ value: n })); // have to use () on curly braces
}); 

console.log(items);
// {value: 1}, {value: 2}, {value: 3}
```

<aside>
💡 Chaining: Suppose you want to implement multiple methods to an array. We can use chaining for this purpose.

</aside>

```jsx
const numbers = [1, -1, 2, 3];

numbers
	.filter(n => n >= 0)
	.map(n => ({ value: n}))
	.filter(obj => obj.value > 1)
	.map(obj => obj.value);

console.log(items); // [2, 3]
```

### Reducing an Array

Suppose we want to add up all the value in an array. The reduce method reduces every value into a single value.

```jsx
const numbers = [1, -1, 2, 3];

numbers.reduce((accumulator, currentValue) => accumulator + currentValue); // 5
```

### Array Destructuring

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

## Functions

### Function Declarations vs Function Expressions

```jsx
// Function Declaration
walk(); // 'walk'

function walk(){
    console.log('walk');
}

run(); // error: not defined

// Function Expression
let run = function() {
    console.log('run');
};
```

<aside>
💡 Hoisting is when the JavaScript engine executes the code, it moves all the function declaration to the top. So that is why we were able to access our function declaration, walk(), but not the function expression run().

</aside>

### Arguments

In JavaScript, since the language is dynamic, we can pass any # of parameters in to a function even though that function may only take for example 2 parameters. Take the sum function below:

```jsx
function sum(a, b) {
	return a + b;
}

console.log(sum(1)); // this will print NaN or not a number b/c the second parameter will automatically be initalized to undefined
console.log(sum(1, 2, 3)); // this will print 3
```

If we want to use every parameter in our called code, we have to use the arguments object.

```jsx
function sum() {
	let total = 0;
	for (let value of arguments)
		total += value;
	return total;
}

console.log(sum(1, 2, 3, 4, 5, 10)); // 25
```

### Rest Operator

We can simplify the above code by using the rest operator.

```jsx
function sum(...args) { 
	console.log(args); // the rest operator will get all the operators and put them in an array
	args.reduce((a,b) => a + b); // getting the sum
}

console.log(sum(1, 2, 3, 4, 5, 10));
```

### Default Value

Starting from ES6, we have a cleaner way to initialize default values

```jsx
function interest(principal, rate = 3.5, years = 5) {
	return principal * rate / 100 * years;
}

console.log(interest(10000)); // 1750
```

### Getters & Setters

We use getters to access properties and setters to change or mutate the properties

```jsx
const person = {
	firstName: 'Mosh',
	lastName: 'Hamedani',
	get fullName() {
		return '${person.firstName} $person.lastName}';
	}
	set fullName(value) {
		const parts = value.split(' ');
		this.firstName = parts[0];
		this.lastName = parts[1];
	}
};

person.fullName = 'John Smith';
```

## ‘this’ keyword

this is a reference to the object that is executing the piece of code

by alone, this references to an empty object

Functions - 10