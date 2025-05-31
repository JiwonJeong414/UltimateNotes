# Queues and Collections in Python 🎯

Python's `collections` module provides specialized container datatypes. This guide focuses on queues and other useful collection types.

## Double-Ended Queue (deque)

The `deque` class provides a double-ended queue with fast append and pop operations on both ends:

```python
from collections import deque

# Create a queue
queue = deque()
queue.append(1)
queue.append(2)
print(queue)  # deque([1, 2])

# Remove from front (FIFO)
queue.popleft()
print(queue)  # deque([2])

# Add to front
queue.appendleft(1)
print(queue)  # deque([1, 2])

# Remove from end
queue.pop()
print(queue)  # deque([1])
```

## Queue Operations

### Basic Queue Operations
```python
from collections import deque

# Initialize queue
queue = deque()

# Enqueue (add to end)
queue.append(1)
queue.append(2)
queue.append(3)

# Dequeue (remove from front)
first_item = queue.popleft()
print(first_item)  # 1
```

### Queue with Max Size
```python
from collections import deque

# Create a queue with maximum size
max_size = 3
queue = deque(maxlen=max_size)

# Add items
queue.append(1)
queue.append(2)
queue.append(3)
queue.append(4)  # This will remove the oldest item (1)

print(queue)  # deque([2, 3, 4], maxlen=3)
```

## Other Collection Types

### Counter
```python
from collections import Counter

# Count occurrences of elements
words = ['apple', 'banana', 'apple', 'cherry', 'banana']
word_count = Counter(words)
print(word_count)  # Counter({'apple': 2, 'banana': 2, 'cherry': 1})
```

### DefaultDict
```python
from collections import defaultdict

# Create a dictionary with default values
d = defaultdict(list)
d['a'].append(1)  # No need to check if key exists
print(d)  # defaultdict(<class 'list'>, {'a': [1]})
```

## Best Practices

1. Use `deque` for queue operations
2. Use `maxlen` parameter for fixed-size queues
3. Consider using `Counter` for frequency counting
4. Use `defaultdict` to avoid key existence checks
5. Choose appropriate collection type for your use case

## Common Pitfalls

1. Using list for queue operations (inefficient)
2. Not handling empty queue cases
3. Confusing queue and stack operations
4. Not considering thread safety
5. Not using appropriate collection types

## Performance Considerations

1. `deque` operations are O(1) at both ends
2. List operations are O(n) for front operations
3. `Counter` is optimized for counting operations
4. `defaultdict` adds minimal overhead
5. Consider memory usage with large collections

## Thread Safety

For thread-safe operations, consider using:
```python
from queue import Queue

# Thread-safe queue
queue = Queue()
queue.put(1)  # Thread-safe put
item = queue.get()  # Thread-safe get
```

## Real-World Applications

1. Task scheduling systems
2. Message queues
3. Breadth-first search algorithms
4. Event handling systems
5. Producer-consumer patterns 