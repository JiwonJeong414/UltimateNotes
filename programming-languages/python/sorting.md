# Sorting and List Operations in Python 🔄

Python provides powerful built-in methods for sorting and manipulating lists. This guide covers various sorting techniques, list comprehensions, and 2D lists.

## List Reversal

```python
nums = [1, 2, 3]
nums.reverse()  # O(n) operation
print(nums)
```

## Basic Sorting

Python's built-in sort method is efficient and versatile:

```python
arr = [5, 4, 7, 3, 8]
arr.sort()  # O(n log n)
print(arr)

# Reverse sorting
arr.sort(reverse=True)  # O(n log n)
print(arr)
```

## String Sorting

Lists of strings can be sorted alphabetically:

```python
arr = ["bob", "alice", "jane", "doe"]
arr.sort()
print(arr)

# Custom sort by string length
arr.sort(key=lambda x: len(x))  # Sort by length
print(arr)
```

## List Comprehension

List comprehension provides a concise way to create lists:

```python
# Create a list of numbers from 0 to 4
arr = [i for i in range(5)]
print(arr)
```

## 2D Lists (Arrays)

Creating and working with 2D lists requires careful initialization:

```python
# Correct way to create a 2D list
arr = [[0] * 4 for i in range(4)]
print(arr)

# Incorrect way (creates references to the same list)
arr = [[0] * 4] * 4  # Don't do this!
print(arr)
```

## Advanced Sorting

### Custom Sorting with Key Functions
```python
# Sort by multiple criteria
students = [
    ("Alice", 20, "A"),
    ("Bob", 19, "B"),
    ("Charlie", 20, "A")
]

# Sort by age, then by grade
students.sort(key=lambda x: (x[1], x[2]))
print(students)
```

### Stable Sorting
```python
# Python's sort is stable - maintains relative order of equal elements
arr = [(1, "a"), (2, "b"), (1, "c")]
arr.sort(key=lambda x: x[0])
print(arr)  # [(1, "a"), (1, "c"), (2, "b")]
```

## Best Practices

1. Use `sort()` for in-place sorting
2. Use `sorted()` when you need a new sorted list
3. Use list comprehension for simple transformations
4. Be careful with 2D list initialization
5. Use appropriate key functions for custom sorting

## Common Pitfalls

1. Modifying a list while sorting
2. Incorrect 2D list initialization
3. Not considering sort stability
4. Using inefficient sorting methods
5. Not handling empty lists

## Performance Considerations

1. Python's sort is O(n log n)
2. List comprehension is faster than for loops
3. Consider using `numpy` for large numerical arrays
4. Be aware of memory usage with large lists
5. Use appropriate sorting methods for different data types 