# Functions and Scope in Python 🎯

Functions in Python are first-class objects that can be defined, passed as arguments, and returned from other functions. Understanding function scope and variable visibility is crucial for writing maintainable code.

## Basic Function Definition

```python
def myFunc(n, m):
    return n * m

print(myFunc(1, 2))  # 2
```

## Function Scope

### Local Scope
```python
def local_scope():
    x = 10  # Local variable
    print(x)

local_scope()
# print(x)  # This would raise NameError
```

### Global Scope
```python
x = 10  # Global variable

def global_scope():
    print(x)  # Can access global variable

global_scope()
print(x)  # Can access global variable
```

### Nested Functions
```python
def outer(a, b):
    c = "c"  # Enclosing scope variable

    def inner():
        return a + b + c  # Can access outer variables
    return inner()

print(outer("a", "b"))  # "abc"
```

## Variable Modifications

### Modifying Objects
```python
def double(arr, val):
    def helper():
        # Modify array works
        for i, n in enumerate(arr):
            arr[i] *= 2

        # will only modify val in the helper scope
        # val *= 2

        # this will modify val outside helper scope
        nonlocal val
        val *= 2
    helper()
    print(arr, val)

nums = [1, 2]
val = 3
double(nums, val)  # [2, 4] 6
```

## Function Arguments

### Default Arguments
```python
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet("Alice"))  # "Hello, Alice!"
print(greet("Bob", "Hi"))  # "Hi, Bob!"
```

### Variable Arguments
```python
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3))  # 6
print(sum_all(1, 2, 3, 4, 5))  # 15
```

### Keyword Arguments
```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=30, city="New York")
```

## Lambda Functions

```python
# Simple lambda function
square = lambda x: x * x
print(square(5))  # 25

# Lambda with multiple arguments
multiply = lambda x, y: x * y
print(multiply(3, 4))  # 12

# Lambda in sorting
arr = ["bob", "alice", "jane", "doe"]
arr.sort(key=lambda x: len(x))
print(arr)  # ['bob', 'doe', 'jane', 'alice']
```

## Function Decorators

```python
def timer(func):
    def wrapper(*args, **kwargs):
        import time
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"Function {func.__name__} took {end - start} seconds")
        return result
    return wrapper

@timer
def slow_function():
    import time
    time.sleep(1)
    return "Done"

print(slow_function())
```

## Best Practices

1. Use descriptive function names
2. Keep functions small and focused
3. Use type hints for better documentation
4. Handle exceptions appropriately
5. Use appropriate scope for variables

## Common Pitfalls

1. Modifying mutable default arguments
2. Confusing local and global scope
3. Not using nonlocal keyword when needed
4. Overusing global variables
5. Not handling exceptions properly

## Performance Considerations

1. Function calls have overhead
2. Lambda functions are slightly slower
3. Decorators add minimal overhead
4. Consider using generators for large data
5. Use appropriate argument types

## Real-World Applications

1. Modular code organization
2. Event handling
3. Callback functions
4. Data processing pipelines
5. API endpoints

## Advanced Usage

### Function Annotations
```python
def greet(name: str, age: int) -> str:
    return f"Hello, {name}! You are {age} years old."

print(greet("Alice", 30))
```

### Generator Functions
```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

for num in fibonacci(5):
    print(num)  # 0, 1, 1, 2, 3
```

### Closures
```python
def counter():
    count = 0
    def increment():
        nonlocal count
        count += 1
        return count
    return increment

c = counter()
print(c())  # 1
print(c())  # 2
print(c())  # 3
```

### Function Composition
```python
def compose(f, g):
    return lambda x: f(g(x))

def add_one(x):
    return x + 1

def multiply_by_two(x):
    return x * 2

add_one_and_double = compose(multiply_by_two, add_one)
print(add_one_and_double(3))  # 8
``` 