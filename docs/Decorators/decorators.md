# Decorators in Python

## Overview
Decorators are a powerful feature in Python that allow you to modify the behavior of functions or classes. They are essentially functions that wrap other functions.

## Basic Concept

A decorator is a callable that takes a function as input and returns a new function with added functionality.

```python
def my_decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

# Calling the decorated function
say_hello()
# Output:
# Before function call
# Hello!
# After function call
```

## Function Decorators

### Basic Decorator Pattern

```python
def decorator_function(original_function):
    def wrapper_function():
        # Code before
        print(f"Wrapper executed before {original_function.__name__}")
        result = original_function()
        # Code after
        print(f"Wrapper executed after {original_function.__name__}")
        return result
    return wrapper_function

# Using @ syntax (preferred)
@decorator_function
def display():
    print("Display function ran")

# Equivalent to: display = decorator_function(display)

display()
```

### Decorators with Arguments

```python
def decorator_with_args(func):
    def wrapper(*args, **kwargs):
        print(f"Arguments: {args}, {kwargs}")
        result = func(*args, **kwargs)
        return result
    return wrapper

@decorator_with_args
def add(a, b):
    return a + b

@decorator_with_args
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(add(5, 3))  # Output: Arguments: (5, 3), {}
print(greet("Alice", greeting="Hi"))  # Arguments: ('Alice',), {'greeting': 'Hi'}
```

### Preserving Function Metadata

```python
from functools import wraps

def my_decorator(func):
    @wraps(func)  # Preserves original function's metadata
    def wrapper(*args, **kwargs):
        """Wrapper function"""
        print("Decorating...")
        return func(*args, **kwargs)
    return wrapper

@my_decorator
def my_function():
    """Original function"""
    pass

print(my_function.__name__)  # Output: my_function (not wrapper)
print(my_function.__doc__)   # Output: Original function
```

## Common Use Cases

### 1. Timing Functions

```python
import time
from functools import wraps

def timer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
    print("Function complete")

slow_function()
# Output:
# Function complete
# slow_function took 1.0001 seconds
```

### 2. Logging

```python
def log_function_call(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__} with args={args}, kwargs={kwargs}")
        result = func(*args, **kwargs)
        print(f"{func.__name__} returned {result}")
        return result
    return wrapper

@log_function_call
def multiply(x, y):
    return x * y

multiply(3, 4)
# Output:
# Calling multiply with args=(3, 4), kwargs={}
# multiply returned 12
```

### 3. Authentication/Authorization

```python
def require_authentication(func):
    @wraps(func)
    def wrapper(user, *args, **kwargs):
        if not user.get('authenticated'):
            raise PermissionError("User must be authenticated")
        return func(user, *args, **kwargs)
    return wrapper

@require_authentication
def view_profile(user):
    return f"Profile for {user['name']}"

# Usage
authenticated_user = {'name': 'Alice', 'authenticated': True}
guest_user = {'name': 'Guest', 'authenticated': False}

print(view_profile(authenticated_user))  # Works
# print(view_profile(guest_user))  # Raises PermissionError
```

### 4. Caching/Memoization

```python
def memoize(func):
    cache = {}
    @wraps(func)
    def wrapper(*args):
        if args not in cache:
            cache[args] = func(*args)
        return cache[args]
    return wrapper

@memoize
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(100))  # Fast due to caching
```

## Decorators with Parameters

```python
def repeat(times):
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(times=3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
# Output:
# Hello, Alice!
# Hello, Alice!
# Hello, Alice!
```

## Class Decorators

```python
def add_method(cls):
    def new_method(self):
        return "Added method"
    cls.new_method = new_method
    return cls

@add_method
class MyClass:
    def original_method(self):
        return "Original"

obj = MyClass()
print(obj.original_method())  # Output: Original
print(obj.new_method())  # Output: Added method
```

## Built-in Decorators

### @property

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def radius(self):
        return self._radius
    
    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius cannot be negative")
        self._radius = value
    
    @property
    def area(self):
        return 3.14159 * self._radius ** 2

circle = Circle(5)
print(circle.radius)  # 5
print(circle.area)  # 78.53975
circle.radius = 10  # Using setter
```

### @staticmethod and @classmethod

```python
class MyClass:
    class_variable = "Class level"
    
    def instance_method(self):
        return f"Instance method, {self.class_variable}"
    
    @classmethod
    def class_method(cls):
        return f"Class method, {cls.class_variable}"
    
    @staticmethod
    def static_method():
        return "Static method, no access to class or instance"

print(MyClass.class_method())  # Class method, Class level
print(MyClass.static_method())  # Static method
```

## Chaining Decorators

```python
def bold(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return f"<b>{func(*args, **kwargs)}</b>"
    return wrapper

def italic(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return f"<i>{func(*args, **kwargs)}</i>"
    return wrapper

@bold
@italic
def greet(name):
    return f"Hello, {name}"

print(greet("Alice"))  # Output: <b><i>Hello, Alice</i></b>
# Applied bottom to top: italic first, then bold
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is a decorator?**
a) A function that modifies another function  
b) A class that inherits from another  
c) A variable that stores data  
d) A loop structure

**2. Which symbol is used to apply a decorator?**
a) `#`  
b) `@`  
c) `$`  
d) `&`

**3. What does `@wraps` do?**
a) Wraps a gift  
b) Preserves function metadata  
c) Creates a loop  
d) Handles exceptions

**4. Can you stack multiple decorators?**
a) Yes  
b) No  
c) Only in Python 3  
d) Only with classes

**5. What is `@property` used for?**
a) Creating static methods  
b) Creating getter/setter methods  
c) Decorating classes  
d) Error handling

---

## Coding Exercises

**Exercise 1: Debug Decorator**
Create a decorator that prints the function name, arguments, and return value.

**Exercise 2: Retry Decorator**
Write a decorator that retries a function up to 3 times if it raises an exception.

**Exercise 3: Rate Limiter**
Create a decorator that limits how often a function can be called (e.g., once per second).

**Exercise 4: Validation Decorator**
Write a decorator that validates function arguments are positive numbers.

**Exercise 5: Count Calls**
Create a decorator that counts how many times a function has been called.

---

## Answers

### Multiple Choice Answers
1. **a** - Decorator modifies/wraps another function
2. **b** - `@` symbol applies decorators
3. **b** - `@wraps` preserves original function metadata
4. **a** - Multiple decorators can be stacked
5. **b** - `@property` creates getter/setter methods

### Coding Exercise Solutions

**Solution 1:**
```python
from functools import wraps

def debug(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        print(f"Arguments: {args}, {kwargs}")
        result = func(*args, **kwargs)
        print(f"Return value: {result}")
        return result
    return wrapper

@debug
def add(a, b):
    return a + b

add(5, 3)
# Output:
# Calling add
# Arguments: (5, 3), {}
# Return value: 8
```

**Solution 2:**
```python
from functools import wraps
import time

def retry(max_attempts=3, delay=1):
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            attempts = 0
            while attempts < max_attempts:
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    attempts += 1
                    print(f"Attempt {attempts} failed: {e}")
                    if attempts >= max_attempts:
                        raise
                    time.sleep(delay)
        return wrapper
    return decorator

@retry(max_attempts=3, delay=0.5)
def unreliable_function():
    import random
    if random.random() < 0.7:
        raise ValueError("Random failure")
    return "Success!"

print(unreliable_function())
```

**Solution 3:**
```python
import time
from functools import wraps

def rate_limit(min_interval):
    def decorator(func):
        last_called = [0]  # Mutable object to store state
        
        @wraps(func)
        def wrapper(*args, **kwargs):
            elapsed = time.time() - last_called[0]
            if elapsed < min_interval:
                time.sleep(min_interval - elapsed)
            last_called[0] = time.time()
            return func(*args, **kwargs)
        return wrapper
    return decorator

@rate_limit(min_interval=1.0)
def print_message(msg):
    print(f"{time.time()}: {msg}")

# These calls will be at least 1 second apart
print_message("First")
print_message("Second")
print_message("Third")
```

**Solution 4:**
```python
from functools import wraps

def validate_positive(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        for arg in args:
            if isinstance(arg, (int, float)) and arg <= 0:
                raise ValueError(f"All arguments must be positive, got {arg}")
        for value in kwargs.values():
            if isinstance(value, (int, float)) and value <= 0:
                raise ValueError(f"All arguments must be positive, got {value}")
        return func(*args, **kwargs)
    return wrapper

@validate_positive
def calculate_area(width, height):
    return width * height

print(calculate_area(5, 10))  # Output: 50
# print(calculate_area(-5, 10))  # Raises ValueError
```

**Solution 5:**
```python
from functools import wraps

def count_calls(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        wrapper.calls += 1
        print(f"{func.__name__} has been called {wrapper.calls} times")
        return func(*args, **kwargs)
    wrapper.calls = 0
    return wrapper

@count_calls
def say_hello():
    print("Hello!")

say_hello()  # say_hello has been called 1 times
say_hello()  # say_hello has been called 2 times
say_hello()  # say_hello has been called 3 times
```
