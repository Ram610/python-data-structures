# Tuples in Python

## Overview
Tuples are **immutable** sequences in Python, typically used to store collections of heterogeneous data. Once created, tuples cannot be modified.

## Key Characteristics
- **Immutable**: Cannot change elements after creation
- **Ordered**: Elements maintain their position
- **Allow duplicates**: Can contain duplicate values
- **Indexed**: Access elements by index (starting from 0)
- **Heterogeneous**: Can contain different data types

## Creating Tuples

```python
# Empty tuple
empty_tuple = ()
empty_tuple = tuple()

# Tuple with elements
numbers = (1, 2, 3, 4, 5)
mixed = (1, "hello", 3.14, True)

# Single element tuple (note the comma)
single = (5,)  # Correct
not_tuple = (5)  # This is just an integer

# Tuple without parentheses
my_tuple = 1, 2, 3  # Valid tuple

# Tuple from other iterables
list_to_tuple = tuple([1, 2, 3])
string_to_tuple = tuple("hello")  # ('h', 'e', 'l', 'l', 'o')
```

## Accessing Tuple Elements

```python
fruits = ("apple", "banana", "cherry", "date")

# Indexing
print(fruits[0])   # Output: apple
print(fruits[-1])  # Output: date

# Slicing
print(fruits[1:3])   # Output: ('banana', 'cherry')
print(fruits[:2])    # Output: ('apple', 'banana')
print(fruits[2:])    # Output: ('cherry', 'date')
print(fruits[::2])   # Output: ('apple', 'cherry')
```

## Tuple Methods

```python
numbers = (1, 2, 3, 2, 4, 2, 5)

# count() - returns the number of times a value appears
count = numbers.count(2)  # Output: 3

# index() - returns the index of first occurrence
index = numbers.index(3)  # Output: 2

# Length
length = len(numbers)  # Output: 7
```

## Tuple Operations

```python
# Concatenation
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)
combined = tuple1 + tuple2  # (1, 2, 3, 4, 5, 6)

# Repetition
repeated = tuple1 * 3  # (1, 2, 3, 1, 2, 3, 1, 2, 3)

# Membership
print(2 in tuple1)      # Output: True
print(10 not in tuple1) # Output: True

# Unpacking
a, b, c = (1, 2, 3)
print(a, b, c)  # Output: 1 2 3

# Extended unpacking
first, *middle, last = (1, 2, 3, 4, 5)
print(first)   # Output: 1
print(middle)  # Output: [2, 3, 4]
print(last)    # Output: 5
```

## Nested Tuples

```python
nested = ((1, 2), (3, 4), (5, 6))
print(nested[0])     # Output: (1, 2)
print(nested[1][0])  # Output: 3

# Mixed nesting
mixed_nested = (1, [2, 3], (4, 5))
mixed_nested[1].append(6)  # Lists inside tuples can be modified
print(mixed_nested)  # Output: (1, [2, 3, 6], (4, 5))
```

## Tuple vs List

| Feature | Tuple | List |
|---------|-------|------|
| Mutability | Immutable | Mutable |
| Syntax | () | [] |
| Performance | Faster | Slower |
| Methods | Limited (2) | Many |
| Use Case | Fixed data | Dynamic data |

## When to Use Tuples
1. **Immutable data**: When you want to ensure data doesn't change
2. **Dictionary keys**: Tuples can be dictionary keys (lists cannot)
3. **Function returns**: Return multiple values from a function
4. **Performance**: Slightly faster than lists for iteration

## Common Use Cases

```python
# Function returning multiple values
def get_coordinates():
    return (10, 20)

x, y = get_coordinates()

# Dictionary with tuple keys
locations = {
    (0, 0): "Origin",
    (1, 2): "Point A",
    (3, 4): "Point B"
}

# Named tuples for better readability
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(10, 20)
print(p.x, p.y)  # Output: 10 20
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is the output of the following code?**
```python
t = (1, 2, 3)
print(type(t[0]))
```
a) `<class 'tuple'>`  
b) `<class 'int'>`  
c) `<class 'list'>`  
d) Error

**2. Which of the following creates a tuple with a single element?**
a) `t = (5)`  
b) `t = [5]`  
c) `t = (5,)`  
d) `t = {5}`

**3. Can tuples be used as dictionary keys?**
a) Yes, always  
b) No, never  
c) Yes, if they contain only immutable elements  
d) Only if they contain strings

**4. What will be the output?**
```python
t = (1, 2, 3, 2, 4)
print(t.count(2))
```
a) 1  
b) 2  
c) 3  
d) Error

**5. Which operation is NOT possible with tuples?**
a) Indexing  
b) Slicing  
c) Appending  
d) Concatenation

**6. What is the output?**
```python
t = (1, 2, 3)
t = t + (4, 5)
print(len(t))
```
a) 3  
b) 5  
c) Error  
d) None

**7. Which statement is true about tuples?**
a) Tuples are mutable  
b) Tuples are faster than lists  
c) Tuples cannot contain lists  
d) Tuples cannot be nested

**8. What will this code print?**
```python
a, *b, c = (1, 2, 3, 4, 5)
print(b)
```
a) `[2, 3, 4]`  
b) `(2, 3, 4)`  
c) `2, 3, 4`  
d) Error

---

### Coding Exercises

**Exercise 1: Tuple Basics**
Write a function that takes a tuple of numbers and returns a new tuple containing only the even numbers.

**Exercise 2: Tuple Unpacking**
Create a function that swaps the first and last elements of a tuple and returns the new tuple.

**Exercise 3: Nested Tuples**
Given a tuple of tuples representing coordinates `((1, 2), (3, 4), (5, 6))`, write a function to calculate the sum of all x-coordinates and y-coordinates separately.

**Exercise 4: Tuple Operations**
Write a function that takes two tuples and returns a tuple containing:
- Elements common to both tuples
- Elements unique to the first tuple
- Elements unique to the second tuple

**Exercise 5: Data Processing**
Create a function that takes a tuple of student records (name, age, grade) and returns:
- The average age
- The student with the highest grade
- A sorted tuple by name

---

## Answers

### Multiple Choice Answers
1. **b** - The element at index 0 is an integer
2. **c** - Single element tuples need a trailing comma
3. **c** - Tuples with only immutable elements can be dictionary keys
4. **b** - The number 2 appears twice in the tuple
5. **c** - Tuples are immutable, so appending is not possible
6. **b** - The concatenation creates a new tuple with 5 elements
7. **b** - Tuples are generally faster than lists due to immutability
8. **a** - Extended unpacking creates a list for middle elements

### Coding Exercise Solutions

**Solution 1:**
```python
def get_even_numbers(t):
    return tuple(x for x in t if x % 2 == 0)

# Test
numbers = (1, 2, 3, 4, 5, 6, 7, 8)
print(get_even_numbers(numbers))  # Output: (2, 4, 6, 8)
```

**Solution 2:**
```python
def swap_first_last(t):
    if len(t) < 2:
        return t
    return (t[-1],) + t[1:-1] + (t[0],)

# Test
my_tuple = (1, 2, 3, 4, 5)
print(swap_first_last(my_tuple))  # Output: (5, 2, 3, 4, 1)
```

**Solution 3:**
```python
def sum_coordinates(coords):
    sum_x = sum(coord[0] for coord in coords)
    sum_y = sum(coord[1] for coord in coords)
    return (sum_x, sum_y)

# Test
coordinates = ((1, 2), (3, 4), (5, 6))
print(sum_coordinates(coordinates))  # Output: (9, 12)
```

**Solution 4:**
```python
def tuple_operations(t1, t2):
    common = tuple(x for x in t1 if x in t2)
    unique_t1 = tuple(x for x in t1 if x not in t2)
    unique_t2 = tuple(x for x in t2 if x not in t1)
    return (common, unique_t1, unique_t2)

# Test
tuple1 = (1, 2, 3, 4, 5)
tuple2 = (4, 5, 6, 7, 8)
print(tuple_operations(tuple1, tuple2))
# Output: ((4, 5), (1, 2, 3), (6, 7, 8))
```

**Solution 5:**
```python
def process_students(students):
    # Average age
    avg_age = sum(student[1] for student in students) / len(students)
    
    # Student with highest grade
    top_student = max(students, key=lambda x: x[2])
    
    # Sorted by name
    sorted_students = tuple(sorted(students, key=lambda x: x[0]))
    
    return {
        'average_age': avg_age,
        'top_student': top_student,
        'sorted': sorted_students
    }

# Test
students = (
    ("Alice", 20, 85),
    ("Bob", 22, 92),
    ("Charlie", 21, 88)
)
result = process_students(students)
print(result)
# Output: {'average_age': 21.0, 'top_student': ('Bob', 22, 92), 
#          'sorted': (('Alice', 20, 85), ('Bob', 22, 92), ('Charlie', 21, 88))}
```
