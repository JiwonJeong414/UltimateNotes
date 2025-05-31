# Tuples and Immutable Data in Python 🔒

Tuples in Python are immutable sequences, typically used to store collections of heterogeneous data. They are similar to lists but cannot be modified after creation.

## Basic Tuple Operations

```python
# Create a tuple
tup = (1, 2, 3)
print(tup)  # (1, 2, 3)
print(tup[0])  # 1
print(tup[-1])  # 3

# Tuples are immutable
# tup[0] = 4  # This would raise TypeError
```

## Tuple Creation

There are several ways to create tuples:

```python
# Literal syntax
tup = (1, 2, 3)

# Single element tuple (note the comma)
single = (1,)

# Tuple from iterable
tup = tuple([1, 2, 3])

# Tuple unpacking
a, b, c = (1, 2, 3)
print(a, b, c)  # 1 2 3
```

## Tuple as Dictionary Keys

Tuples can be used as dictionary keys because they are immutable:

```python
# Create dictionary with tuple keys
myMap = {(1, 2): 3}
print(myMap[(1, 2)])  # 3

# Tuples in sets
mySet = set()
mySet.add((1, 2))
print((1, 2) in mySet)  # True

# Lists cannot be keys (they are mutable)
# myMap[[3, 4]] = 5  # This would raise TypeError
```

## Tuple Methods

```python
tup = (1, 2, 2, 3, 2)

# Count occurrences
print(tup.count(2))  # 3

# Find index
print(tup.index(2))  # 1 (first occurrence)
```

## Tuple Operations

```python
tup1 = (1, 2, 3)
tup2 = (4, 5, 6)

# Concatenation
print(tup1 + tup2)  # (1, 2, 3, 4, 5, 6)

# Repetition
print(tup1 * 2)  # (1, 2, 3, 1, 2, 3)

# Slicing
print(tup1[1:])  # (2, 3)
```

## Named Tuples

`namedtuple` from collections module creates tuple subclasses with named fields:

```python
from collections import namedtuple

# Create a named tuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)

# Access fields by name
print(p.x)  # 1
print(p.y)  # 2

# Access fields by index
print(p[0])  # 1
print(p[1])  # 2
```

## Best Practices

1. Use tuples for immutable sequences
2. Use tuples as dictionary keys
3. Use named tuples for structured data
4. Use tuple unpacking for clean code
5. Use tuples for function return values

## Common Pitfalls

1. Forgetting comma in single-element tuples
2. Trying to modify tuple elements
3. Using lists instead of tuples for keys
4. Not using tuple unpacking
5. Confusing tuple and list operations

## Performance Considerations

1. Tuples are more memory efficient than lists
2. Tuple creation is faster than list creation
3. Tuple unpacking is efficient
4. Named tuples add minimal overhead
5. Consider using tuples for constant data

## Real-World Applications

1. Function return values
2. Dictionary keys
3. Data records
4. Configuration settings
5. Coordinate systems

## Advanced Usage

### Tuple Comprehension
```python
# Create tuple of squares
squares = tuple(x*x for x in range(5))
print(squares)  # (0, 1, 4, 9, 16)
```

### Tuple as Record
```python
# Using tuple as a simple record
person = ('John', 30, 'New York')
name, age, city = person  # Unpacking
print(f"{name} is {age} years old from {city}")
```

### Immutable Data Structures
```python
# Using tuples for immutable data structures
matrix = ((1, 2, 3),
          (4, 5, 6),
          (7, 8, 9))

# Access elements
print(matrix[0][1])  # 2
``` 