# Exception Handling in Python

## Overview
Exception handling allows you to gracefully handle errors and unexpected situations in your code without crashing the program.

## Basic Syntax

```python
try:
    # Code that might raise an exception
    result = 10 / 0
except:
    # Code to handle the exception
    print("An error occurred")
```

## Common Exceptions

| Exception | Description |
|-----------|-------------|
| `ValueError` | Invalid value for operation |
| `TypeError` | Wrong type used |
| `KeyError` | Dictionary key not found |
| `IndexError` | List index out of range |
| `FileNotFoundError` | File doesn't exist |
| `ZeroDivisionError` | Division by zero |
| `AttributeError` | Invalid attribute reference |
| `ImportError` | Import fails |

## Try-Except Blocks

```python
# Catch specific exception
try:
    number = int(input("Enter a number: "))
    result = 100 / number
except ZeroDivisionError:
    print("Cannot divide by zero!")
except ValueError:
    print("Please enter a valid number!")

# Catch multiple exceptions
try:
    # some code
    pass
except (ValueError, TypeError) as e:
    print(f"Error: {e}")

# Catch all exceptions (not recommended)
try:
    # some code
    pass
except Exception as e:
    print(f"Unexpected error: {e}")
```

## Try-Except-Else

```python
try:
    file = open('data.txt', 'r')
except FileNotFoundError:
    print("File not found")
else:
    # Executed if no exception occurred
    content = file.read()
    print(content)
    file.close()
```

## Try-Except-Finally

```python
try:
    file = open('data.txt', 'r')
    content = file.read()
except FileNotFoundError:
    print("File not found")
finally:
    # Always executed, even if exception occurs
    print("Cleanup complete")
    # Close file if it was opened
    try:
        file.close()
    except:
        pass
```

## Raising Exceptions

```python
def divide(a, b):
    if b == 0:
        raise ValueError("Denominator cannot be zero")
    return a / b

try:
    result = divide(10, 0)
except ValueError as e:
    print(e)

# Re-raise exception
try:
    # some code
    raise ValueError("Something went wrong")
except ValueError:
    print("Handling error")
    raise  # Re-raise the same exception
```

## Custom Exceptions

```python
class InsufficientFundsError(Exception):
    """Raised when account has insufficient funds"""
    pass

class NegativeAmountError(Exception):
    """Raised when amount is negative"""
    def __init__(self, amount):
        self.amount = amount
        super().__init__(f"Amount cannot be negative: {amount}")

# Using custom exceptions
class BankAccount:
    def __init__(self, balance):
        self.balance = balance
    
    def withdraw(self, amount):
        if amount < 0:
            raise NegativeAmountError(amount)
        if amount > self.balance:
            raise InsufficientFundsError("Not enough balance")
        self.balance -= amount
        return self.balance

# Test
account = BankAccount(100)
try:
    account.withdraw(-50)
except NegativeAmountError as e:
    print(e)

try:
    account.withdraw(200)
except InsufficientFundsError as e:
    print(e)
```

## Best Practices

```python
# 1. Be specific with exceptions
try:
    value = int("abc")
except ValueError:  # Good - specific
    print("Invalid integer")

# 2. Don't catch Exception unless necessary
try:
    # code
    pass
except Exception:  # Avoid this
    pass

# 3. Log exceptions
import logging
try:
    # code
    pass
except Exception as e:
    logging.error(f"Error occurred: {e}")

# 4. Use context managers
with open('file.txt', 'r') as f:
    # No need for try-finally
    content = f.read()
```

---

## Practice Questions

### Multiple Choice Questions

**1. Which block always executes?**
a) try  
b) except  
c) else  
d) finally

**2. What exception is raised for division by zero?**
a) ValueError  
b) ZeroDivisionError  
c) ArithmeticError  
d) DivisionError

**3. How to raise an exception?**
a) `throw Exception()`  
b) `raise Exception()`  
c) `error Exception()`  
d) `exception()`

**4. When does the else block execute?**
a) Always  
b) When exception occurs  
c) When no exception occurs  
d) Never

**5. Can you create custom exceptions?**
a) Yes  
b) No  
c) Only in Python 3  
d) Only for built-in types

---

## Answers

### Multiple Choice Answers
1. **d** - finally block always executes
2. **b** - ZeroDivisionError for division by zero
3. **b** - Use `raise` keyword
4. **c** - else executes when no exception occurs
5. **a** - Yes, inherit from Exception class
