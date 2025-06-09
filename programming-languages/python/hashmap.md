# Dictionaries and HashMaps in Python 🗝️

Dictionaries in Python are mutable, unordered collections of key-value pairs. They are implemented as hash tables, making them very efficient for lookups and insertions.

## Basic Dictionary Operations

get or default

```python
# Create HashMap
hashMap[s[i]] = hashMap.get(s[i], 0) + 1
```

```python
# Create a dictionary
myMap = {}
myMap["alice"] = 88
myMap["bob"] = 77
print(myMap)  # {'alice': 88, 'bob': 77}
print(len(myMap))  # 2

# Update value
myMap["alice"] = 80
print(myMap["alice"])  # 80

# Check key existence
print("alice" in myMap)  # True

# Remove key-value pair
myMap.pop("alice")
print("alice" in myMap)  # False
```

## Dictionary Creation

There are several ways to create dictionaries:

```python
# Literal syntax
myMap = {"alice": 90, "bob": 70}
print(myMap)

# Dictionary comprehension
myMap = {i: 2*i for i in range(3)}
print(myMap)  # {0: 0, 1: 2, 2: 4}
```

## Dictionary Iteration

There are multiple ways to iterate through a dictionary:

```python
myMap = {"alice": 90, "bob": 70}

# Iterate through keys
for key in myMap:
    print(key, myMap[key])

# Iterate through values
for val in myMap.values():
    print(val)

# Iterate through key-value pairs
for key, val in myMap.items():
    print(key, val)
```

## DefaultDict

The `defaultdict` from collections module automatically handles missing keys:

```python
from collections import defaultdict

# Regular dictionary - need to check if key exists
regular_dict = {}
# regular_dict["count"] += 1  # This would raise KeyError

# defaultdict with int - automatically initializes to 0
count_dict = defaultdict(int)
count_dict["count"] += 1  # Works! Automatically starts at 0
print(count_dict["count"])  # 1

# defaultdict with list - automatically initializes to empty list
list_dict = defaultdict(list)
list_dict["numbers"].append(1)  # Works! Automatically creates empty list
print(list_dict["numbers"])  # [1]

# defaultdict with set - automatically initializes to empty set
set_dict = defaultdict(set)
set_dict["unique"].add(1)  # Works! Automatically creates empty set
print(set_dict["unique"])  # {1}
```

## Common Use Cases

### Counting Occurrences
```python
word = "hello"
char_count = defaultdict(int)
for char in word:
    char_count[char] += 1  # No need to check if key exists
print(char_count)  # {'h': 1, 'e': 1, 'l': 2, 'o': 1}
```

### Dictionary Methods
```python
myMap = {"alice": 88, "bob": 77}

# Get value with default
print(myMap.get("alice", 0))  # 88
print(myMap.get("charlie", 0))  # 0 (default value if key doesn't exist)

# Check if key exists
if "alice" in myMap:
    print("alice exists")

# Remove key-value pair
myMap.pop("alice")
print(myMap)

# Clear dictionary
myMap.clear()
print(myMap)
```

## Best Practices

1. Use `defaultdict` when you need default values
2. Use `get()` method to safely access values
3. Use dictionary comprehension for simple transformations
4. Consider using `OrderedDict` when order matters
5. Use appropriate dictionary methods for different operations

## Common Pitfalls

1. Modifying dictionary while iterating
2. Not handling missing keys properly
3. Confusing dictionary methods
4. Not considering hashability of keys
5. Not using appropriate dictionary types

## Performance Considerations

1. Lookup and insertion are O(1)
2. Dictionary comprehension is faster than loops
3. `defaultdict` adds minimal overhead
4. Consider memory usage with large dictionaries
5. Use appropriate dictionary types for different use cases

## Real-World Applications

1. Caching and memoization
2. Counting and frequency analysis
3. Configuration storage
4. Object property storage
5. Graph representations 