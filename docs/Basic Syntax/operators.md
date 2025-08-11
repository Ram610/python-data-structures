# Operators in Python

Operators are special symbols or keywords in Python that perform operations on variables and values. They are the building blocks of any programming language and are categorized based on their functionality.

---

## 1. Arithmetic Operators
Arithmetic operators are used to perform mathematical operations.

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `+`      | Addition          | `a + b`         |
| `-`      | Subtraction       | `a - b`         |
| `*`      | Multiplication    | `a * b`         |
| `/`      | Division          | `a / b`         |
| `%`      | Modulus           | `a % b`         |
| `**`     | Exponentiation    | `a ** b`        |
| `//`     | Floor Division    | `a // b`        |

---

## 2. Comparison Operators
Comparison operators compare two values and return a Boolean result.

| Operator | Description               | Example          |
|----------|---------------------------|------------------|
| `==`     | Equal to                  | `a == b`         |
| `!=`     | Not equal to              | `a != b`         |
| `>`      | Greater than              | `a > b`          |
| `<`      | Less than                 | `a < b`          |
| `>=`     | Greater than or equal to  | `a >= b`         |
| `<=`     | Less than or equal to     | `a <= b`         |

---

## 3. Logical Operators
Logical operators are used to combine conditional statements.

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `and`    | Logical AND       | `a and b`        |
| `or`     | Logical OR        | `a or b`         |
| `not`    | Logical NOT       | `not a`          |

---

## 4. Bitwise Operators
Bitwise operators perform operations on binary numbers.

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `&`      | AND               | `a & b`          |
| `|`      | OR                | `a | b`          |
| `^`      | XOR               | `a ^ b`          |
| `~`      | NOT               | `~a`             |
| `<<`     | Left Shift        | `a << b`         |
| `>>`     | Right Shift       | `a >> b`         |

---

## 5. Assignment Operators
Assignment operators are used to assign values to variables.

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `=`      | Assign            | `a = b`          |
| `+=`     | Add and assign     | `a += b`         |
| `-=`     | Subtract and assign| `a -= b`         |
| `*=`     | Multiply and assign| `a *= b`         |
| `/=`     | Divide and assign  | `a /= b`         |
| `%=`     | Modulus and assign | `a %= b`         |
| `**=`    | Exponent and assign| `a **= b`        |
| `//=`    | Floor divide and assign | `a //= b`  |

---

## 6. Membership Operators
Membership operators test for membership in a sequence (e.g., strings, lists).

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `in`     | True if value is found in sequence | `a in b` |
| `not in` | True if value is not found in sequence | `a not in b` |

---

## 7. Identity Operators
Identity operators compare the memory location of two objects.

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `is`     | True if objects are identical | `a is b` |
| `is not` | True if objects are not identical | `a is not b` |

---

## 8. Special Operators
### a. Ternary Operator
The ternary operator is a shorthand for an `if-else` statement.
```python
x = a if condition else b
```

### b. Operator Precedence
Operator precedence determines the order in which operations are performed.
| Precedence Level | Operators                     |
|------------------|-------------------------------|
| Highest          | `**`                          |
|                  | `*, /, //, %`                 |
|                  | `+, -`                        |
| Lowest           | `and, or, not`               |

---

## 9. Practical Examples
### Example 1: Arithmetic Operators
```python
a = 10
b = 3
print(a + b)  # Output: 13
print(a ** b) # Output: 1000
```

### Example 2: Logical Operators
```python
x = True
y = False
print(x and y)  # Output: False
print(x or y)   # Output: True
```

### Example 3: Membership Operators
```python
my_list = [1, 2, 3]
print(2 in my_list)  # Output: True
print(4 not in my_list)  # Output: True
```

---

This comprehensive guide covers all types of operators in Python, their usage, and practical examples to help you prepare for interviews effectively.

## 10. Interview Questions and Answers on Python Operators

### Q1: What is the difference between `is` and `==` in Python?
**Answer**:  
- `is` checks if two variables refer to the same object in memory.  
- `==` checks if the values of two variables are equal.  

Example:  
```python
a = [1, 2, 3]
b = [1, 2, 3]
print(a == b)  # Output: True (values are equal)
print(a is b)  # Output: False (different memory locations)
```

---

### Q2: What is the difference between `/` and `//` operators?
**Answer**:  
- `/` performs regular division and returns a float.  
- `//` performs floor division and returns the largest integer less than or equal to the result.  

Example:  
```python
print(10 / 3)   # Output: 3.3333333333333335
print(10 // 3)  # Output: 3
```

---

### Q3: How does the `not` operator work in Python?
**Answer**:  
The `not` operator inverts the Boolean value of an expression.  
Example:  
```python
x = True
print(not x)  # Output: False
```

---

### Q4: Can you use logical operators with non-Boolean values?
**Answer**:  
Yes, logical operators like `and`, `or`, and `not` can be used with non-Boolean values. They return one of the operands based on truthiness.  
Example:  
```python
print(0 and 5)  # Output: 0 (first falsy value)
print(3 or 0)   # Output: 3 (first truthy value)
```

---

### Q5: What is operator precedence, and why is it important?
**Answer**:  
Operator precedence determines the order in which operators are evaluated in an expression. It is important to avoid unexpected results.  
Example:  
```python
result = 10 + 2 * 3  # Multiplication (*) has higher precedence than addition (+)
print(result)  # Output: 16
```

---

### Q6: What is the difference between `a += b` and `a = a + b`?
**Answer**:  
Both perform addition and assign the result to `a`. However, `a += b` may modify the object in place if it is mutable (e.g., lists).  
Example:  
```python
a = [1, 2]
b = [3, 4]
a += b  # Modifies the list in place
print(a)  # Output: [1, 2, 3, 4]
```

---

### Q7: How do bitwise operators work in Python?
**Answer**:  
Bitwise operators perform operations on the binary representation of integers.  
Example:  
```python
a = 5  # Binary: 0101
b = 3  # Binary: 0011
print(a & b)  # Output: 1 (Binary: 0001)
print(a | b)  # Output: 7 (Binary: 0111)
```

---

### Q8: What is the ternary operator in Python, and how is it used?
**Answer**:  
The ternary operator is a shorthand for an `if-else` statement.  
Syntax: `x = a if condition else b`  
Example:  
```python
age = 18
status = "Adult" if age >= 18 else "Minor"
print(status)  # Output: Adult
```

---

### Q9: How can you check if a value exists in a list using operators?
**Answer**:  
You can use the `in` operator to check for membership.  
Example:  
```python
my_list = [1, 2, 3]
print(2 in my_list)  # Output: True
print(4 not in my_list)  # Output: True
```

---

### Q10: What is the output of the following code?
```python
a = 10
b = 20
print(a < b and b > 15)
print(a > b or b == 20)
print(not (a == 10))
```
**Answer**:  
- `a < b and b > 15` → `True` (both conditions are true)  
- `a > b or b == 20` → `True` (second condition is true)  
- `not (a == 10)` → `False` (negation of `True`)  

---

These questions cover fundamental concepts and practical scenarios, helping you prepare for Python interviews effectively.