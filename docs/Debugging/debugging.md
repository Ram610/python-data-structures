# Debugging in Python

## Print Debugging

### Basic Print Statements
```python
def calculate_average(numbers):
    print(f"Input: {numbers}")
    total = sum(numbers)
    print(f"Total: {total}")
    count = len(numbers)
    print(f"Count: {count}")
    average = total / count
    print(f"Average: {average}")
    return average

result = calculate_average([10, 20, 30])
```

### Using f-strings for Debugging
```python
def process_user(user_id, name):
    print(f"DEBUG: user_id={user_id}, name={name}")
    # Process user...
    return f"Processed {name}"
```

---

## Logging Module

### Basic Logging Setup
```python
import logging

# Configure logging
logging.basicConfig(
    level=logging.DEBUG,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    filename='app.log'
)

# Create logger
logger = logging.getLogger(__name__)

# Logging levels
logger.debug("Debug message")
logger.info("Info message")
logger.warning("Warning message")
logger.error("Error message")
logger.critical("Critical message")
```

### Logging Levels
| Level    | Value | Usage                          |
|----------|-------|--------------------------------|
| DEBUG    | 10    | Detailed information           |
| INFO     | 20    | General information            |
| WARNING  | 30    | Warning messages               |
| ERROR    | 40    | Error messages                 |
| CRITICAL | 50    | Critical errors                |

### Advanced Logging Configuration
```python
import logging

# Create custom logger
logger = logging.getLogger('my_app')
logger.setLevel(logging.DEBUG)

# Create handlers
console_handler = logging.StreamHandler()
file_handler = logging.FileHandler('app.log')

# Set levels for handlers
console_handler.setLevel(logging.WARNING)
file_handler.setLevel(logging.DEBUG)

# Create formatter
formatter = logging.Formatter(
    '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
)

# Add formatter to handlers
console_handler.setFormatter(formatter)
file_handler.setFormatter(formatter)

# Add handlers to logger
logger.addHandler(console_handler)
logger.addHandler(file_handler)

# Use logger
logger.debug("This goes to file only")
logger.warning("This goes to console and file")
```

---

## Python Debugger (pdb)

### Basic pdb Usage
```python
import pdb

def divide_numbers(a, b):
    pdb.set_trace()  # Debugger stops here
    result = a / b
    return result

divide_numbers(10, 2)
```

### Common pdb Commands
| Command | Description                    |
|---------|--------------------------------|
| `l`     | List source code               |
| `n`     | Execute next line              |
| `s`     | Step into function             |
| `c`     | Continue execution             |
| `p var` | Print variable value           |
| `pp var`| Pretty-print variable          |
| `b 10`  | Set breakpoint at line 10      |
| `cl`    | Clear breakpoints              |
| `q`     | Quit debugger                  |

### Breakpoint Function (Python 3.7+)
```python
def calculate_total(items):
    total = 0
    for item in items:
        breakpoint()  # Modern way to set breakpoint
        total += item['price']
    return total

items = [{'name': 'apple', 'price': 1.50}, {'name': 'banana', 'price': 0.75}]
calculate_total(items)
```

### Conditional Breakpoints
```python
import pdb

def process_list(numbers):
    for i, num in enumerate(numbers):
        if num < 0:
            pdb.set_trace()  # Only debug negative numbers
        result = num * 2
        print(result)

process_list([1, 2, -3, 4, -5])
```

---

## Debugging Techniques

### Try-Except with Traceback
```python
import traceback

try:
    result = 10 / 0
except Exception as e:
    print(f"Error occurred: {e}")
    traceback.print_exc()
```

### Assert Statements
```python
def calculate_discount(price, discount_percent):
    assert 0 <= discount_percent <= 100, "Discount must be between 0 and 100"
    assert price > 0, "Price must be positive"
    return price * (1 - discount_percent / 100)

# This will raise AssertionError
calculate_discount(100, 150)
```

### Using warnings Module
```python
import warnings

def deprecated_function():
    warnings.warn("This function is deprecated", DeprecationWarning)
    return "old result"

# Show warnings
deprecated_function()
```

---

## Practice Questions

### Multiple Choice Questions

**1. Which logging level is highest?**
a) ERROR  
b) WARNING  
c) CRITICAL  
d) DEBUG

**2. What command continues execution in pdb?**
a) n  
b) s  
c) c  
d) q

**3. What is the modern way to set breakpoint in Python 3.7+?**
a) pdb.set_trace()  
b) breakpoint()  
c) debug()  
d) stop()

**4. What does 'n' command do in pdb?**
a) Quit debugger  
b) Continue execution  
c) Execute next line  
d) Step into function

**5. Which logging level shows the most detail?**
a) INFO  
b) WARNING  
c) DEBUG  
d) ERROR

---

## Coding Exercises

**Exercise 1:** Create a function that uses logging to track the execution of a calculation.

**Exercise 2:** Write a function that uses assertions to validate input parameters.

**Exercise 3:** Debug the following code using pdb:
```python
def calculate_average(numbers):
    total = sum(numbers)
    count = len(numbers)
    average = total / count
    return average

result = calculate_average([])  # This will cause an error
```

---

## Answers

### MCQ Answers
**1.** c - CRITICAL is the highest level  
**2.** c - 'c' continues execution  
**3.** b - breakpoint() is modern way  
**4.** c - 'n' executes next line  
**5.** c - DEBUG shows most detail

### Exercise Solutions

**Exercise 1:**
```python
import logging

logging.basicConfig(level=logging.DEBUG)
logger = logging.getLogger(__name__)

def calculate_with_logging(a, b):
    logger.debug(f"Starting calculation with a={a}, b={b}")
    result = a + b
    logger.info(f"Result: {result}")
    return result

calculate_with_logging(10, 20)
```

**Exercise 2:**
```python
def validate_age(age):
    assert isinstance(age, int), "Age must be an integer"
    assert 0 <= age <= 150, "Age must be between 0 and 150"
    return f"Age {age} is valid"

print(validate_age(25))
```

**Exercise 3:**
```python
import pdb

def calculate_average(numbers):
    pdb.set_trace()
    if not numbers:
        return 0
    total = sum(numbers)
    count = len(numbers)
    average = total / count
    return average

result = calculate_average([10, 20, 30])
print(result)
```
