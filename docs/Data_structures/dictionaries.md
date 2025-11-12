# Dictionaries in Python

## Overview
Dictionaries are **mutable**, **unordered** collections of key-value pairs. They provide fast lookups and are one of the most versatile data structures in Python.

## Key Characteristics
- **Key-Value Pairs**: Each item consists of a key and its associated value
- **Mutable**: Can add, remove, or modify items
- **Unordered** (Python 3.6-): Maintains insertion order in Python 3.7+
- **Unique Keys**: Keys must be unique; values can be duplicated
- **Fast Lookup**: O(1) average time complexity for access
- **Keys Must Be Immutable**: strings, numbers, tuples (not lists)

## Creating Dictionaries

```python
# Empty dictionary
empty_dict = {}
empty_dict = dict()

# Dictionary with initial values
student = {
    "name": "Alice",
    "age": 20,
    "grade": "A"
}

# Using dict() constructor
person = dict(name="Bob", age=25, city="New York")

# From list of tuples
pairs = [("a", 1), ("b", 2), ("c", 3)]
dict_from_pairs = dict(pairs)

# Dictionary comprehension
squares = {x: x**2 for x in range(6)}
# Output: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Using dict.fromkeys()
keys = ['a', 'b', 'c']
default_dict = dict.fromkeys(keys, 0)
# Output: {'a': 0, 'b': 0, 'c': 0}
```

## Accessing Dictionary Elements

```python
student = {"name": "Alice", "age": 20, "grade": "A"}

# Using square brackets
print(student["name"])  # Output: Alice
# print(student["marks"])  # KeyError if key doesn't exist

# Using get() - safer method
print(student.get("age"))  # Output: 20
print(student.get("marks"))  # Output: None
print(student.get("marks", 0))  # Output: 0 (default value)

# Check if key exists
if "name" in student:
    print(student["name"])

# Get all keys
keys = student.keys()  # dict_keys(['name', 'age', 'grade'])

# Get all values
values = student.values()  # dict_values(['Alice', 20, 'A'])

# Get all items (key-value pairs)
items = student.items()  # dict_items([('name', 'Alice'), ('age', 20), ('grade', 'A')])
```

## Modifying Dictionaries

```python
student = {"name": "Alice", "age": 20}

# Adding/Updating items
student["grade"] = "A"  # Add new key-value pair
student["age"] = 21  # Update existing value

# Using update() - merge dictionaries
student.update({"city": "Boston", "major": "CS"})
student.update(age=22, year=2)

# Removing items
del student["major"]  # Remove specific key

grade = student.pop("grade")  # Remove and return value
print(grade)  # Output: A

# Remove last inserted item (Python 3.7+)
last_item = student.popitem()  
print(last_item)  # Output: tuple of (key, value)

# Clear all items
student.clear()  # {}
```

## Dictionary Methods

```python
person = {"name": "Bob", "age": 25, "city": "NYC"}

# setdefault() - get value or set default if key doesn't exist
age = person.setdefault("age", 0)  # Returns 25
country = person.setdefault("country", "USA")  # Adds and returns "USA"

# copy() - shallow copy
person_copy = person.copy()

# get all keys, values, items
keys = list(person.keys())
values = list(person.values())
items = list(person.items())
```

## Iterating Through Dictionaries

```python
student = {"name": "Alice", "age": 20, "grade": "A"}

# Iterate over keys (default)
for key in student:
    print(key)

# Iterate over keys explicitly
for key in student.keys():
    print(key, student[key])

# Iterate over values
for value in student.values():
    print(value)

# Iterate over key-value pairs
for key, value in student.items():
    print(f"{key}: {value}")
```

## Nested Dictionaries

```python
# Dictionary of dictionaries
students = {
    "student1": {
        "name": "Alice",
        "age": 20,
        "grades": [85, 90, 92]
    },
    "student2": {
        "name": "Bob",
        "age": 22,
        "grades": [78, 85, 88]
    }
}

# Accessing nested values
print(students["student1"]["name"])  # Output: Alice
print(students["student2"]["grades"][0])  # Output: 78

# Modifying nested values
students["student1"]["age"] = 21
students["student2"]["grades"].append(90)
```

## Dictionary Comprehensions

```python
# Basic comprehension
squares = {x: x**2 for x in range(6)}

# With condition
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}

# From two lists
keys = ['a', 'b', 'c']
values = [1, 2, 3]
combined = {k: v for k, v in zip(keys, values)}

# Swap keys and values
original = {'a': 1, 'b': 2, 'c': 3}
swapped = {v: k for k, v in original.items()}
# Output: {1: 'a', 2: 'b', 3: 'c'}

# Filtering
data = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
filtered = {k: v for k, v in data.items() if v > 2}
# Output: {'c': 3, 'd': 4}
```

## Common Use Cases

### Counting Occurrences

```python
# Manual counting
text = "hello world"
char_count = {}
for char in text:
    char_count[char] = char_count.get(char, 0) + 1

# Using Counter
from collections import Counter
char_count = Counter(text)
print(char_count.most_common(3))  # Top 3 most common
```

### Grouping Data

```python
students = [
    {"name": "Alice", "grade": "A"},
    {"name": "Bob", "grade": "B"},
    {"name": "Charlie", "grade": "A"},
    {"name": "David", "grade": "B"}
]

# Group by grade
by_grade = {}
for student in students:
    grade = student["grade"]
    if grade not in by_grade:
        by_grade[grade] = []
    by_grade[grade].append(student["name"])

print(by_grade)
# Output: {'A': ['Alice', 'Charlie'], 'B': ['Bob', 'David']}
```

### Caching/Memoization

```python
cache = {}

def fibonacci(n):
    if n in cache:
        return cache[n]
    if n <= 1:
        return n
    result = fibonacci(n-1) + fibonacci(n-2)
    cache[n] = result
    return result
```

## Default Dictionaries

```python
from collections import defaultdict

# Auto-initialize with default value
word_count = defaultdict(int)  # default value 0
word_count['apple'] += 1  # No KeyError

# Group items
groups = defaultdict(list)  # default value []
groups['fruits'].append('apple')
groups['fruits'].append('banana')

print(dict(groups))  # {'fruits': ['apple', 'banana']}
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is the output of the following code?**
```python
d = {"a": 1, "b": 2}
print(d.get("c", 3))
```
a) Error  
b) None  
c) 3  
d) 0

**2. Which data type CANNOT be used as a dictionary key?**
a) String  
b) Integer  
c) List  
d) Tuple

**3. What is the time complexity of accessing a value in a dictionary?**
a) O(n)  
b) O(log n)  
c) O(1)  
d) O(n²)

**4. What does the `setdefault()` method do?**
a) Sets a default value for all keys  
b) Returns value if key exists, otherwise sets and returns default  
c) Deletes a key  
d) Updates multiple keys

**5. What is the output?**
```python
d = {'a': 1, 'b': 2}
d['c'] = 3
print(len(d))
```
a) 2  
b) 3  
c) 4  
d) Error

**6. How do you create an empty dictionary?**
a) `d = []`  
b) `d = ()`  
c) `d = {}`  
d) `d = set()`

**7. What does `dict.items()` return?**
a) List of keys  
b) List of values  
c) List of key-value tuples  
d) String

**8. Can dictionary values be mutable objects like lists?**
a) No, never  
b) Yes, always  
c) Only in Python 3  
d) Only if keys are strings

**9. What is the output?**
```python
d = {'a': 1, 'b': 2, 'a': 3}
print(d['a'])
```
a) 1  
b) 3  
c) [1, 3]  
d) Error

**10. Which method removes and returns an arbitrary key-value pair?**
a) `remove()`  
b) `pop()`  
c) `popitem()`  
d) `delete()`

---

### Coding Exercises

**Exercise 1: Word Frequency**
Write a function that takes a string and returns a dictionary with the frequency of each word (case-insensitive).

**Exercise 2: Merge Dictionaries**
Create a function that merges multiple dictionaries. If a key appears in multiple dictionaries, sum their values.

**Exercise 3: Invert Dictionary**
Write a function that inverts a dictionary (keys become values, values become keys). Handle cases where multiple keys have the same value by creating a list of keys.

**Exercise 4: Nested Dictionary Operations**
Given a nested dictionary representing a company structure, write functions to:
- Find all employees in a specific department
- Calculate total salary of all employees
- Find the employee with the highest salary

**Exercise 5: Dictionary from Lists**
Create a function that takes two lists (keys and values) and returns a dictionary. Handle cases where lists have different lengths.

---

## Answers

### Multiple Choice Answers
1. **c** - `get()` returns default value (3) when key doesn't exist
2. **c** - Lists are mutable and cannot be dictionary keys
3. **c** - Dictionary access is O(1) average case
4. **b** - `setdefault()` returns value if exists, else sets default and returns it
5. **b** - Dictionary has 3 keys after adding 'c'
6. **c** - `{}` creates an empty dictionary
7. **c** - `items()` returns view of key-value tuples
8. **b** - Values can be any type, including mutable objects
9. **b** - Duplicate keys: last value (3) overwrites previous
10. **c** - `popitem()` removes and returns last inserted key-value pair

### Coding Exercise Solutions

**Solution 1:**
```python
def word_frequency(text):
    words = text.lower().split()
    frequency = {}
    for word in words:
        # Remove punctuation
        word = ''.join(char for char in word if char.isalnum())
        frequency[word] = frequency.get(word, 0) + 1
    return frequency

# Test
text = "Hello world! Hello Python. Python is great."
print(word_frequency(text))
# Output: {'hello': 2, 'world': 1, 'python': 2, 'is': 1, 'great': 1}
```

**Solution 2:**
```python
def merge_dictionaries(*dicts):
    result = {}
    for d in dicts:
        for key, value in d.items():
            result[key] = result.get(key, 0) + value
    return result

# Test
d1 = {'a': 1, 'b': 2}
d2 = {'b': 3, 'c': 4}
d3 = {'a': 5, 'd': 6}
print(merge_dictionaries(d1, d2, d3))
# Output: {'a': 6, 'b': 5, 'c': 4, 'd': 6}
```

**Solution 3:**
```python
def invert_dictionary(d):
    inverted = {}
    for key, value in d.items():
        if value in inverted:
            if isinstance(inverted[value], list):
                inverted[value].append(key)
            else:
                inverted[value] = [inverted[value], key]
        else:
            inverted[value] = key
    return inverted

# Test
original = {'a': 1, 'b': 2, 'c': 1, 'd': 3}
print(invert_dictionary(original))
# Output: {1: ['a', 'c'], 2: 'b', 3: 'd'}
```

**Solution 4:**
```python
def analyze_company(company):
    # company structure example:
    # {
    #     "Engineering": [
    #         {"name": "Alice", "salary": 100000},
    #         {"name": "Bob", "salary": 90000}
    #     ],
    #     "Sales": [
    #         {"name": "Charlie", "salary": 80000}
    #     ]
    # }
    
    def get_employees_by_dept(dept):
        return company.get(dept, [])
    
    def total_salary():
        total = 0
        for dept in company.values():
            for employee in dept:
                total += employee['salary']
        return total
    
    def highest_paid():
        max_employee = None
        max_salary = 0
        for dept in company.values():
            for employee in dept:
                if employee['salary'] > max_salary:
                    max_salary = employee['salary']
                    max_employee = employee
        return max_employee
    
    return {
        'get_employees': get_employees_by_dept,
        'total_salary': total_salary(),
        'highest_paid': highest_paid()
    }

# Test
company = {
    "Engineering": [
        {"name": "Alice", "salary": 100000},
        {"name": "Bob", "salary": 90000}
    ],
    "Sales": [
        {"name": "Charlie", "salary": 80000},
        {"name": "David", "salary": 85000}
    ]
}

result = analyze_company(company)
print(f"Total Salary: ${result['total_salary']}")
print(f"Highest Paid: {result['highest_paid']}")
# Output: Total Salary: $355000
#         Highest Paid: {'name': 'Alice', 'salary': 100000}
```

**Solution 5:**
```python
def dict_from_lists(keys, values):
    # Handle different lengths
    length = min(len(keys), len(values))
    result = {}
    
    for i in range(length):
        result[keys[i]] = values[i]
    
    # Alternative using zip
    # result = dict(zip(keys, values))
    
    return result

# Test
keys = ['a', 'b', 'c', 'd']
values = [1, 2, 3]
print(dict_from_lists(keys, values))
# Output: {'a': 1, 'b': 2, 'c': 3}

# With equal lengths
keys2 = ['x', 'y', 'z']
values2 = [10, 20, 30]
print(dict_from_lists(keys2, values2))
# Output: {'x': 10, 'y': 20, 'z': 30}
```
