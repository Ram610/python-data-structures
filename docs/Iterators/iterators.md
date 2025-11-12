# Iterators in Python

## Overview
Iterators are objects that implement the iterator protocol with `__iter__()` and `__next__()` methods.

## Iterator Protocol

### How Iterators Work
```python
# Any iterable (list, tuple, string) can create an iterator
my_list = [1, 2, 3]
iterator = iter(my_list)

print(next(iterator))  # 1
print(next(iterator))  # 2
print(next(iterator))  # 3
# print(next(iterator))  # Raises StopIteration
```

### Creating Custom Iterator
```python
class Counter:
    def __init__(self, start, end):
        self.current = start
        self.end = end
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current > self.end:
            raise StopIteration
        current = self.current
        self.current += 1
        return current

# Usage
counter = Counter(1, 5)
for num in counter:
    print(num)  # 1, 2, 3, 4, 5
```

## Built-in Iterator Functions

### itertools Module
```python
import itertools

# count - infinite counter
for i in itertools.count(10, 2):
    if i > 20:
        break
    print(i)  # 10, 12, 14, 16, 18, 20

# cycle - repeat indefinitely
counter = 0
for item in itertools.cycle(['A', 'B', 'C']):
    if counter >= 6:
        break
    print(item, end=' ')  # A B C A B C
    counter += 1

# repeat - repeat n times
for item in itertools.repeat('Hello', 3):
    print(item)  # Hello (3 times)

# chain - combine iterables
combined = itertools.chain([1, 2], [3, 4], [5, 6])
print(list(combined))  # [1, 2, 3, 4, 5, 6]

# islice - slice iterator
sliced = itertools.islice(range(10), 2, 8, 2)
print(list(sliced))  # [2, 4, 6]
```

## Iterator vs Iterable

```python
# Iterable: object that can return an iterator
# Iterator: object with __next__() method

# List is iterable, not iterator
my_list = [1, 2, 3]
print(hasattr(my_list, '__iter__'))  # True
print(hasattr(my_list, '__next__'))  # False

# Get iterator from iterable
iterator = iter(my_list)
print(hasattr(iterator, '__iter__'))  # True
print(hasattr(iterator, '__next__'))  # True
```

## Practical Examples

### Infinite Sequence
```python
class InfiniteSequence:
    def __init__(self):
        self.num = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        current = self.num
        self.num += 1
        return current

# Use with limit
seq = InfiniteSequence()
for i, num in enumerate(seq):
    if i >= 10:
        break
    print(num, end=' ')  # 0 1 2 3 4 5 6 7 8 9
```

### File Line Iterator
```python
class FileLineIterator:
    def __init__(self, filename):
        self.file = open(filename, 'r')
    
    def __iter__(self):
        return self
    
    def __next__(self):
        line = self.file.readline()
        if not line:
            self.file.close()
            raise StopIteration
        return line.strip()

# Usage
for line in FileLineIterator('data.txt'):
    print(line)
```

---

## Practice Questions

### Multiple Choice Questions

**1. What methods must an iterator implement?**
a) `__iter__` and `__next__`  
b) `__init__` and `__iter__`  
c) `__next__` only  
d) `__iter__` only

**2. What does `StopIteration` indicate?**
a) Error occurred  
b) End of iteration  
c) Pause iteration  
d) Reset iterator

**3. Can you iterate over iterator multiple times?**
a) Yes, always  
b) No, exhausts after one use  
c) Only lists  
d) Depends on type

**4. What is `iter()` function for?**
a) Creates iterator from iterable  
b) Gets next item  
c) Resets iterator  
d) None

---

## Answers

**1.** a - Both `__iter__` and `__next__` required  
**2.** b - Signals end of iteration  
**3.** b - Iterators exhaust after one use  
**4.** a - Creates iterator from iterable
