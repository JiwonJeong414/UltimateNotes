# Classes and Object-Oriented Programming in Python 🏗️

Python's object-oriented programming (OOP) features allow you to create reusable, maintainable, and organized code. Classes are blueprints for creating objects with attributes and methods.

## Basic Class Definition

```python
class MyClass:
    # Constructor
    def __init__(self, nums):
        # Create member variables
        self.nums = nums
        self.size = len(nums)

    # Instance method
    def getLength(self):
        return self.size
    
    def getDoubleLength(self):
        return 2 * self.getLength()
```

## Class Attributes and Methods

### Instance Attributes
```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Instance attribute
        self.age = age    # Instance attribute

    def greet(self):
        return f"Hello, I'm {self.name} and I'm {self.age} years old."

person = Person("Alice", 30)
print(person.greet())  # "Hello, I'm Alice and I'm 30 years old."
```

### Class Attributes
```python
class Circle:
    pi = 3.14159  # Class attribute

    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return Circle.pi * self.radius ** 2

circle = Circle(5)
print(circle.area())  # 78.53975
```

### Static Methods
```python
class MathUtils:
    @staticmethod
    def add(x, y):
        return x + y

    @staticmethod
    def multiply(x, y):
        return x * y

print(MathUtils.add(2, 3))  # 5
print(MathUtils.multiply(2, 3))  # 6
```

### Class Methods
```python
class Date:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day

    @classmethod
    def from_string(cls, date_string):
        year, month, day = map(int, date_string.split('-'))
        return cls(year, month, day)

date = Date.from_string('2024-03-15')
print(f"{date.year}-{date.month}-{date.day}")  # 2024-3-15
```

## Inheritance

### Basic Inheritance
```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

dog = Dog("Buddy")
cat = Cat("Whiskers")
print(dog.speak())  # "Buddy says Woof!"
print(cat.speak())  # "Whiskers says Meow!"
```

### Multiple Inheritance
```python
class A:
    def method(self):
        return "A"

class B:
    def method(self):
        return "B"

class C(A, B):
    pass

c = C()
print(c.method())  # "A" (Method Resolution Order)
```

## Special Methods

### String Representation
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"Point({self.x}, {self.y})"

    def __repr__(self):
        return f"Point(x={self.x}, y={self.y})"

p = Point(3, 4)
print(str(p))  # "Point(3, 4)"
print(repr(p))  # "Point(x=3, y=4)"
```

### Operator Overloading
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)

v1 = Vector(1, 2)
v2 = Vector(3, 4)
v3 = v1 + v2
v4 = v1 * 2
print(f"v3: ({v3.x}, {v3.y})")  # v3: (4, 6)
print(f"v4: ({v4.x}, {v4.y})")  # v4: (2, 4)
```

## Best Practices

1. Use meaningful class and method names
2. Follow the Single Responsibility Principle
3. Use inheritance appropriately
4. Implement proper encapsulation
5. Use type hints for better documentation

## Common Pitfalls

1. Not using `self` in instance methods
2. Confusing class and instance attributes
3. Overusing inheritance
4. Not handling exceptions properly
5. Not using proper encapsulation

## Performance Considerations

1. Class instantiation has overhead
2. Method calls are slightly slower than functions
3. Multiple inheritance can be complex
4. Consider using `__slots__` for memory optimization
5. Use appropriate data structures

## Real-World Applications

1. Data modeling
2. GUI development
3. Game development
4. Web frameworks
5. Database ORMs

## Advanced Usage

### Property Decorators
```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero!")
        self._celsius = value

    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32

temp = Temperature(25)
print(temp.fahrenheit)  # 77.0
temp.celsius = 30
print(temp.fahrenheit)  # 86.0
```

### Abstract Base Classes
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

rect = Rectangle(5, 3)
print(rect.area())  # 15
print(rect.perimeter())  # 16
```

### Metaclasses
```python
class Singleton(type):
    _instances = {}
    
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Database(metaclass=Singleton):
    def __init__(self):
        print("Initializing database...")

db1 = Database()
db2 = Database()  # Won't print "Initializing database..."
print(db1 is db2)  # True
``` 