# Sets and HashSets in Python 🔍

Sets in Python are unordered collections of unique elements. They are implemented as hash tables, making them very efficient for membership testing and duplicate removal.

## Basic Set Operations

```python
# Create a set
mySet = set()

# Add elements
mySet.add(1)
mySet.add(2)
print(mySet)  # {1, 2}
print(len(mySet))  # 2

# Check membership
print(1 in mySet)  # True

# Remove elements
mySet.remove(2)
print(2 in mySet)  # False
```

## Set Creation

There are several ways to create sets:

```python
# From a list
print(set([1, 2, 3]))  # {1, 2, 3}

# Set comprehension
mySet = {i for i in range(5)}
print(mySet)  # {0, 1, 2, 3, 4}

# Literal syntax
mySet = {1, 2, 3}
print(mySet)  # {1, 2, 3}
```

## Set Operations

### Union, Intersection, and Difference
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Union
print(set1 | set2)  # {1, 2, 3, 4, 5}
print(set1.union(set2))  # Same as above

# Intersection
print(set1 & set2)  # {3}
print(set1.intersection(set2))  # Same as above

# Difference
print(set1 - set2)  # {1, 2}
print(set1.difference(set2))  # Same as above
```

### Symmetric Difference
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Elements in either set, but not in both
print(set1 ^ set2)  # {1, 2, 4, 5}
print(set1.symmetric_difference(set2))  # Same as above
```

## Set Methods

```python
mySet = {1, 2, 3}

# Add multiple elements
mySet.update([4, 5, 6])
print(mySet)  # {1, 2, 3, 4, 5, 6}

# Remove element (raises KeyError if not found)
mySet.remove(1)

# Discard element (no error if not found)
mySet.discard(10)

# Pop random element
element = mySet.pop()
print(element)  # Random element from set

# Clear set
mySet.clear()
print(mySet)  # set()
```

## Best Practices

1. Use sets for membership testing
2. Use sets to remove duplicates
3. Use set operations for mathematical set operations
4. Consider using frozen sets for immutable sets
5. Use appropriate set methods for different operations

## Common Pitfalls

1. Expecting ordered elements in sets
2. Modifying sets while iterating
3. Not handling KeyError in remove operations
4. Confusing set operations
5. Not considering hashability of elements

## Performance Considerations

1. Membership testing is O(1)
2. Adding and removing elements is O(1)
3. Set operations are O(len(s) + len(t))
4. Sets use more memory than lists
5. Consider using sets for large collections

## Real-World Applications

1. Removing duplicates from sequences
2. Membership testing in large collections
3. Finding unique elements
4. Mathematical set operations
5. Graph algorithms (visited nodes)

## Advanced Usage

### Frozen Sets
```python
# Immutable sets
frozen = frozenset([1, 2, 3])
# frozen.add(4)  # This would raise an error
```

### Set Comprehension with Conditions
```python
# Create set of even numbers
evens = {x for x in range(10) if x % 2 == 0}
print(evens)  # {0, 2, 4, 6, 8}
``` 