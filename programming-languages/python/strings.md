# Strings and Text Processing in Python 📝

Strings in Python are immutable sequences of characters. This guide covers string operations, manipulation, and common string processing techniques.

## Basic String Operations

```python
# Strings are similar to arrays
s = "abc"
print(s[0:2])  # "ab"

# Strings are immutable
# s[0] = "A"  # This would raise an error

# Creating a new string
s += "def"
print(s)  # "abcdef"
```

## String Conversion

```python
# Converting between strings and numbers
print(int("123") + int("123"))  # 246
print(str(123) + str(123))      # "123123"

# ASCII values
print(ord("a"))  # 97
print(ord("b"))  # 98
```

## String Joining

```python
# Joining a list of strings
strings = ["ab", "cd", "ef"]
print("".join(strings))  # "abcdef"
```

## String Multiplication and Concatenation

```python
def string_times(str, n):
    string = ""  # Initialize as empty string, not None
    for i in range(n):
        string += str
    return string

# Or more simply, use string multiplication
def string_times_simple(str, n):
    return str * n

print(string_times("Hi", 3))        # "HiHiHi"
print(string_times_simple("Hi", 3))  # "HiHiHi"
```

## String Search Methods

```python
text = "hixxxhi"
print(text.find("hi"))     # Returns 0 (first position of "hi")
print(text.find("hi", 1))  # Returns 5 (finds "hi" starting from position 1)
print(text.count("hi"))    # Returns 2 (counts all occurrences of "hi")
```

## String Slicing

```python
text = "notebook"

# Basic slicing
print(text[:3])    # "not" - first 3 characters
print(text[3:])    # "ebook" - from index 3 to end
print(text[3:6])   # "ebo" - from index 3 to 5
print(text[:])     # "notebook" - all characters

# Getting specific characters
print(text[0])     # "P" - first character
print(text[-1])    # "n" - last character
print(text[2])     # "t" - third character
print(text[-2])    # "o" - second to last character

# Negative indices
print(text[-3:])   # "hon" - last 3 characters
print(text[:-3])   # "Pyt" - all except last 3 characters

# Step in slicing
print(text[::2])   # "Pto" - every second character
print(text[::-1])  # "nohtyP" - reverse string
```

## Common String Operations

```python
# Checking prefixes
def add_not(str):
    if len(str) >= 3 and str[:3] == "not":
        return str
    return "not " + str

print(add_not("notebook"))  # "notebook"
print(add_not("hello"))     # "not hello"
```

## Best Practices

1. Use string methods instead of manual manipulation
2. Use f-strings for string formatting
3. Consider using `join()` for concatenating multiple strings
4. Use appropriate string methods for different operations
5. Handle string encoding properly

## Common Pitfalls

1. Modifying strings directly (they're immutable)
2. Not handling empty strings
3. Confusing string methods with similar names
4. Not considering string encoding
5. Inefficient string concatenation

## Performance Considerations

1. String concatenation with `+` is O(n)
2. `join()` is more efficient for multiple strings
3. String methods are optimized for common operations
4. Consider using `StringIO` for large string operations
5. Be aware of memory usage with large strings 