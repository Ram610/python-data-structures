# Object-Oriented Programming in Python

## Overview
OOP is a programming paradigm that organizes code into objects containing data (attributes) and code (methods).

## Classes and Objects

```python
# Define a class
class Dog:
    # Class attribute (shared by all instances)
    species = "Canis familiaris"
    
    # Constructor
    def __init__(self, name, age):
        # Instance attributes
        self.name = name
        self.age = age
    
    # Instance method
    def bark(self):
        return f"{self.name} says Woof!"
    
    # Another method
    def birthday(self):
        self.age += 1
        return f"{self.name} is now {self.age} years old"

# Create objects (instances)
dog1 = Dog("Buddy", 3)
dog2 = Dog("Lucy", 5)

# Access attributes
print(dog1.name)  # Output: Buddy
print(dog1.species)  # Output: Canis familiaris

# Call methods
print(dog1.bark())  # Output: Buddy says Woof!
print(dog1.birthday())  # Output: Buddy is now 4 years old
```

## Inheritance

```python
# Parent class
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        return "Some sound"
    
    def info(self):
        return f"I am {self.name}"

# Child class inherits from Animal
class Dog(Animal):
    def speak(self):
        return "Woof!"
    
    def fetch(self):
        return f"{self.name} is fetching the ball"

class Cat(Animal):
    def speak(self):
        return "Meow!"
    
    def scratch(self):
        return f"{self.name} is scratching"

# Using inherited classes
dog = Dog("Buddy")
cat = Cat("Whiskers")

print(dog.speak())  # Output: Woof! (overridden)
print(dog.info())   # Output: I am Buddy (inherited)
print(dog.fetch())  # Output: Buddy is fetching the ball

print(cat.speak())  # Output: Meow!
```

## Encapsulation

```python
class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner
        self.__balance = balance  # Private attribute (name mangling)
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return f"Deposited ${amount}. New balance: ${self.__balance}"
        return "Invalid amount"
    
    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return f"Withdrew ${amount}. New balance: ${self.__balance}"
        return "Insufficient funds or invalid amount"
    
    def get_balance(self):
        return self.__balance

# Usage
account = BankAccount("Alice", 1000)
print(account.deposit(500))  # Output: Deposited $500. New balance: $1500
# print(account.__balance)  # AttributeError: can't access private attribute
print(account.get_balance())  # Output: 1500
```

## Polymorphism

```python
# Method overriding
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return 3.14 * self.radius ** 2

# Polymorphism in action
shapes = [Rectangle(4, 5), Circle(3), Rectangle(2, 10)]

for shape in shapes:
    print(f"Area: {shape.area()}")
# Different implementations of area() called
```

## Special Methods (Magic Methods)

```python
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages
    
    def __str__(self):
        # String representation for users
        return f"{self.title} by {self.author}"
    
    def __repr__(self):
        # String representation for developers
        return f"Book('{self.title}', '{self.author}', {self.pages})"
    
    def __len__(self):
        return self.pages
    
    def __eq__(self, other):
        return self.title == other.title and self.author == other.author
    
    def __lt__(self, other):
        return self.pages < other.pages

# Usage
book1 = Book("Python 101", "John Doe", 350)
book2 = Book("Advanced Python", "Jane Smith", 500)

print(book1)  # Calls __str__: Python 101 by John Doe
print(len(book1))  # Calls __len__: 350
print(book1 == book2)  # Calls __eq__: False
print(book1 < book2)  # Calls __lt__: True
```

## Class Methods and Static Methods

```python
class Employee:
    company = "TechCorp"
    num_employees = 0
    
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
        Employee.num_employees += 1
    
    # Instance method
    def give_raise(self, amount):
        self.salary += amount
    
    # Class method
    @classmethod
    def from_string(cls, emp_str):
        # Alternative constructor
        name, salary = emp_str.split('-')
        return cls(name, int(salary))
    
    @classmethod
    def set_company(cls, new_company):
        cls.company = new_company
    
    # Static method
    @staticmethod
    def is_workday(day):
        return day.weekday() < 5

# Usage
emp1 = Employee("Alice", 50000)
emp2 = Employee.from_string("Bob-60000")  # Using class method

print(Employee.num_employees)  # Output: 2

import datetime
today = datetime.date.today()
print(Employee.is_workday(today))  # Using static method
```

## Property Decorators

```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius
    
    @property
    def celsius(self):
        return self._celsius
    
    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero is not possible")
        self._celsius = value
    
    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        self.celsius = (value - 32) * 5/9

# Usage
temp = Temperature(25)
print(temp.celsius)  # Output: 25
print(temp.fahrenheit)  # Output: 77.0

temp.fahrenheit = 100
print(temp.celsius)  # Output: 37.77...
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is the purpose of `__init__`?**
a) Destroy object  
b) Initialize object  
c) Copy object  
d) None

**2. What is inheritance?**
a) Creating new class from existing class  
b) Hiding data  
c) Method overloading  
d) None

**3. Which method makes objects printable?**
a) `__print__`  
b) `__display__`  
c) `__str__`  
d) `__show__`

**4. What is encapsulation?**
a) Hiding implementation details  
b) Inheriting from parent  
c) Method overriding  
d) Creating objects

**5. What does `@classmethod` do?**
a) Creates instance method  
b) Creates class method  
c) Creates static method  
d) Creates property

---

## Coding Exercises

**Exercise 1: Create a `Person` class with name, age, and method to introduce themselves.**

**Exercise 2: Create a `Vehicle` parent class and `Car`, `Bike` child classes with inheritance.**

**Exercise 3: Implement a `Rectangle` class with properties for area and perimeter.**

**Exercise 4: Create a `Library` class that manages `Book` objects.**

---

## Answers

### Solutions

**Solution 1:**
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"Hi, I'm {self.name} and I'm {self.age} years old"

person = Person("Alice", 30)
print(person.introduce())
```

**Solution 2:**
```python
class Vehicle:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model
    
    def info(self):
        return f"{self.brand} {self.model}"

class Car(Vehicle):
    def __init__(self, brand, model, doors):
        super().__init__(brand, model)
        self.doors = doors
    
    def info(self):
        return f"{super().info()} with {self.doors} doors"

class Bike(Vehicle):
    def __init__(self, brand, model, type):
        super().__init__(brand, model)
        self.type = type
    
    def info(self):
        return f"{super().info()} - {self.type} bike"

car = Car("Toyota", "Camry", 4)
bike = Bike("Yamaha", "R15", "Sport")
print(car.info())
print(bike.info())
```
