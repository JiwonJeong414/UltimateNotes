# JavaScript Objects

## Object Literals

In Java, an object is created from a class (class is a blueprint for objects). Each object has an identity, a behavior and a state. The state of an object is stored in fields (variables), while methods (functions) display the object's behavior.

In JAVASCRIPT, we can manually create individual objects using Object Literals Syntax. For example:

```javascript
const circle = {
    radius: 1,
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

```javascript
circle.constructor
--> f Object();
```

## Factory Functions

However, what if we want to change the value of an object depending on the parameter or create multiple objects w/ the same blueprints? Then, we use the factory function

```javascript
// Factory Function
function createCircle(radius) {
    return {
        // in JS, if our key & value are the same, we can simply put the key in        
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

Constructor Functions serves an equal purpose with the Factory Functions.

Both of these functions are equally good at creating objects but people who are familiar with JAVA, have easier time using the Constructor Function.

```javascript
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

```javascript
const circle = {
    radius: 1
};

circle.color = 'yellow';

console.log(circle);
// {radius: 1, color: "yellow}
// we can also delete properties
delete circle.color;
```

## Cloning an Object

This is an example of cloning an object:

```javascript
const circle = {
    radius: 1,
    draw() {
        console.log('draw');
    }
};

// Method 1: Using Object.assign
const another = Object.assign({}, circle); // the {} represents an empty object passed

// Method 2: Using spread operator
const another = {...circle};
```

## Object Properties

### Enumerating Properties

```javascript
const circle = {
    radius: 1,
    draw() {
        console.log('draw');
    }
};

// Method 1: for...in loop
for (let key in circle)
    console.log(key, circle[key]);

// Method 2: Object.keys()
for (let key of Object.keys(circle))
    console.log(key);

// Method 3: Object.entries()
for (let entry of Object.entries(circle))
    console.log(entry);
```

### Property Descriptors

```javascript
const person = { name: 'Jiwon' };

// Get property descriptor
let descriptor = Object.getOwnPropertyDescriptor(person, 'name');
console.log(descriptor);

// Define property with descriptor
Object.defineProperty(person, 'name', {
    writable: false,
    enumerable: false,
    configurable: false
});
```

## Object Best Practices

1. Use object literals for simple objects
2. Use factory functions when you need multiple similar objects
3. Use constructor functions when you need to create objects with specific behavior
4. Use Object.assign or spread operator for cloning objects
5. Use property descriptors to control object properties
6. Use Object.keys(), Object.values(), and Object.entries() for iteration
7. Use Object.freeze() to make objects immutable 