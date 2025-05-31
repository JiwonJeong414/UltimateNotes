# JavaScript Functions

## Function Declarations vs Function Expressions

```javascript
// Function Declaration
walk(); // 'walk'

function walk() {
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

## Arguments

In JavaScript, since the language is dynamic, we can pass any # of parameters in to a function even though that function may only take for example 2 parameters.

```javascript
function sum(a, b) {
    return a + b;
}

console.log(sum(1)); // this will print NaN or not a number b/c the second parameter will automatically be initalized to undefined
console.log(sum(1, 2, 3)); // this will print 3
```

If we want to use every parameter in our called code, we have to use the arguments object:

```javascript
function sum() {
    let total = 0;
    for (let value of arguments)
        total += value;
    return total;
}

console.log(sum(1, 2, 3, 4, 5, 10)); // 25
```

## Rest Operator

We can simplify the above code by using the rest operator:

```javascript
function sum(...args) { 
    console.log(args); // the rest operator will get all the operators and put them in an array
    return args.reduce((a,b) => a + b); // getting the sum
}

console.log(sum(1, 2, 3, 4, 5, 10));
```

## Default Parameters

Starting from ES6, we have a cleaner way to initialize default values:

```javascript
function interest(principal, rate = 3.5, years = 5) {
    return principal * rate / 100 * years;
}

console.log(interest(10000)); // 1750
```

## Getters & Setters

We use getters to access properties and setters to change or mutate the properties:

```javascript
const person = {
    firstName: 'Mosh',
    lastName: 'Hamedani',
    get fullName() {
        return `${person.firstName} ${person.lastName}`;
    },
    set fullName(value) {
        const parts = value.split(' ');
        this.firstName = parts[0];
        this.lastName = parts[1];
    }
};

person.fullName = 'John Smith';
```

## Arrow Functions

Arrow functions provide a more concise syntax for writing function expressions:

```javascript
// Traditional function
const add = function(a, b) {
    return a + b;
};

// Arrow function
const add = (a, b) => a + b;

// With multiple lines
const add = (a, b) => {
    const sum = a + b;
    return sum;
};
```

## Function Best Practices

1. Use meaningful function names
2. Keep functions small and focused
3. Use default parameters instead of conditional logic
4. Use rest parameters for variable arguments
5. Use arrow functions for callbacks
6. Use getters and setters for computed properties
7. Document complex functions with comments 