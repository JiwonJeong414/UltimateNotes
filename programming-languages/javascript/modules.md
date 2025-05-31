# JavaScript Modules

## CommonJS Modules (Node.js)

CommonJS is the original module system used in Node.js.

### Exporting

```javascript
// math.js
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;

// Method 1: Export individual functions
module.exports.add = add;
module.exports.subtract = subtract;

// Method 2: Export as an object
module.exports = {
    add,
    subtract
};
```

### Importing

```javascript
// Method 1: Import specific functions
const { add, subtract } = require('./math');

// Method 2: Import entire module
const math = require('./math');
console.log(math.add(5, 3));
```

## ES6 Modules

ES6 modules are the standard module system in modern JavaScript.

### Exporting

```javascript
// math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// Default export
export default class Calculator {
    add(a, b) { return a + b; }
    subtract(a, b) { return a - b; }
}
```

### Importing

```javascript
// Method 1: Import specific functions
import { add, subtract } from './math.js';

// Method 2: Import with alias
import { add as addition } from './math.js';

// Method 3: Import default export
import Calculator from './math.js';

// Method 4: Import everything
import * as math from './math.js';
```

## Using Modules in HTML

To use ES6 modules in HTML, add the `type="module"` attribute:

```html
<script type="module">
    import { add } from './math.js';
    console.log(add(2, 3));
</script>
```

## Best Practices

1. Use ES6 modules for modern web applications
2. Use CommonJS for Node.js applications
3. Keep modules focused and single-purpose
4. Use named exports for multiple exports
5. Use default exports for main module functionality
6. Use clear and descriptive names for exports 