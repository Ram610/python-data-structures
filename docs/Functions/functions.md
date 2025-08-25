# Functions in Python: Complete Guide

## 1. Introduction to Functions
- **Definition**: A function is a reusable block of code that performs a specific task.
- **Syntax**:
    ```python
    def function_name(parameters):
            """docstring"""
            statement(s)
            return value
    ```
- **Example**:
    ```python
    def greet(name):
            print(f"Hello, {name}!")
    greet("Alice")
    ```

## 2. Types of Functions
- **Built-in Functions**: Provided by Python (e.g., `len()`, `print()`, `sum()`).
- **User-defined Functions**: Created by the user using `def`.
- **Lambda Functions**: Anonymous, single-expression functions.
    ```python
    add = lambda x, y: x + y
    print(add(2, 3))  # Output: 5
    ```

## 3. Function Arguments
- **Positional Arguments**: Matched by position.
- **Keyword Arguments**: Matched by parameter name.
    ```python
    def func(a, b):
            print(a, b)
    func(1, b=2)
    ```
- **Default Arguments**: Provide default values.
    ```python
    def power(base, exp=2):
            return base ** exp
    print(power(3))  # Output: 9
    ```
- **Variable-length Arguments**:
    - `*args`: Tuple of positional arguments.
        ```python
        def add(*args):
                return sum(args)
        print(add(1, 2, 3))  # Output: 6
        ```
    - `**kwargs`: Dictionary of keyword arguments.
        ```python
        def print_info(**kwargs):
                for key, value in kwargs.items():
                        print(f"{key}: {value}")
        print_info(name="Alice", age=25)
        ```

## 4. Return Statement
- **Returning Values**: Use `return` to send a result back.
- **Multiple Returns**: Return multiple values as tuple.
    ```python
    def stats(numbers):
            return min(numbers), max(numbers)
    mn, mx = stats([1, 2, 3])
    ```

## 5. Scope and Lifetime of Variables
- **Local Scope**: Variables defined inside a function.
- **Global Scope**: Variables defined outside all functions.
- **`global` Keyword**: Modify global variables inside a function.
- **`nonlocal` Keyword**: Modify variables in the nearest enclosing scope (not global).
    ```python
    def outer():
            x = "local"
            def inner():
                    nonlocal x
                    x = "nonlocal"
            inner()
            print(x)  # Output: nonlocal
    ```

## 6. Docstrings and Annotations
- **Docstrings**: Document your functions.
    ```python
    def add(a, b):
            """Returns the sum of a and b."""
            return a + b
    ```
- **Annotations**: Type hints for parameters and return values.
    ```python
    def add(a: int, b: int) -> int:
            return a + b
    ```

## 7. First-Class Functions & Higher-Order Functions
- **First-Class Functions**: Functions can be assigned to variables, passed as arguments, and returned.
- **Higher-Order Functions**: Functions that take other functions as arguments or return them.
    ```python
    def apply(func, value):
            return func(value)
    print(apply(abs, -5))  # Output: 5
    ```

## 8. Closures
- **Definition**: A closure is a function object that remembers values in enclosing scopes.
    ```python
    def make_multiplier(x):
            def multiplier(n):
                    return x * n
            return multiplier
    times3 = make_multiplier(3)
    print(times3(10))  # Output: 30
    ```

## 9. Decorators
- **Definition**: Functions that modify the behavior of other functions.
    ```python
    def my_decorator(func):
            def wrapper():
                    print("Before")
                    func()
                    print("After")
            return wrapper

    @my_decorator
    def say_hello():
            print("Hello!")
    say_hello()
    ```

## 10. Recursion
- **Definition**: A function calling itself.
- **Example**:
    ```python
    def factorial(n):
            if n == 0:
                    return 1
            else:
                    return n * factorial(n-1)
    print(factorial(5))  # Output: 120
    ```

## 11. Generators and `yield`
- **Generators**: Functions that yield values one at a time.
    ```python
    def countdown(n):
            while n > 0:
                    yield n
                    n -= 1
    for i in countdown(3):
            print(i)
    ```

## 12. Best Practices
- Use descriptive names.
- Keep functions small and focused.
- Use docstrings and type hints.
- Avoid using global variables.
- Handle exceptions gracefully.

---

# Interview Questions

### Conceptual
1. What is the difference between a function and a method in Python?
2. Explain the difference between `*args` and `**kwargs`.
3. What is a closure? Give an example.
4. How does Python handle default mutable arguments?
5. What are decorators and how are they used?
6. What is the scope of a variable? Explain `global` and `nonlocal`.
7. How do you document a function in Python?
8. What is recursion? What are its pros and cons?
9. How do you return multiple values from a function?
10. What are lambda functions and where would you use them?

### Coding
1. Write a function to check if a number is prime.
2. Implement a decorator that logs the execution time of a function.
3. Write a recursive function to compute the nth Fibonacci number.
4. Write a function that accepts any number of positional and keyword arguments and prints them.
5. Write a function that returns another function (closure).

---

# Multiple Choice Questions

1. What is the output of the following code?
     ```python
     def foo(x, y=2):
             return x * y
     print(foo(3))
     ```
     - a) 2
     - b) 3
     - c) 6
     - d) Error

2. Which of the following is used to define an anonymous function in Python?
     - a) def
     - b) lambda
     - c) func
     - d) anonymous

3. What will be the output?
     ```python
     def func(a, b, c=5):
             print(a, b, c)
     func(1, 2)
     ```
     - a) 1 2 5
     - b) 1 5 2
     - c) 2 1 5
     - d) Error

4. What does the `yield` keyword do?
     - a) Returns a value and exits the function
     - b) Returns a generator
     - c) Raises an exception
     - d) None of the above

5. Which statement is true about functions in Python?
     - a) Functions cannot return multiple values
     - b) Functions can be assigned to variables
     - c) Functions cannot be passed as arguments
     - d) Functions must always have a return statement

---

**Answers:**  
1. c  
2. b  
3. a  
4. b  
5. b  
