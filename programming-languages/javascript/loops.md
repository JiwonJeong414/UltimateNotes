# JavaScript Loops

## For Loops

The for loop is used when you know how many times you want to execute a block of code.

```javascript
// Basic for loop
for (let i = 0; i < 5; i++) {
    console.log(i);
}

// For...of loop (ES6)
const colors = ['red', 'green', 'blue'];
for (let color of colors) {
    console.log(color);
}

// For...in loop (for objects)
const person = {
    name: 'John',
    age: 30
};
for (let key in person) {
    console.log(key, person[key]);
}
```

## While Loops

The while loop is used when you want to execute a block of code as long as a condition is true.

```javascript
// Basic while loop
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}

// Do...while loop
let j = 0;
do {
    console.log(j);
    j++;
} while (j < 5);
```

## Loop Control Statements

- `break`: Exits the loop completely
- `continue`: Skips the current iteration and continues with the next one

```javascript
// Break example
for (let i = 0; i < 10; i++) {
    if (i === 5) break;
    console.log(i);
}

// Continue example
for (let i = 0; i < 5; i++) {
    if (i === 2) continue;
    console.log(i);
}
```

## Common Loop Patterns

### Iterating Arrays
```javascript
const numbers = [1, 2, 3, 4, 5];

// Using for...of
for (let num of numbers) {
    console.log(num);
}

// Using forEach
numbers.forEach(num => console.log(num));
```

### Iterating Objects
```javascript
const person = {
    name: 'John',
    age: 30,
    city: 'New York'
};

// Using for...in
for (let key in person) {
    console.log(`${key}: ${person[key]}`);
}

// Using Object.entries
Object.entries(person).forEach(([key, value]) => {
    console.log(`${key}: ${value}`);
});
``` 