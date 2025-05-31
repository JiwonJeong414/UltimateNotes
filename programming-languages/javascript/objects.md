# JavaScript Objects

## Object Literals

In Java, an object is created from a class (class is a blueprint for objects). Each object has an identity, a behavior and a state. The state of an object is stored in fields (variables), while methods (functions) display the object's behavior.

In JAVASCRIPT, we can manually create individual objects using Object Literals Syntax:

```javascript
const circle = {
    radius: 1,
    location: {
        x: 1,
        y: 1
    },
    isVisible: true,
    draw: function() {
        console.log('draw');
    }
}

// All of these are part of a circle object
```

When we create an object using the Object Literals Syntax, internally, the JavaScript engine uses the constructor function:

```javascript
circle.constructor
// f Object();
```

## Cloning Objects

```javascript
const circle = {
    radius: 1,
    draw() {
        console.log('draw');
    }
};

// Method 1: Using Object.assign
const another = Object.assign({}, circle);

// Method 2: Using spread operator
const another = {...circle};
```

## Factory Functions

Factory functions are used to create multiple objects with the same blueprint:

```javascript
function createCircle(radius) {
    return {
        radius, // equivalent to radius: radius
        draw() { // equivalent to function draw()
            console.log('draw');
        }
    }
}

const circle1 = createCircle(1);
const circle2 = createCircle(2);
```

## Constructor Functions

Constructor Functions serve the same purpose as Factory Functions. Both are equally good at creating objects, but people familiar with JAVA might find Constructor Functions more intuitive:

```javascript
function Circle(radius) {
    this.radius = radius;
    this.draw = function() {
        console.log('draw');
    }
} 

const circle = new Circle(1);
```

<aside>
💡 Objects are dynamic in JavaScript. We can add or remove properties at runtime:
</aside>

```javascript
const circle = {
    radius: 1
};

circle.color = 'yellow';
console.log(circle); // {radius: 1, color: "yellow"}

delete circle.color;
console.log(circle); // {radius: 1}
```

## Object Methods

### Object.keys()
```javascript
const person = {
    name: 'John',
    age: 30
};

const keys = Object.keys(person);
console.log(keys); // ['name', 'age']
```

### Object.values()
```javascript
const values = Object.values(person);
console.log(values); // ['John', 30]
```

### Object.entries()
```javascript
const entries = Object.entries(person);
console.log(entries); // [['name', 'John'], ['age', 30]]
```

## Object Best Practices

1. Use object literals for simple objects
2. Use factory functions for complex objects
3. Use constructor functions when you need inheritance
4. Use meaningful property names
5. Group related properties together
6. Use computed property names when appropriate
7. Use object destructuring for clean code 