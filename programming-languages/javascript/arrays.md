# JavaScript Arrays

## Adding Elements

```javascript
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

## Finding Elements

### Finding Primitive Types
```javascript
const numbers = [1, 2, 3, 1, 4];

numbers.indexOf(1); // 0
numbers.lastIndexOf(1); // 3
numbers.indexOf(1, 2); // 3 (the second parameter represents which index the search will begin at)
console.log(numbers.includes(1)); // true
```

### Finding Reference Types
```javascript
const courses = [
    { id: 1, name: 'a'},
    { id: 2, name: 'b'},
];

// Using find
const course = courses.find(function(course) {
    return course.name === 'a';
});
console.log(course); // { id: 1, name: 'a' }

// Using findIndex
const courseIndex = courses.findIndex(function(course) {
    return course.name === 'a';
});
console.log(courseIndex); // 0

// Using arrow function
const course = courses.find(course => course.name === 'a');
```

## Removing Elements

```javascript
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

## Emptying an Array

```javascript
let numbers = [1, 2, 3, 4];
numbers.length = 0;
```

## Combining & Slicing Arrays

```javascript
// Combining
const first = [1, 2, 3];
const second = [4, 5, 6];

const combined = first.concat(second); // 1, 2, 3, 4, 5, 6

// Slicing
const sliced = combined.slice(2, 4); // 3, 4
```

## The Spread Operator

```javascript
const first = [1, 2, 3];
const second = [4, 5, 6];

// Combining
const combined = [...first, ...second];

// Adding elements between arrays
const combined = [...first, 'a', ...second, 'b'];

// Making a copy
const copy = [...combined];
```

## Iterating Arrays

```javascript
const numbers = [1, 2, 3];

// Option 1: for...of
for (let number of numbers)
    console.log(number);

// Option 2: forEach with function
numbers.forEach(function(number) {
    console.log(number);
});

// Option 3: forEach with arrow function
numbers.forEach(number => console.log(number));
```

## Array Methods

### Join
```javascript
const numbers = [1, 2, 3];
const joined = numbers.join(',');
console.log(joined); // 1,2,3
```

### Sort
```javascript
// For Strings & Integers
const numbers = [2, 3, 1];
numbers.sort(); // 1, 2, 3
numbers.reverse(); // 3, 2, 1

// For Objects
const courses = [
    { id: 1, name: 'Node.js' },
    { id: 2, name: 'JavaScript' },
];

courses.sort(function(a, b) {
    if(a.name < b.name) return -1;
    if(a.name > b.name) return 1;
    return 0;
});
```

### Filter
```javascript
const numbers = [1, -1, 2, 3];
const filtered = numbers.filter(value => value >= 0);
console.log(filtered); // [1, 2, 3]
```

### Map
```javascript
const numbers = [1, 2, 3];

// Mapping to HTML
const items = numbers.map(n => '<li>' + n + '</li>');
console.log(items); // ['<li>1</li>', '<li>2</li>', '<li>3</li>']

// Mapping to objects
const items = numbers.map(n => ({ value: n }));
console.log(items); // [{value: 1}, {value: 2}, {value: 3}]
```

### Reduce
```javascript
const numbers = [1, -1, 2, 3];
const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue);
console.log(sum); // 5
```

## Array Best Practices

1. Use array methods instead of loops when possible
2. Use spread operator for combining arrays
3. Use map for transforming data
4. Use filter for selecting data
5. Use reduce for aggregating data
6. Use find for finding single items
7. Use some/every for testing conditions 