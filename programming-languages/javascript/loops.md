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

## Do...while Loop

The do...while loop is very useful when you want to execute statements at least once.

```javascript
let i = 9;
do {
    if (i % 2 !== 0) console.log(i);
    i++;
} while (i <= 5);
```

## For...in Loop

The for...in loop is used to loop through the properties of an object.

```javascript
const person = {
    name: 'Jiwon',
    age: 16
};

for (let key in person)
    console.log(key, person[key]);
// name Jiwon
// age 16
```

## For...of Loop

The for...of loop is the ideal way to iterate over an array.

```javascript
const colors = ['red', 'green', 'blue'];

for (let color of colors)
    console.log(color);

// red
// green
// blue
```

## Traditional For Loop

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

## While Loop

```javascript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

## Loop Control Statements

### break
The break statement is used to exit a loop early.

```javascript
for (let i = 0; i < 5; i++) {
    if (i === 3) break;
    console.log(i);
}
// Output: 0, 1, 2
```

### continue
The continue statement is used to skip the current iteration and continue with the next one.

```javascript
for (let i = 0; i < 5; i++) {
    if (i === 3) continue;
    console.log(i);
}
// Output: 0, 1, 2, 4
```

## Loop Best Practices

1. Use for...of for arrays
2. Use for...in for objects
3. Use while when you don't know the number of iterations
4. Use do...while when you want to execute at least once
5. Use break and continue carefully
6. Avoid infinite loops
7. Use meaningful variable names for loop counters 