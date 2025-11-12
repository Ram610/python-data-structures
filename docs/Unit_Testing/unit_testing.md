# Unit Testing in Python

## Overview
Unit testing involves testing individual components of code to ensure they work correctly.

## unittest Framework (Built-in)

### Basic Test Class
```python
import unittest

class TestMathOperations(unittest.TestCase):
    def test_addition(self):
        self.assertEqual(2 + 2, 4)
    
    def test_subtraction(self):
        self.assertEqual(5 - 3, 2)
    
    def test_multiplication(self):
        self.assertEqual(3 * 4, 12)
    
    def test_division(self):
        self.assertEqual(10 / 2, 5)

if __name__ == '__main__':
    unittest.main()
```

### Assert Methods
```python
class TestAssertions(unittest.TestCase):
    def test_equality(self):
        self.assertEqual(1, 1)
        self.assertNotEqual(1, 2)
    
    def test_boolean(self):
        self.assertTrue(True)
        self.assertFalse(False)
    
    def test_membership(self):
        self.assertIn(2, [1, 2, 3])
        self.assertNotIn(4, [1, 2, 3])
    
    def test_exceptions(self):
        with self.assertRaises(ValueError):
            int('abc')
    
    def test_comparison(self):
        self.assertGreater(5, 3)
        self.assertLess(2, 5)
```

### Setup and Teardown
```python
class TestWithSetup(unittest.TestCase):
    def setUp(self):
        """Run before each test"""
        self.data = [1, 2, 3]
    
    def tearDown(self):
        """Run after each test"""
        self.data = None
    
    def test_length(self):
        self.assertEqual(len(self.data), 3)
```

## pytest Framework (Popular)

### Installation
```bash
pip install pytest
```

### Simple Tests
```python
# test_example.py
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
    assert add(-1, 1) == 0
    assert add(0, 0) == 0

def test_add_negative():
    assert add(-2, -3) == -5
```

### Running Tests
```bash
# Run all tests
pytest

# Run specific file
pytest test_example.py

# Run with verbose output
pytest -v

# Run with coverage
pytest --cov=mymodule
```

### Fixtures
```python
import pytest

@pytest.fixture
def sample_data():
    return [1, 2, 3, 4, 5]

def test_sum(sample_data):
    assert sum(sample_data) == 15

def test_length(sample_data):
    assert len(sample_data) == 5
```

### Parametrized Tests
```python
import pytest

@pytest.mark.parametrize("a,b,expected", [
    (2, 3, 5),
    (0, 0, 0),
    (-1, 1, 0),
    (10, -5, 5),
])
def test_add(a, b, expected):
    assert add(a, b) == expected
```

## Testing Best Practices

### 1. Test Organization
```
project/
    src/
        calculator.py
    tests/
        test_calculator.py
        test_utils.py
```

### 2. Test Naming
```python
# Good names
def test_add_positive_numbers():
    pass

def test_divide_by_zero_raises_error():
    pass

# Bad names
def test1():
    pass

def test_func():
    pass
```

### 3. AAA Pattern
```python
def test_calculator_add():
    # Arrange
    calc = Calculator()
    a, b = 5, 3
    
    # Act
    result = calc.add(a, b)
    
    # Assert
    assert result == 8
```

## Mocking

```python
from unittest.mock import Mock, patch

# Mock object
def test_with_mock():
    mock_obj = Mock()
    mock_obj.method.return_value = 42
    
    result = mock_obj.method()
    assert result == 42

# Patch function
@patch('module.function_name')
def test_with_patch(mock_func):
    mock_func.return_value = 'mocked'
    result = module.function_name()
    assert result == 'mocked'
```

## Test Coverage

```bash
# Install coverage
pip install pytest-cov

# Run with coverage
pytest --cov=src --cov-report=html

# View coverage report
# Open htmlcov/index.html
```

---

## Practice Questions

### Multiple Choice Questions

**1. What framework is built into Python?**
a) pytest  
b) unittest  
c) nose  
d) doctest

**2. What does assert do?**
a) Prints message  
b) Checks condition  
c) Raises exception  
d) Returns value

**3. What is setUp() for?**
a) Run before each test  
b) Run after tests  
c) Initialize module  
d) Nothing

**4. How to run pytest?**
a) `python test.py`  
b) `pytest`  
c) `run tests`  
d) `unittest`

**5. What is test coverage?**
a) Number of tests  
b) Percentage of code tested  
c) Test speed  
d) Test results

---

## Answers

**1.** b - unittest is built-in  
**2.** b - assert checks conditions  
**3.** a - setUp runs before each test  
**4.** b - Use `pytest` command  
**5.** b - Percentage of code covered by tests
