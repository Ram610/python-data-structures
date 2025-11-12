# Python Internals

## Memory Management

### Reference Counting
```python
import sys

# Check reference count
a = [1, 2, 3]
print(sys.getrefcount(a))  # 2 (variable 'a' and function argument)

b = a  # Create another reference
print(sys.getrefcount(a))  # 3

del b  # Remove reference
print(sys.getrefcount(a))  # 2
```

### Garbage Collection
```python
import gc

# Manual garbage collection
gc.collect()

# Check if GC is enabled
print(gc.isenabled())  # True

# Disable/Enable GC
gc.disable()
gc.enable()

# Get GC statistics
print(gc.get_stats())
```

### Memory Allocation
```python
import sys

# Check object size
x = 10
print(sys.getsizeof(x))  # 28 bytes

list1 = [1, 2, 3]
print(sys.getsizeof(list1))  # 88 bytes

string = "Hello"
print(sys.getsizeof(string))  # 54 bytes
```

---

## Global Interpreter Lock (GIL)

### What is GIL?
The Global Interpreter Lock is a mutex that protects access to Python objects, preventing multiple threads from executing Python bytecode simultaneously.

### GIL Impact on Threading
```python
import threading
import time

# CPU-bound task (affected by GIL)
def count_up(n):
    count = 0
    for i in range(n):
        count += 1
    return count

# Single-threaded
start = time.time()
count_up(10000000)
count_up(10000000)
print(f"Single-threaded: {time.time() - start:.2f}s")

# Multi-threaded (still affected by GIL)
start = time.time()
t1 = threading.Thread(target=count_up, args=(10000000,))
t2 = threading.Thread(target=count_up, args=(10000000,))
t1.start()
t2.start()
t1.join()
t2.join()
print(f"Multi-threaded: {time.time() - start:.2f}s")
```

### Workarounds for GIL

**1. Multiprocessing (Best for CPU-bound tasks)**
```python
from multiprocessing import Pool

def square(x):
    return x * x

if __name__ == '__main__':
    with Pool(4) as p:
        result = p.map(square, [1, 2, 3, 4, 5])
    print(result)  # [1, 4, 9, 16, 25]
```

**2. Threading (Good for I/O-bound tasks)**
```python
import threading
import requests

def download_file(url):
    response = requests.get(url)
    return len(response.content)

urls = ['http://example.com'] * 10
threads = []

for url in urls:
    t = threading.Thread(target=download_file, args=(url,))
    threads.append(t)
    t.start()

for t in threads:
    t.join()
```

**3. Using C Extensions**
- NumPy, pandas release GIL for computations
- Write performance-critical code in C/C++

---

## Object Internals

### id() and is Operator
```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(id(a))  # Memory address
print(id(b))  # Same as 'a'
print(id(c))  # Different address

print(a is b)  # True (same object)
print(a is c)  # False (different objects)
print(a == c)  # True (same value)
```

### Integer Caching
```python
# Small integers (-5 to 256) are cached
a = 10
b = 10
print(a is b)  # True (same object)

# Larger integers are not cached
x = 1000
y = 1000
print(x is y)  # False (different objects)
```

### String Interning
```python
# String interning for identifiers
s1 = "hello"
s2 = "hello"
print(s1 is s2)  # True (interned)

# Strings with spaces may not be interned
s3 = "hello world"
s4 = "hello world"
print(s3 is s4)  # May be False
```

---

## Bytecode

### Viewing Bytecode
```python
import dis

def add_numbers(a, b):
    return a + b

# View bytecode
dis.dis(add_numbers)
```

### Bytecode Example Output
```
  2           0 LOAD_FAST                0 (a)
              2 LOAD_FAST                1 (b)
              4 BINARY_ADD
              6 RETURN_VALUE
```

---

## Performance Optimization

### Using __slots__
```python
# Without __slots__
class RegularClass:
    def __init__(self, x, y):
        self.x = x
        self.y = y

# With __slots__ (saves memory)
class OptimizedClass:
    __slots__ = ['x', 'y']
    
    def __init__(self, x, y):
        self.x = x
        self.y = y

import sys
r = RegularClass(1, 2)
o = OptimizedClass(1, 2)

print(sys.getsizeof(r))  # Larger
print(sys.getsizeof(o))  # Smaller
```

### Generator vs List
```python
import sys

# List (stores all in memory)
list_comp = [x for x in range(10000)]
print(sys.getsizeof(list_comp))  # ~87 KB

# Generator (lazy evaluation)
gen_exp = (x for x in range(10000))
print(sys.getsizeof(gen_exp))  # ~112 bytes
```

---

## Practice Questions

### Multiple Choice Questions

**1. What does GIL stand for?**
a) General Interface Lock  
b) Global Interpreter Lock  
c) Generic Internal Lock  
d) Global Interface Layer

**2. Which is best for CPU-bound tasks?**
a) Threading  
b) Async IO  
c) Multiprocessing  
d) Coroutines

**3. What does sys.getrefcount() return?**
a) Memory size  
b) Reference count  
c) Object ID  
d) Type

**4. Which integers are cached in Python?**
a) 0 to 100  
b) -5 to 256  
c) All integers  
d) None

**5. What is __slots__ used for?**
a) Threading  
b) Memory optimization  
c) Debugging  
d) Testing

---

## Coding Exercises

**Exercise 1:** Write code to demonstrate reference counting with sys.getrefcount().

**Exercise 2:** Compare execution time of CPU-bound task using threading vs multiprocessing.

**Exercise 3:** Create a class using __slots__ and compare memory usage with regular class.

---

## Answers

### MCQ Answers
**1.** b - Global Interpreter Lock  
**2.** c - Multiprocessing (bypasses GIL)  
**3.** b - Reference count  
**4.** b - -5 to 256 are cached  
**5.** b - Memory optimization

### Exercise Solutions

**Exercise 1:**
```python
import sys

x = [1, 2, 3]
print(f"References to x: {sys.getrefcount(x)}")

y = x
print(f"After y = x: {sys.getrefcount(x)}")

del y
print(f"After del y: {sys.getrefcount(x)}")
```

**Exercise 2:**
```python
import time
import threading
from multiprocessing import Process

def cpu_task():
    count = 0
    for i in range(10000000):
        count += 1

# Threading
start = time.time()
t1 = threading.Thread(target=cpu_task)
t2 = threading.Thread(target=cpu_task)
t1.start()
t2.start()
t1.join()
t2.join()
print(f"Threading: {time.time() - start:.2f}s")

# Multiprocessing
start = time.time()
p1 = Process(target=cpu_task)
p2 = Process(target=cpu_task)
p1.start()
p2.start()
p1.join()
p2.join()
print(f"Multiprocessing: {time.time() - start:.2f}s")
```

**Exercise 3:**
```python
import sys

class RegularClass:
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z

class SlottedClass:
    __slots__ = ['x', 'y', 'z']
    
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z

regular = RegularClass(1, 2, 3)
slotted = SlottedClass(1, 2, 3)

print(f"Regular class: {sys.getsizeof(regular)} bytes")
print(f"Slotted class: {sys.getsizeof(slotted)} bytes")
print(f"Memory saved: {sys.getsizeof(regular) - sys.getsizeof(slotted)} bytes")
```
