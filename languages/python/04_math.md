# Mathematics and Numbers in Python 🔢

Python provides various ways to handle mathematical operations and number manipulation. This guide covers basic arithmetic, division, modulo operations, and mathematical functions.

## Division Operations

Python's division behavior is different from many other languages:

```python
# Division is decimal by default
print(5 / 2)  # Returns 2.5

# Double slash rounds down
print(5 // 2)  # Returns 2
```

## Negative Number Division

Be careful with negative numbers in division:

```python
# Most languages round towards 0 by default
print(-3 // 2)  # Returns -2

# Workaround for rounding towards zero
print(int(-3 / 2))  # Returns -1
```

## Modulo Operations

The modulo operator (%) works similarly to other languages, but with some differences for negative numbers:

```python
# Basic modulo
print(10 % 3)  # Returns 1

# Negative number modulo
print(-10 % 3)  # Returns 2

# Using math.fmod for consistent behavior
import math
print(math.fmod(-10, 3))  # Returns -1.0
```

## Mathematical Functions

Python's math module provides various mathematical functions:

```python
import math

# Basic math functions
print(math.floor(3 / 2))  # Returns 1
print(math.ceil(3 / 2))   # Returns 2
print(math.sqrt(2))       # Returns 1.4142135623730951
print(math.pow(2, 3))     # Returns 8.0
```

## Infinity and Large Numbers

Python can handle very large numbers and infinity:

```python
# Infinity values
float("inf")
float("-inf")

# Python numbers are infinite so they never overflow
print(math.pow(2, 200))

# But still less than infinity
print(math.pow(2, 200) < float("inf"))
```

## Best Practices

1. Use `//` for integer division when you need whole numbers
2. Use `math.fmod()` for consistent modulo behavior with negative numbers
3. Import math module for advanced mathematical operations
4. Use appropriate data types for different mathematical operations
5. Consider precision when working with floating-point numbers

## Common Pitfalls

1. Forgetting that division returns float by default
2. Not handling negative numbers correctly in division
3. Confusion between `//` and `/` operators
4. Not considering floating-point precision
5. Not importing math module when needed

## Performance Considerations

1. Integer operations are faster than floating-point operations
2. Use `**` for small integer powers instead of `math.pow()`
3. Consider using `numpy` for large-scale mathematical operations
4. Be aware of memory usage with very large numbers
5. Use appropriate data types to optimize performance 