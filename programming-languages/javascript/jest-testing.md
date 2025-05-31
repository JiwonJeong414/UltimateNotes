# Testing with Jest

Jest is a popular JavaScript testing framework that provides a complete testing solution with built-in assertion library.

## Installation

```bash
npm install --save-dev jest
```

Add to package.json:
```json
{
  "scripts": {
    "test": "jest"
  }
}
```

## Basic Test Structure

```javascript
// math.js
function add(a, b) {
    return a + b;
}

module.exports = { add };

// math.test.js
const { add } = require('./math');

describe('Math functions', () => {
    test('adds 1 + 2 to equal 3', () => {
        expect(add(1, 2)).toBe(3);
    });
});
```

## Common Matchers

### Basic Matchers
```javascript
test('basic matchers', () => {
    // Exact equality
    expect(2 + 2).toBe(4);
    
    // Object matching
    expect({ name: 'John' }).toEqual({ name: 'John' });
    
    // Truthiness
    expect(null).toBeNull();
    expect(undefined).toBeUndefined();
    expect(true).toBeTruthy();
    expect(false).toBeFalsy();
});
```

### Number Matchers
```javascript
test('number matchers', () => {
    const value = 2 + 2;
    
    expect(value).toBeGreaterThan(3);
    expect(value).toBeLessThan(5);
    expect(value).toBeGreaterThanOrEqual(4);
    expect(value).toBeLessThanOrEqual(4);
});
```

### String Matchers
```javascript
test('string matchers', () => {
    expect('team').toMatch(/team/);
    expect('team').not.toMatch(/I/);
});
```

### Array Matchers
```javascript
test('array matchers', () => {
    const shoppingList = ['milk', 'bread', 'eggs'];
    
    expect(shoppingList).toContain('milk');
    expect(new Set(shoppingList)).toContain('milk');
});
```

## Async Testing

### Promises
```javascript
test('async with promises', () => {
    return fetchData().then(data => {
        expect(data).toBe('peanut butter');
    });
});
```

### Async/Await
```javascript
test('async with async/await', async () => {
    const data = await fetchData();
    expect(data).toBe('peanut butter');
});
```

## Mock Functions

```javascript
test('mock functions', () => {
    const mockFn = jest.fn();
    
    mockFn();
    expect(mockFn).toHaveBeenCalled();
    
    mockFn.mockReturnValue('mocked value');
    expect(mockFn()).toBe('mocked value');
});
```

## Test Setup and Teardown

```javascript
beforeAll(() => {
    // Runs once before all tests
});

afterAll(() => {
    // Runs once after all tests
});

beforeEach(() => {
    // Runs before each test
});

afterEach(() => {
    // Runs after each test
});
```

## Best Practices

1. Keep tests focused and atomic
2. Use descriptive test names
3. Follow the AAA pattern (Arrange, Act, Assert)
4. Mock external dependencies
5. Keep tests independent
6. Use appropriate matchers
7. Clean up after tests
8. Test both success and failure cases 