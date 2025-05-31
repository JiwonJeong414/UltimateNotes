# Input and Output in Python 📥📤

Python provides various ways to handle input and output operations. This guide covers basic input handling, type conversion, error handling, and different input scenarios.

## Basic Input

The simplest way to get user input is using the `input()` function:

```python
name = input("What is your name? ")
print("Hello, " + name + "!")  # String concatenation
```

## Input with Type Conversion

When you need numeric input, you'll need to convert the string input to the appropriate type:

```python
age = input("How old are you? ")
age = int(age)  # Convert string to integer
print(f"In 5 years, you will be {age + 5} years old")
```

## Input with Error Handling

It's important to handle potential errors when converting input types:

```python
try:
    temperature = float(input("Enter temperature in Celsius: "))
    fahrenheit = (temperature * 9/5) + 32
    print(f"{temperature}°C is equal to {fahrenheit:.1f}°F")
except ValueError:
    print("Please enter a valid number!")
```

## Multiple Inputs

There are several ways to handle multiple inputs:

### Method 1: Separate Inputs
```python
first_name = input("Enter your first name: ")
last_name = input("Enter your last name: ")
print(f"Full name: {first_name} {last_name}")
```

### Method 2: Split Input
```python
x, y = input("Enter two numbers (separated by space): ").split()
x, y = int(x), int(y)  # Convert to integers
print(f"Sum: {x + y}")
```

## Input Validation

Always validate user input to ensure it meets your requirements:

```python
while True:
    password = input("Enter a password (min 8 characters): ")
    if len(password) >= 8:
        print("Password is valid!")
        break
    else:
        print("Password is too short. Try again.")
```

## Input with Default Values

You can provide default values when input is empty:

```python
color = input("Enter your favorite color (press Enter for default): ").strip()
if not color:  # If empty input
    color = "blue"  # Default value
print(f"Your favorite color is {color}")
```

## Menu Selection

A common pattern for menu-driven programs:

```python
print("\nMenu:")
print("1. Option One")
print("2. Option Two")
print("3. Exit")

choice = input("Enter your choice (1-3): ")
if choice == "1":
    print("You selected Option One")
elif choice == "2":
    print("You selected Option Two")
elif choice == "3":
    print("Goodbye!")
else:
    print("Invalid choice!")
```

## Best Practices

1. Always validate user input
2. Use try-except blocks for type conversion
3. Provide clear prompts to users
4. Handle edge cases (empty input, invalid input)
5. Use appropriate data types for different inputs

## Common Pitfalls

1. Forgetting to convert string input to appropriate types
2. Not handling exceptions during type conversion
3. Not validating input before processing
4. Not providing clear error messages
5. Not handling empty or invalid input 