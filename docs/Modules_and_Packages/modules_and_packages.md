# Modules and Packages in Python

## Overview
Modules and packages allow you to organize Python code into reusable components. They help keep code modular, maintainable, and shareable.

## Modules

### What is a Module?
A module is a Python file (.py) containing Python definitions, functions, classes, and variables.

### Creating a Module

```python
# File: mymodule.py
"""This is my custom module"""

def greet(name):
    """Greet someone"""
    return f"Hello, {name}!"

def add(a, b):
    """Add two numbers"""
    return a + b

PI = 3.14159
```

### Importing Modules

```python
# Import entire module
import mymodule
print(mymodule.greet("Alice"))
print(mymodule.PI)

# Import specific items
from mymodule import greet, add
print(greet("Bob"))
print(add(5, 3))

# Import with alias
import mymodule as mm
print(mm.greet("Charlie"))

# Import all (not recommended)
from mymodule import *
print(greet("David"))
```

### Built-in Modules

```python
# Math module
import math
print(math.sqrt(16))  # 4.0
print(math.pi)  # 3.141592653589793

# Random module
import random
print(random.randint(1, 10))
print(random.choice(['apple', 'banana', 'cherry']))

# Datetime module
import datetime
now = datetime.datetime.now()
print(now)

# OS module
import os
print(os.getcwd())  # Current directory
print(os.listdir('.'))  # List files

# Sys module
import sys
print(sys.version)  # Python version
print(sys.path)  # Module search paths
```

### Module Search Path

```python
import sys

# Python searches for modules in these locations (in order):
# 1. Current directory
# 2. PYTHONPATH environment variable
# 3. Installation-dependent default paths

print(sys.path)

# Add custom path
sys.path.append('/path/to/custom/modules')
```

### The `__name__` Variable

```python
# File: mymodule.py
def main():
    print("Running as main program")

if __name__ == "__main__":
    # This code only runs when file is executed directly
    main()
else:
    # This runs when imported as module
    print("Module imported")
```

### Module Attributes

```python
import mymodule

# Module name
print(mymodule.__name__)

# Module documentation
print(mymodule.__doc__)

# Module file location
print(mymodule.__file__)

# List all attributes
print(dir(mymodule))
```

## Packages

### What is a Package?
A package is a directory containing Python modules and a special `__init__.py` file.

### Creating a Package

```
mypackage/
    __init__.py
    module1.py
    module2.py
    subpackage/
        __init__.py
        module3.py
```

```python
# File: mypackage/__init__.py
"""My custom package"""
__version__ = "1.0.0"

# File: mypackage/module1.py
def func1():
    return "Function from module1"

# File: mypackage/module2.py
def func2():
    return "Function from module2"

# File: mypackage/subpackage/module3.py
def func3():
    return "Function from subpackage module3"
```

### Importing from Packages

```python
# Import package
import mypackage
print(mypackage.__version__)

# Import module from package
from mypackage import module1
print(module1.func1())

# Import specific function
from mypackage.module2 import func2
print(func2())

# Import from subpackage
from mypackage.subpackage.module3 import func3
print(func3())

# Import with alias
from mypackage import module1 as m1
print(m1.func1())
```

### `__init__.py` File

```python
# File: mypackage/__init__.py

# Make functions available at package level
from .module1 import func1
from .module2 import func2

# Define what's exported with "from package import *"
__all__ = ['func1', 'func2']

# Package initialization code
print("Package initialized")

# Package metadata
__version__ = "1.0.0"
__author__ = "Your Name"
```

### Relative Imports

```python
# Within a package, use relative imports

# File: mypackage/module1.py
from . import module2  # Import sibling module
from .module2 import func2  # Import from sibling
from ..otherpackage import something  # Import from parent
from .subpackage import module3  # Import from subpackage
```

## Package Management with pip

### Installing Packages

```bash
# Install package
pip install requests

# Install specific version
pip install requests==2.28.0

# Install minimum version
pip install requests>=2.28.0

# Install from requirements file
pip install -r requirements.txt

# Install in development mode
pip install -e .
```

### Managing Packages

```bash
# List installed packages
pip list

# Show package information
pip show requests

# Search for packages
pip search numpy

# Upgrade package
pip install --upgrade requests

# Uninstall package
pip uninstall requests

# Freeze installed packages
pip freeze > requirements.txt
```

### requirements.txt

```text
# File: requirements.txt
requests==2.28.0
numpy>=1.21.0
pandas~=1.3.0  # Compatible release
flask  # Latest version
```

```bash
# Install all dependencies
pip install -r requirements.txt
```

## Creating Distributable Packages

### setup.py

```python
# File: setup.py
from setuptools import setup, find_packages

setup(
    name="mypackage",
    version="1.0.0",
    author="Your Name",
    author_email="your.email@example.com",
    description="A short description",
    long_description=open("README.md").read(),
    long_description_content_type="text/markdown",
    url="https://github.com/yourusername/mypackage",
    packages=find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires=">=3.6",
    install_requires=[
        "requests>=2.28.0",
        "numpy>=1.21.0",
    ],
)
```

### Building and Distributing

```bash
# Install build tools
pip install build twine

# Build package
python -m build

# Upload to PyPI
python -m twine upload dist/*

# Install locally
pip install -e .
```

## Best Practices

### 1. Module Organization

```python
# Good structure
myproject/
    __init__.py
    main.py
    utils/
        __init__.py
        helpers.py
        validators.py
    models/
        __init__.py
        user.py
        product.py
    tests/
        __init__.py
        test_utils.py
        test_models.py
```

### 2. Import Conventions

```python
# Standard library imports first
import os
import sys

# Third-party imports
import numpy as np
import pandas as pd

# Local imports
from myproject.utils import helpers
from myproject.models import User
```

### 3. Avoid Circular Imports

```python
# Bad: module1 imports module2, module2 imports module1

# Good: Use local imports or restructure
def function_using_module2():
    from . import module2
    return module2.some_function()
```

---

## Practice Questions

### Multiple Choice Questions

**1. What file makes a directory a package?**
a) `__main__.py`  
b) `__init__.py`  
c) `__package__.py`  
d) `package.py`

**2. What does `import math as m` do?**
a) Imports math module with alias m  
b) Imports m from math  
c) Creates math variable  
d) Error

**3. Which command installs a package?**
a) `python install package`  
b) `pip install package`  
c) `install package`  
d) `package install`

**4. What is `requirements.txt` used for?**
a) List Python requirements  
b) List package dependencies  
c) Configure Python  
d) Document code

**5. When does `if __name__ == "__main__":` execute?**
a) Always  
b) When imported  
c) When run directly  
d) Never

**6. What does `from module import *` do?**
a) Imports everything from module  
b) Imports nothing  
c) Creates error  
d) Imports __all__

**7. How to import from parent package?**
a) `from .. import module`  
b) `from parent import module`  
c) `import ../module`  
d) `parent.module`

**8. What is pip?**
a) Python package manager  
b) Python interpreter  
c) Python IDE  
d) Python compiler

---

### Coding Exercises

**Exercise 1: Create a Module**
Create a module `calculator.py` with functions for add, subtract, multiply, and divide.

**Exercise 2: Package Structure**
Create a package `geometry` with modules for calculating areas of different shapes (circle, rectangle, triangle).

**Exercise 3: Import Practice**
Write code that imports the `datetime` module and displays the current date and time in a formatted way.

**Exercise 4: Custom Package**
Create a package `text_utils` with functions for text manipulation (uppercase, lowercase, reverse, count words).

**Exercise 5: Requirements File**
Create a `requirements.txt` file for a project that needs requests, pandas, and matplotlib.

---

## Answers

### Multiple Choice Answers
1. **b** - `__init__.py` makes directory a package
2. **a** - Creates alias m for math module
3. **b** - `pip install` installs packages
4. **b** - Lists package dependencies
5. **c** - Executes when script run directly
6. **a** - Imports all public names (or __all__)
7. **a** - Use `..` for parent package
8. **a** - pip is Python's package manager

### Coding Exercise Solutions

**Solution 1:**
```python
# File: calculator.py
"""Simple calculator module"""

def add(a, b):
    """Add two numbers"""
    return a + b

def subtract(a, b):
    """Subtract b from a"""
    return a - b

def multiply(a, b):
    """Multiply two numbers"""
    return a * b

def divide(a, b):
    """Divide a by b"""
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b

# Test code
if __name__ == "__main__":
    print(f"10 + 5 = {add(10, 5)}")
    print(f"10 - 5 = {subtract(10, 5)}")
    print(f"10 * 5 = {multiply(10, 5)}")
    print(f"10 / 5 = {divide(10, 5)}")
```

**Solution 2:**
```python
# Package structure:
# geometry/
#     __init__.py
#     circle.py
#     rectangle.py
#     triangle.py

# File: geometry/__init__.py
"""Geometry package for calculating areas"""
from .circle import area as circle_area
from .rectangle import area as rectangle_area
from .triangle import area as triangle_area

__all__ = ['circle_area', 'rectangle_area', 'triangle_area']

# File: geometry/circle.py
import math

def area(radius):
    """Calculate area of circle"""
    return math.pi * radius ** 2

# File: geometry/rectangle.py
def area(length, width):
    """Calculate area of rectangle"""
    return length * width

# File: geometry/triangle.py
def area(base, height):
    """Calculate area of triangle"""
    return 0.5 * base * height

# Usage:
from geometry import circle_area, rectangle_area, triangle_area

print(circle_area(5))
print(rectangle_area(4, 6))
print(triangle_area(3, 8))
```

**Solution 3:**
```python
import datetime

# Get current date and time
now = datetime.datetime.now()

# Format 1: Default
print(f"Current datetime: {now}")

# Format 2: Custom format
formatted = now.strftime("%Y-%m-%d %H:%M:%S")
print(f"Formatted: {formatted}")

# Format 3: Different style
readable = now.strftime("%B %d, %Y at %I:%M %p")
print(f"Readable: {readable}")

# Just date
print(f"Date: {now.date()}")

# Just time
print(f"Time: {now.time()}")
```

**Solution 4:**
```python
# Package structure:
# text_utils/
#     __init__.py
#     case_converter.py
#     text_analyzer.py

# File: text_utils/__init__.py
"""Text utility package"""
from .case_converter import to_uppercase, to_lowercase
from .text_analyzer import reverse_text, count_words

__all__ = ['to_uppercase', 'to_lowercase', 'reverse_text', 'count_words']

# File: text_utils/case_converter.py
def to_uppercase(text):
    """Convert text to uppercase"""
    return text.upper()

def to_lowercase(text):
    """Convert text to lowercase"""
    return text.lower()

# File: text_utils/text_analyzer.py
def reverse_text(text):
    """Reverse the text"""
    return text[::-1]

def count_words(text):
    """Count words in text"""
    return len(text.split())

# Usage:
from text_utils import to_uppercase, reverse_text, count_words

text = "Hello World"
print(to_uppercase(text))  # HELLO WORLD
print(reverse_text(text))  # dlroW olleH
print(count_words(text))  # 2
```

**Solution 5:**
```text
# File: requirements.txt
# HTTP library for making requests
requests>=2.28.0

# Data analysis library
pandas>=1.3.0,<2.0.0

# Plotting library
matplotlib>=3.5.0

# Optional: Specify exact versions for reproducibility
# requests==2.31.0
# pandas==1.5.3
# matplotlib==3.7.1

# Can also include extras
# requests[security]>=2.28.0

# Development dependencies (separate file: requirements-dev.txt)
# pytest>=7.0.0
# black>=22.0.0
# flake8>=4.0.0
```

### Additional Example: Complete Project Structure

```python
# Project: my_app
# Structure:
my_app/
    setup.py
    requirements.txt
    README.md
    my_app/
        __init__.py
        main.py
        config.py
        utils/
            __init__.py
            helpers.py
        models/
            __init__.py
            user.py
    tests/
        __init__.py
        test_utils.py
    docs/
        index.md

# File: setup.py
from setuptools import setup, find_packages

setup(
    name="my_app",
    version="0.1.0",
    packages=find_packages(),
    install_requires=[
        "requests>=2.28.0",
    ],
)

# File: my_app/__init__.py
"""My Application Package"""
__version__ = "0.1.0"

# File: my_app/main.py
from my_app.utils.helpers import process_data
from my_app.models.user import User

def main():
    user = User("Alice")
    data = process_data(user.get_info())
    print(data)

if __name__ == "__main__":
    main()
```
