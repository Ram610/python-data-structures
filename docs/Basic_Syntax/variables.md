# Python Variables

## What is a Variable?
A variable in Python is a symbolic name that is a reference or pointer to an object. Once an object is assigned to a variable, you can refer to the object by that name.

### Key Points:
- Variables do not need explicit declaration.
- The type of a variable is determined dynamically based on the value assigned.
- Variables are case-sensitive.

---

## Rules for Naming Variables
1. Must start with a letter (a-z, A-Z) or an underscore (_).
2. Cannot start with a number.
3. Can only contain alphanumeric characters and underscores (a-z, A-Z, 0-9, _).
4. Cannot use reserved keywords (e.g., `if`, `else`, `class`, etc.).
5. Variable names are case-sensitive (`age` and `Age` are different).

---

## Assigning Values to Variables
Python allows multiple ways to assign values to variables:

### Single Assignment
```python
x = 10
name = "Alice"
```

### Multiple Assignments
```python
a, b, c = 1, 2, 3
```

### Same Value to Multiple Variables
```python
x = y = z = 100
```

---

## Variable Types
Python is dynamically typed, so you don't need to declare the type of a variable. Common types include:
- **int**: Integer values (e.g., `x = 10`)
- **float**: Decimal values (e.g., `pi = 3.14`)
- **str**: Strings (e.g., `name = "Alice"`)
- **bool**: Boolean values (`True` or `False`)
- **list**: Ordered, mutable collections (e.g., `nums = [1, 2, 3]`)
- **tuple**: Ordered, immutable collections (e.g., `coords = (1, 2)`)
- **dict**: Key-value pairs (e.g., `person = {"name": "Alice", "age": 25}`)
- **set**: Unordered, unique collections (e.g., `unique_nums = {1, 2, 3}`)

---

## Variable Scope
### Local Variables
Defined inside a function and accessible only within that function.

### Global Variables
Defined outside any function and accessible throughout the program.

### Example:
```python
x = 10  # Global variable

def my_function():
    y = 5  # Local variable
    print(x + y)

my_function()
```

---

## Constants
Python does not have built-in constant types. By convention, constants are written in uppercase:
```python
PI = 3.14159
GRAVITY = 9.8
```

---

## Best Practices for Variables
1. Use descriptive names (`age` instead of `a`).
2. Follow snake_case for variable names (`user_name`).
3. Avoid using single-character names except for loop counters.
4. Use constants for values that do not change.
5. Avoid overwriting built-in names (e.g., `list`, `str`).

---

## Common Interview Questions
1. **What is the difference between mutable and immutable variables?**
   - Mutable: Can be changed after creation (e.g., `list`, `dict`).
   - Immutable: Cannot be changed after creation (e.g., `int`, `str`, `tuple`).

2. **How does Python handle variable memory management?**
   - Python uses reference counting and garbage collection to manage memory.

3. **What is the difference between `is` and `==`?**
   - `is`: Checks if two variables point to the same object.
   - `==`: Checks if two variables have the same value.

4. **What are global and nonlocal keywords?**
   - `global`: Used to modify a global variable inside a function.
   - `nonlocal`: Used to modify a variable in the nearest enclosing scope.

---

## Example Code
```python
# Global and Local Variables
x = 50

def modify_variable():
    global x
    x = 100
    print("Inside function:", x)

modify_variable()
print("Outside function:", x)

# Mutable vs Immutable
nums = [1, 2, 3]  # Mutable
nums.append(4)
print(nums)

name = "Alice"  # Immutable
name = name + " Smith"
print(name)
```
