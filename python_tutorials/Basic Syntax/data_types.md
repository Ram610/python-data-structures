# Data Types in Python

Data types in Python define the type of data a variable can hold. Python is a dynamically typed language, meaning you don't need to declare the type of a variable explicitly.

## 1. **Numeric Types**
Python supports three types of numeric data:
- **int**: Integer values (e.g., `10`, `-5`)
- **float**: Floating-point numbers (e.g., `3.14`, `-0.01`)
- **complex**: Complex numbers with real and imaginary parts (e.g., `3+4j`)

### Example:
```python
x = 10       # int
y = 3.14     # float
z = 2 + 3j   # complex
```

## 2. **Sequence Types**
Sequence types represent ordered collections of items.
- **str**: String, a sequence of characters (e.g., `"Hello"`)
- **list**: Mutable, ordered collection (e.g., `[1, 2, 3]`)
- **tuple**: Immutable, ordered collection (e.g., `(1, 2, 3)`)

### Example:
```python
s = "Python"          # str
lst = [1, 2, 3]       # list
tpl = (1, 2, 3)       # tuple
```

## 3. **Mapping Type**
- **dict**: A collection of key-value pairs (e.g., `{"name": "Alice", "age": 25}`)

### Example:
```python
person = {"name": "Alice", "age": 25}
```

## 4. **Set Types**
- **set**: Unordered collection of unique items (e.g., `{1, 2, 3}`)
- **frozenset**: Immutable version of a set

### Example:
```python
s = {1, 2, 3}          # set
fs = frozenset([1, 2]) # frozenset
```

## 5. **Boolean Type**
- **bool**: Represents `True` or `False`

### Example:
```python
is_active = True
```

## 6. **Binary Types**
- **bytes**: Immutable sequence of bytes (e.g., `b"data"`)
- **bytearray**: Mutable sequence of bytes
- **memoryview**: Memory view object

### Example:
```python
b = b"data"               # bytes
ba = bytearray(b"data")   # bytearray
mv = memoryview(b)        # memoryview
```

## 7. **None Type**
- **NoneType**: Represents the absence of a value (`None`)

### Example:
```python
x = None
```

## Type Checking
You can check the type of a variable using the `type()` function:
```python
x = 10
print(type(x))  # Output: <class 'int'>
```

## Type Conversion
Python allows explicit type conversion using functions like `int()`, `float()`, `str()`, etc.
```python
x = "123"
y = int(x)  # Converts string to integer
```

## Summary Table

| Data Type   | Description                     | Example                  |
|-------------|---------------------------------|--------------------------|
| `int`       | Integer                         | `10`, `-5`              |
| `float`     | Floating-point number           | `3.14`, `-0.01`         |
| `complex`   | Complex number                  | `3+4j`                  |
| `str`       | String                          | `"Hello"`               |
| `list`      | Mutable sequence                | `[1, 2, 3]`             |
| `tuple`     | Immutable sequence              | `(1, 2, 3)`             |
| `dict`      | Key-value pairs                 | `{"key": "value"}`      |
| `set`       | Unordered unique collection     | `{1, 2, 3}`             |
| `frozenset` | Immutable set                   | `frozenset([1, 2])`     |
| `bool`      | Boolean                         | `True`, `False`         |
| `bytes`     | Immutable byte sequence         | `b"data"`               |
| `bytearray` | Mutable byte sequence           | `bytearray(b"data")`    |
| `NoneType`  | Represents no value             | `None`                  |


## Interview Questions on Python Data Types

### 1. **What are the different data types in Python?**
**Answer:** Python has the following built-in data types:
- Numeric types: `int`, `float`, `complex`
- Sequence types: `str`, `list`, `tuple`
- Mapping type: `dict`
- Set types: `set`, `frozenset`
- Boolean type: `bool`
- Binary types: `bytes`, `bytearray`, `memoryview`
- None type: `NoneType`

---

### 2. **What is the difference between `list` and `tuple`?**
**Answer:**
- `list`: Mutable, meaning you can modify its elements after creation.
- `tuple`: Immutable, meaning its elements cannot be changed after creation.

Example:
```python
lst = [1, 2, 3]  # Mutable
tpl = (1, 2, 3)  # Immutable
```

---

### 3. **What is the difference between `set` and `frozenset`?**
**Answer:**
- `set`: Mutable, allowing addition and removal of elements.
- `frozenset`: Immutable, meaning it cannot be modified after creation.

Example:
```python
s = {1, 2, 3}          # set
fs = frozenset([1, 2]) # frozenset
```

---

### 4. **How do you check the type of a variable in Python?**
**Answer:** Use the `type()` function.
Example:
```python
x = 10
print(type(x))  # Output: <class 'int'>
```

---

### 5. **What is the purpose of the `None` type in Python?**
**Answer:** `None` represents the absence of a value or a null value. It is of type `NoneType`.

Example:
```python
x = None
print(x)  # Output: None
```

---

### 6. **What is the difference between `bytes` and `bytearray`?**
**Answer:**
- `bytes`: Immutable sequence of bytes.
- `bytearray`: Mutable sequence of bytes.

Example:
```python
b = b"data"               # bytes
ba = bytearray(b"data")   # bytearray
```

---

### 7. **How can you convert one data type to another in Python?**
**Answer:** Use type conversion functions like `int()`, `float()`, `str()`, etc.

Example:
```python
x = "123"
y = int(x)  # Converts string to integer
```

---

### 8. **What is the difference between `is` and `==` in Python?**
**Answer:**
- `is`: Checks if two variables point to the same object in memory.
- `==`: Checks if the values of two variables are equal.

Example:
```python
a = [1, 2, 3]
b = [1, 2, 3]
print(a == b)  # True (values are equal)
print(a is b)  # False (different objects in memory)
```

---

### 9. **What are mutable and immutable data types in Python?**
**Answer:**
- Mutable: Can be modified after creation (e.g., `list`, `dict`, `set`, `bytearray`).
- Immutable: Cannot be modified after creation (e.g., `int`, `float`, `str`, `tuple`, `frozenset`, `bytes`).

---

### 10. **What is a `complex` number in Python?**
**Answer:** A `complex` number has a real and an imaginary part, represented as `a + bj`, where `a` is the real part and `b` is the imaginary part.

Example:
```python
z = 3 + 4j
print(z.real)  # Output: 3.0
print(z.imag)  # Output: 4.0
```

---

### 11. **What is the difference between `str` and `bytes`?**
**Answer:**
- `str`: Represents a sequence of Unicode characters.
- `bytes`: Represents a sequence of bytes (binary data).

Example:
```python
s = "Hello"  # str
b = b"Hello" # bytes
```

---

### 12. **How do you create an empty dictionary, list, and tuple?**
**Answer:**
- Empty dictionary: `{}`
- Empty list: `[]`
- Empty tuple: `()`

Example:
```python
d = {}      # Empty dictionary
lst = []    # Empty list
tpl = ()    # Empty tuple
```

---

### 13. **What is the difference between `dict` and `list`?**
**Answer:**
- `dict`: Stores key-value pairs, unordered.
- `list`: Stores ordered elements, indexed by position.

Example:
```python
d = {"key": "value"}  # dict
lst = [1, 2, 3]       # list
```

---

### 14. **What is the output of `type(None)`?**
**Answer:** The output is `<class 'NoneType'>`.

Example:
```python
print(type(None))  # Output: <class 'NoneType'>
```

---

### 15. **What is the difference between `int` and `float`?**
**Answer:**
- `int`: Represents whole numbers (e.g., `10`, `-5`).
- `float`: Represents numbers with decimal points (e.g., `3.14`, `-0.01`).

Example:
```python
x = 10    # int
y = 3.14  # float
```