# List Comprehensions & Generators in Python

## List Comprehensions

### Basic Syntax
```python
# Basic list comprehension
squares = [x**2 for x in range(10)]
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
evens = [x for x in range(20) if x % 2 == 0]
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# With if-else
numbers = [x if x % 2 == 0 else -x for x in range(10)]
# [0, -1, 2, -3, 4, -5, 6, -7, 8, -9]
```

### Nested Loops
```python
# Nested comprehension
matrix = [[i*j for j in range(3)] for i in range(3)]
# [[0, 0, 0], [0, 1, 2], [0, 2, 4]]

# Flatten list
nested = [[1, 2], [3, 4], [5, 6]]
flat = [item for sublist in nested for item in sublist]
# [1, 2, 3, 4, 5, 6]
```

## Dictionary Comprehensions

```python
# Basic dict comprehension
squares_dict = {x: x**2 for x in range(6)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# From two lists
keys = ['a', 'b', 'c']
values = [1, 2, 3]
dict_comp = {k: v for k, v in zip(keys, values)}
# {'a': 1, 'b': 2, 'c': 3}

# With condition
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
# {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}

# Swap keys and values
original = {'a': 1, 'b': 2}
swapped = {v: k for k, v in original.items()}
# {1: 'a', 2: 'b'}
```

## Set Comprehensions

```python
# Basic set comprehension
unique_squares = {x**2 for x in [1, 1, 2, 2, 3, 3]}
# {1, 4, 9}

# With condition
vowels = {char.lower() for char in "Hello World" if char.lower() in 'aeiou'}
# {'e', 'o'}
```

## Generator Expressions

### What are Generators?
Generators produce items one at a time and are memory-efficient for large datasets.

```python
# Generator expression (uses parentheses)
gen = (x**2 for x in range(10))
print(type(gen))  # <class 'generator'>

# Iterate through generator
for value in gen:
    print(value)

# Convert to list
squares_list = list((x**2 for x in range(10)))
```

### Generator Functions

```python
def countdown(n):
    """Generator function"""
    while n > 0:
        yield n
        n -= 1

# Using generator
for num in countdown(5):
    print(num)  # 5, 4, 3, 2, 1

# Generator object
gen = countdown(3)
print(next(gen))  # 3
print(next(gen))  # 2
print(next(gen))  # 1
# print(next(gen))  # StopIteration
```

### Generator vs List Comprehension

```python
# List comprehension - creates entire list in memory
list_comp = [x**2 for x in range(1000000)]  # Uses lots of memory

# Generator - produces values on demand
gen_exp = (x**2 for x in range(1000000))  # Memory efficient

# Memory comparison
import sys
print(sys.getsizeof(list_comp))  # Large
print(sys.getsizeof(gen_exp))  # Small
```

## Advanced Examples

### Fibonacci Generator
```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

# Get first 10 Fibonacci numbers
fib = list(fibonacci(10))
# [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

### File Reading Generator
```python
def read_large_file(file_path):
    """Memory-efficient file reading"""
    with open(file_path) as file:
        for line in file:
            yield line.strip()

# Usage
for line in read_large_file('large_file.txt'):
    process(line)
```

### Pipeline with Generators
```python
def numbers():
    for i in range(10):
        yield i

def squares(nums):
    for n in nums:
        yield n**2

def filter_even(nums):
    for n in nums:
        if n % 2 == 0:
            yield n

# Chain generators
pipeline = filter_even(squares(numbers()))
print(list(pipeline))  # [0, 4, 16, 36, 64]
```

## Common Use Cases

### 1. Data Transformation
```python
# Convert names to uppercase
names = ['alice', 'bob', 'charlie']
upper_names = [name.upper() for name in names]

# Extract specific fields
users = [{'name': 'Alice', 'age': 25}, {'name': 'Bob', 'age': 30}]
names = [user['name'] for user in users]
```

### 2. Filtering
```python
# Filter positive numbers
numbers = [-2, -1, 0, 1, 2, 3]
positives = [n for n in numbers if n > 0]

# Complex filtering
words = ['hello', 'world', 'python', 'programming']
long_words = [w for w in words if len(w) > 5]
```

### 3. Matrix Operations
```python
# Transpose matrix
matrix = [[1, 2, 3], [4, 5, 6]]
transposed = [[row[i] for row in matrix] for i in range(3)]
# [[1, 4], [2, 5], [3, 6]]
```

---

## Practice Questions

### Multiple Choice Questions

**1. What's the difference between `[]` and `()` in comprehensions?**
a) No difference  
b) `[]` creates list, `()` creates generator  
c) `()` creates tuple  
d) Both create lists

**2. Are generators memory efficient?**
a) Yes  
b) No  
c) Same as lists  
d) Depends on size

**3. What does `yield` do?**
a) Returns and exits function  
b) Returns value and pauses  
c) Raises exception  
d) Nothing

**4. Can you have nested comprehensions?**
a) Yes  
b) No  
c) Only in Python 3  
d) Only for lists

**5. What is `next()` used for?**
a) Get next item from generator  
b) Skip item  
c) Reset generator  
d) Delete item

---

## Coding Exercises

**Exercise 1:** Create list comprehension to get squares of odd numbers from 1-20.

**Exercise 2:** Write dict comprehension to create {letter: position} for 'PYTHON'.

**Exercise 3:** Create generator function for prime numbers up to n.

**Exercise 4:** Use comprehension to flatten nested list `[[1,2],[3,4],[5,6]]`.

**Exercise 5:** Write generator that yields factorial of numbers.

---

## Answers

### Solutions

**Solution 1:**
```python
odd_squares = [x**2 for x in range(1, 21) if x % 2 != 0]
print(odd_squares)
# [1, 9, 25, 49, 81, 121, 169, 225, 289, 361]
```

**Solution 2:**
```python
word = 'PYTHON'
letter_position = {letter: idx for idx, letter in enumerate(word, 1)}
print(letter_position)
# {'P': 1, 'Y': 2, 'T': 3, 'H': 4, 'O': 5, 'N': 6}
```

**Solution 3:**
```python
def prime_generator(n):
    """Generate prime numbers up to n"""
    for num in range(2, n + 1):
        is_prime = True
        for i in range(2, int(num**0.5) + 1):
            if num % i == 0:
                is_prime = False
                break
        if is_prime:
            yield num

# Test
primes = list(prime_generator(20))
print(primes)  # [2, 3, 5, 7, 11, 13, 17, 19]
```

**Solution 4:**
```python
nested = [[1, 2], [3, 4], [5, 6]]
flattened = [item for sublist in nested for item in sublist]
print(flattened)  # [1, 2, 3, 4, 5, 6]
```

**Solution 5:**
```python
def factorial_generator(n):
    """Generate factorials from 0! to n!"""
    factorial = 1
    for i in range(n + 1):
        if i == 0:
            yield 1
        else:
            factorial *= i
            yield factorial

# Test
factorials = list(factorial_generator(5))
print(factorials)  # [1, 1, 2, 6, 24, 120]
```
