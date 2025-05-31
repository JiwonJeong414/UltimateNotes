# Control Flow in Python 🔄

Control flow statements are essential for creating dynamic and responsive programs. Python provides several ways to control the flow of execution in your code.

## If Statements

Python's if statements are unique in that they don't require parentheses or curly braces - just indentation:

```python
n = 1
if n > 2:
    n -= 1
elif n == 2:
    n *= 2
else:
    n += 2
```

## Complex Conditions

For complex conditions, you can use parentheses and logical operators:

```python
n, m = 1, 2
if ((n > 2 and n != m) or n == m):
    n += 1
```

Note: Python uses `and` and `or` instead of `&&` and `||`

## While Loops

While loops continue executing as long as a condition is true:

```python
n = 0
while n < 5:
    print(n)
    n += 1
```

## For Loops

Python's for loops are versatile and can iterate over various sequences:

### Basic Range Loop
```python
# Looping from i = 0 to i = 4
for i in range(5):
    print(i)
```

### Custom Range
```python
# Looping from i = 2 to i = 5
for i in range(2, 6):
    print(i)
```

### Reverse Range
```python
# Looping from i = 5 to i = 2
for i in range(5, 1, -1):
    print(i)
```

## Best Practices

1. Use meaningful variable names in loops
2. Keep loop bodies small and focused
3. Use appropriate loop types for different scenarios
4. Consider using list comprehensions for simple loops
5. Avoid modifying the loop variable inside the loop

## Common Pitfalls

1. Forgetting to increment counter in while loops
2. Modifying the loop variable inside a for loop
3. Using `range()` incorrectly
4. Not handling edge cases in conditions
5. Deeply nested if statements (consider refactoring)

## Performance Considerations

1. `for` loops are generally faster than `while` loops
2. List comprehensions can be more efficient than loops
3. Avoid unnecessary computations inside loops
4. Consider using `enumerate()` when you need both index and value
5. Use `break` and `continue` appropriately to optimize loops 