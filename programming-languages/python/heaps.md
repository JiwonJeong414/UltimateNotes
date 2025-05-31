# Heaps and Priority Queues in Python 📊

A heap is a specialized tree-based data structure that satisfies the heap property. Python's `heapq` module implements a min heap by default, which can be used to implement priority queues.

## Basic Heap Operations

```python
import heapq

# Create a min heap
minHeap = []
heapq.heappush(minHeap, 3)
heapq.heappush(minHeap, 2)
heapq.heappush(minHeap, 4)

# Min is always at index 0
print(minHeap[0])  # 2

# Pop elements in order
while len(minHeap):
    print(heapq.heappop(minHeap))  # 2, 3, 4
```

## Max Heap Implementation

Since Python's `heapq` only implements min heaps, we can create a max heap by negating values:

```python
import heapq

# Create a max heap
maxHeap = []
heapq.heappush(maxHeap, -3)
heapq.heappush(maxHeap, -2)
heapq.heappush(maxHeap, -4)

# Max is always at index 0 (negated)
print(-1 * maxHeap[0])  # 4

# Pop elements in order
while len(maxHeap):
    print(-1 * heapq.heappop(maxHeap))  # 4, 3, 2
```

## Heap Creation

There are several ways to create heaps:

```python
import heapq

# Create heap from list
arr = [2, 1, 8, 4, 5]
heapq.heapify(arr)  # Convert list to heap in-place
print(arr)  # [1, 2, 8, 4, 5]

# Create heap using heappush
heap = []
for x in [2, 1, 8, 4, 5]:
    heapq.heappush(heap, x)
print(heap)  # [1, 2, 8, 4, 5]
```

## Priority Queue Implementation

Heaps can be used to implement priority queues:

```python
import heapq

class PriorityQueue:
    def __init__(self):
        self._queue = []
        self._index = 0

    def push(self, item, priority):
        heapq.heappush(self._queue, (priority, self._index, item))
        self._index += 1

    def pop(self):
        return heapq.heappop(self._queue)[-1]

# Usage
pq = PriorityQueue()
pq.push("task1", 2)
pq.push("task2", 1)
pq.push("task3", 3)

print(pq.pop())  # "task2" (highest priority)
print(pq.pop())  # "task1"
print(pq.pop())  # "task3"
```

## Heap Operations

### Heapify
```python
import heapq

# Convert list to heap
arr = [3, 1, 4, 1, 5, 9, 2, 6]
heapq.heapify(arr)
print(arr)  # [1, 1, 2, 3, 5, 9, 4, 6]
```

### Heap Replace
```python
import heapq

# Pop and push in one operation
heap = [1, 2, 3]
print(heapq.heapreplace(heap, 4))  # 1
print(heap)  # [2, 4, 3]
```

### Heap Push Pop
```python
import heapq

# Push and pop in one operation
heap = [1, 2, 3]
print(heapq.heappushpop(heap, 0))  # 0
print(heap)  # [1, 2, 3]
```

## Best Practices

1. Use `heapq` for min heap operations
2. Negate values for max heap operations
3. Use `heapify` for converting lists to heaps
4. Consider using priority queues for scheduling
5. Use appropriate heap operations for different use cases

## Common Pitfalls

1. Forgetting to import `heapq`
2. Not handling empty heaps
3. Confusing min and max heap operations
4. Not maintaining heap property
5. Not considering thread safety

## Performance Considerations

1. Heap operations are O(log n)
2. Heapify is O(n)
3. Heap push/pop are O(log n)
4. Heap replace is O(log n)
5. Consider using heaps for large datasets

## Real-World Applications

1. Task scheduling
2. Event-driven simulation
3. Graph algorithms (Dijkstra's)
4. Merge k sorted lists
5. Median finding

## Advanced Usage

### Custom Objects in Heap
```python
import heapq

class Task:
    def __init__(self, name, priority):
        self.name = name
        self.priority = priority

    def __lt__(self, other):
        return self.priority < other.priority

# Create heap of custom objects
heap = []
heapq.heappush(heap, Task("task1", 2))
heapq.heappush(heap, Task("task2", 1))
heapq.heappush(heap, Task("task3", 3))

# Pop tasks in priority order
while heap:
    task = heapq.heappop(heap)
    print(f"{task.name}: {task.priority}")
```

### K-th Largest Element
```python
import heapq

def kth_largest(arr, k):
    heap = []
    for num in arr:
        heapq.heappush(heap, num)
        if len(heap) > k:
            heapq.heappop(heap)
    return heap[0]

# Usage
arr = [3, 2, 1, 5, 6, 4]
k = 2
print(kth_largest(arr, k))  # 5
```

### Merge K Sorted Lists
```python
import heapq

def merge_k_lists(lists):
    heap = []
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(heap, (lst[0], i, 0))
    
    result = []
    while heap:
        val, list_idx, elem_idx = heapq.heappop(heap)
        result.append(val)
        if elem_idx + 1 < len(lists[list_idx]):
            heapq.heappush(heap, (lists[list_idx][elem_idx + 1], list_idx, elem_idx + 1))
    return result
``` 