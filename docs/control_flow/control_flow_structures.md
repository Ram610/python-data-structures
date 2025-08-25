# Control Flow Structures

## 1. if/else Statements

### Explanation
The `if/else` statement is used to execute code based on a condition. If the condition is `True`, the code inside the `if` block runs; otherwise, the code inside the `else` block runs.

### Syntax
```python
if condition:
    # code to execute if condition is True
else:
    # code to execute if condition is False
```

### Example
```python
age = 18
if age >= 18:
    print("You are an adult.")
else:
    print("You are a minor.")
```

### Using `elif`

The `elif` (short for "else if") statement allows you to check multiple conditions in sequence. If the first `if` condition is `False`, Python checks the `elif` condition(s). If none of the conditions are `True`, the `else` block (if present) runs.

#### Syntax
```python
if condition1:
    # code if condition1 is True
elif condition2:
    # code if condition2 is True
else:
    # code if none of the above conditions are True
```

#### Example
```python
score = 75
if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
else:
    print("Grade: D")
```

### Additional Notes on `if/else` Statements

- **Multiple `elif` blocks:** You can have as many `elif` blocks as needed between `if` and `else`.
- **Omitting `else`:** The `else` block is optional. If omitted, nothing happens when all conditions are `False`.
- **Nested `if` statements:** You can place an `if` statement inside another `if` or `else` block for more complex logic.
- **Truthiness:** Conditions can be any expression that evaluates to `True` or `False`. Non-zero numbers, non-empty strings/lists, etc., are considered `True`.
- **Comparison and logical operators:** Use operators like `==`, `!=`, `<`, `>`, `<=`, `>=`, `and`, `or`, and `not` to build complex conditions.

#### Example with logical operators
```python
age = 20
has_id = True
if age >= 18 and has_id:
    print("Entry allowed")
else:
    print("Entry denied")
```

---

## 2. for Loop

### Explanation
A `for` loop is used to iterate over a sequence (like a list, tuple, or string) and execute a block of code for each item.

### Syntax

#### Iterating over a list
```python
for item in my_list:
    # code to execute for each item
```

#### Iterating with index using `range()`
```python
for i in range(len(my_list)):
    # code to execute using index i
```

#### Iterating over a dictionary (keys)
```python
for key in my_dict:
    # code to execute for each key
```

#### Iterating over dictionary items (key, value pairs)
```python
for key, value in my_dict.items():
    # code to execute for each key-value pair
```

#### Iterating over a string
```python
for char in my_string:
    # code to execute for each character
```

#### Using `enumerate()` for index and value
```python
for index, value in enumerate(my_list):
    # code to execute using index and value
```

### Example
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

---

## 3. while Loop

### Explanation
A `while` loop repeatedly executes a block of code as long as a condition is `True`.

### Syntax
```python
while condition:
    # code to execute while condition is True
```

### Example
```python
count = 0
while count < 5:
    print(count)
    count += 1
```

---

## Interview Questions

1. **What is the difference between `if` and `elif`?**
2. **How does a `for` loop differ from a `while` loop?**
3. **Can you nest `if` statements inside loops? Give an example.**
4. **What happens if the condition in a `while` loop is always `True`?**
5. **How can you break out of a loop prematurely?**

---

## Logical Questions (with Multiple Choice)

1. **What will be the output of the following code?**
    ```python
    x = 10
    if x > 5:
        print("A")
    else:
        print("B")
    ```
    - a) A
    - b) B
    - c) Error
    - d) None

2. **How many times will "Hello" be printed?**
    ```python
    for i in range(3):
        print("Hello")
    ```
    - a) 1
    - b) 2
    - c) 3
    - d) 4

3. **What is the output?**
    ```python
    count = 0
    while count < 2:
        print(count)
        count += 1
    ```
    - a) 0 1
    - b) 1 2
    - c) 0 1 2
    - d) 0

4. **Which statement is used to skip the current iteration in a loop?**
    - a) break
    - b) continue
    - c) pass
    - d) exit

5. **What is the output?**
    ```python
    for i in range(2):
        if i == 1:
            break
        print(i)
    ```
    - a) 0 1
    - b) 1
    - c) 0
    - d) None

---

**Answers:**  
1. a  
2. c  
3. a  
4. b  
5. c  