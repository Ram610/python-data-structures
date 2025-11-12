# String Manipulation in Python

## Overview
Strings are **immutable** sequences of characters in Python. They are one of the most commonly used data types and come with a rich set of methods for manipulation.

## String Basics

### Creating Strings

```python
# Single quotes
string1 = 'Hello'

# Double quotes
string2 = "World"

# Triple quotes (multi-line)
string3 = '''This is
a multi-line
string'''

string4 = """Another
multi-line string"""

# Raw strings (ignore escape sequences)
raw = r"C:\new\folder"  # Backslashes treated literally

# Empty string
empty = ""
```

### String Indexing and Slicing

```python
text = "Python Programming"

# Indexing (0-based)
print(text[0])    # Output: P
print(text[-1])   # Output: g (last character)
print(text[-2])   # Output: n (second from last)

# Slicing [start:end:step]
print(text[0:6])    # Output: Python
print(text[7:])     # Output: Programming
print(text[:6])     # Output: Python
print(text[::2])    # Output: Pto rgamn (every 2nd char)
print(text[::-1])   # Output: gnimmargorP nohtyP (reverse)
```

## String Methods

### Case Manipulation

```python
text = "Hello World"

# Convert to uppercase
print(text.upper())  # Output: HELLO WORLD

# Convert to lowercase
print(text.lower())  # Output: hello world

# Capitalize first character
print(text.capitalize())  # Output: Hello world

# Title case (capitalize each word)
print(text.title())  # Output: Hello World

# Swap case
print(text.swapcase())  # Output: hELLO wORLD

# Check if uppercase/lowercase
print(text.isupper())  # Output: False
print(text.islower())  # Output: False
```

### Searching and Checking

```python
text = "Python Programming"

# Find substring (returns index or -1)
print(text.find("Pro"))  # Output: 7
print(text.find("Java"))  # Output: -1

# Index (like find but raises error if not found)
print(text.index("Pro"))  # Output: 7
# print(text.index("Java"))  # ValueError

# Check if starts/ends with
print(text.startswith("Py"))  # Output: True
print(text.endswith("ing"))   # Output: True

# Count occurrences
print(text.count("o"))  # Output: 2
print(text.count("mm"))  # Output: 1

# Check membership
print("Prog" in text)  # Output: True
print("Java" not in text)  # Output: True
```

### Trimming and Cleaning

```python
text = "   Hello World   "

# Remove whitespace from both ends
print(text.strip())   # Output: "Hello World"

# Remove from left
print(text.lstrip())  # Output: "Hello World   "

# Remove from right
print(text.rstrip())  # Output: "   Hello World"

# Remove specific characters
text2 = "***Hello***"
print(text2.strip("*"))  # Output: "Hello"
```

### Splitting and Joining

```python
# Split string into list
sentence = "Python is awesome"
words = sentence.split()  # Split by whitespace
print(words)  # Output: ['Python', 'is', 'awesome']

# Split by specific delimiter
csv = "apple,banana,cherry"
fruits = csv.split(",")
print(fruits)  # Output: ['apple', 'banana', 'cherry']

# Split with limit
text = "a-b-c-d-e"
parts = text.split("-", 2)  # Split only first 2
print(parts)  # Output: ['a', 'b', 'c-d-e']

# Join list into string
words = ['Python', 'is', 'great']
sentence = " ".join(words)
print(sentence)  # Output: "Python is great"

# Splitlines (split by newlines)
multiline = "Line 1\nLine 2\nLine 3"
lines = multiline.splitlines()
print(lines)  # Output: ['Line 1', 'Line 2', 'Line 3']
```

### Replacing

```python
text = "Hello World"

# Replace substring
new_text = text.replace("World", "Python")
print(new_text)  # Output: "Hello Python"

# Replace with count limit
text2 = "one one one"
result = text2.replace("one", "two", 2)
print(result)  # Output: "two two one"
```

### Checking String Types

```python
# Check if alphanumeric
print("abc123".isalnum())  # Output: True
print("abc 123".isalnum())  # Output: False

# Check if alphabetic
print("abc".isalpha())  # Output: True
print("abc1".isalpha())  # Output: False

# Check if numeric
print("123".isdigit())  # Output: True
print("12.3".isdigit())  # Output: False
print("123".isnumeric())  # Output: True

# Check if decimal
print("123".isdecimal())  # Output: True

# Check if whitespace
print("   ".isspace())  # Output: True
print("a ".isspace())  # Output: False
```

## String Formatting

### Old Style (%)

```python
name = "Alice"
age = 25

# Using % operator
message = "My name is %s and I am %d years old" % (name, age)
print(message)

# With named placeholders
message = "My name is %(name)s, age %(age)d" % {"name": name, "age": age}
```

### str.format()

```python
name = "Bob"
age = 30

# Basic formatting
message = "My name is {} and I am {} years old".format(name, age)
print(message)

# With indices
message = "I am {1} years old. My name is {0}".format(name, age)

# With names
message = "My name is {n} and I am {a} years old".format(n=name, a=age)

# Formatting numbers
pi = 3.14159
print("Pi is {:.2f}".format(pi))  # Output: Pi is 3.14

# Alignment
print("{:<10}".format("left"))    # Left align
print("{:>10}".format("right"))   # Right align
print("{:^10}".format("center"))  # Center align

# Padding with specific character
print("{:*^10}".format("test"))  # Output: ***test***
```

### f-strings (Python 3.6+) - Recommended

```python
name = "Charlie"
age = 35
pi = 3.14159

# Basic f-string
message = f"My name is {name} and I am {age} years old"
print(message)

# Expressions inside f-strings
print(f"Next year I'll be {age + 1}")
print(f"My name in uppercase: {name.upper()}")

# Formatting numbers
print(f"Pi is approximately {pi:.2f}")

# Alignment and padding
print(f"{name:<10}")  # Left align
print(f"{name:>10}")  # Right align
print(f"{name:^10}")  # Center align

# Multiple values
x = 10
y = 20
print(f"{x} + {y} = {x + y}")

# Debug mode (Python 3.8+)
print(f"{name=}")  # Output: name='Charlie'
```

## String Operations

```python
# Concatenation
str1 = "Hello"
str2 = "World"
combined = str1 + " " + str2  # "Hello World"

# Repetition
repeated = "Ha" * 3  # "HaHaHa"

# Length
text = "Python"
length = len(text)  # 6

# Iterate through string
for char in "Python":
    print(char)

# Check membership
print("Py" in "Python")  # True
```

## Common String Patterns

### Reverse a String

```python
text = "Python"
reversed_text = text[::-1]  # "nohtyP"
```

### Remove Vowels

```python
def remove_vowels(text):
    vowels = "aeiouAEIOU"
    return ''.join(char for char in text if char not in vowels)

print(remove_vowels("Hello World"))  # Output: "Hll Wrld"
```

### Count Words

```python
def count_words(text):
    return len(text.split())

print(count_words("Hello World Python"))  # Output: 3
```

### Palindrome Check

```python
def is_palindrome(text):
    cleaned = ''.join(char.lower() for char in text if char.isalnum())
    return cleaned == cleaned[::-1]

print(is_palindrome("A man a plan a canal Panama"))  # Output: True
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is the output of the following code?**
```python
text = "Python"
print(text[-2])
```
a) `y`  
b) `o`  
c) `n`  
d) Error

**2. Which method converts a string to title case?**
a) `upper()`  
b) `capitalize()`  
c) `title()`  
d) `titlecase()`

**3. What does `"Hello World".find("x")` return?**
a) 0  
b) -1  
c) None  
d) Error

**4. What is the output?**
```python
print("Python" * 2)
```
a) `PythonPython`  
b) `Python Python`  
c) `Python2`  
d) Error

**5. Which method splits a string into a list?**
a) `divide()`  
b) `split()`  
c) `separate()`  
d) `break()`

**6. What is the output?**
```python
text = "   Hello   "
print(len(text.strip()))
```
a) 5  
b) 11  
c) 7  
d) 9

**7. Are strings mutable in Python?**
a) Yes  
b) No  
c) Only if defined with single quotes  
d) Only in Python 3

**8. What is the output?**
```python
print("Hello".replace("l", "L"))
```
a) `HeLLo`  
b) `HeLlo`  
c) `Hello`  
d) Error

**9. Which is the most modern string formatting method?**
a) `%` operator  
b) `str.format()`  
c) f-strings  
d) `concat()`

**10. What does `"123".isdigit()` return?**
a) `True`  
b) `False`  
c) `1`  
d) Error

---

### Coding Exercises

**Exercise 1: String Reversal**
Write a function that reverses each word in a sentence while keeping the word order the same.
Example: "Hello World" → "olleH dlroW"

**Exercise 2: Character Frequency**
Create a function that returns a dictionary with the frequency of each character in a string (case-insensitive, ignore spaces).

**Exercise 3: Title Case Converter**
Write a function that converts a string to title case, but keeps small words (like "a", "an", "the", "and", "but", "or") in lowercase unless they're the first word.

**Exercise 4: String Compression**
Implement a function that compresses a string by replacing consecutive repeated characters with the character followed by the count.
Example: "aaabbbcc" → "a3b3c2"

**Exercise 5: Valid Palindrome**
Write a function that checks if a string is a palindrome, ignoring spaces, punctuation, and case.

**Exercise 6: String Rotation**
Create a function that checks if one string is a rotation of another.
Example: "waterbottle" is a rotation of "erbottlewat"

**Exercise 7: Extract Numbers**
Write a function that extracts all numbers from a string and returns them as a list of integers.
Example: "abc123def456" → [123, 456]

**Exercise 8: Camel Case to Snake Case**
Create a function that converts camelCase or PascalCase strings to snake_case.
Example: "myVariableName" → "my_variable_name"

---

## Answers

### Multiple Choice Answers
1. **b** - `text[-2]` is 'o' (second from last)
2. **c** - `title()` capitalizes first letter of each word
3. **b** - `find()` returns -1 when substring not found
4. **a** - String repetition concatenates without spaces
5. **b** - `split()` splits string into list
6. **a** - `strip()` removes whitespace, leaving "Hello" (5 characters)
7. **b** - Strings are immutable in Python
8. **a** - `replace()` replaces all occurrences by default
9. **c** - f-strings (Python 3.6+) are most modern and readable
10. **a** - "123" contains only digits, so returns True

### Coding Exercise Solutions

**Solution 1:**
```python
def reverse_words(sentence):
    words = sentence.split()
    reversed_words = [word[::-1] for word in words]
    return " ".join(reversed_words)

# Test
print(reverse_words("Hello World Python"))
# Output: "olleH dlroW nohtyP"
```

**Solution 2:**
```python
def char_frequency(text):
    text = text.lower().replace(" ", "")
    frequency = {}
    for char in text:
        frequency[char] = frequency.get(char, 0) + 1
    return frequency

# Test
print(char_frequency("Hello World"))
# Output: {'h': 1, 'e': 1, 'l': 3, 'o': 2, 'w': 1, 'r': 1, 'd': 1}
```

**Solution 3:**
```python
def smart_title_case(text):
    small_words = {'a', 'an', 'the', 'and', 'but', 'or', 'for', 'nor', 'on', 'at', 'to', 'by'}
    words = text.lower().split()
    
    result = []
    for i, word in enumerate(words):
        if i == 0 or word not in small_words:
            result.append(word.capitalize())
        else:
            result.append(word)
    
    return " ".join(result)

# Test
print(smart_title_case("the quick brown fox and the lazy dog"))
# Output: "The Quick Brown Fox and the Lazy Dog"
```

**Solution 4:**
```python
def compress_string(text):
    if not text:
        return ""
    
    compressed = []
    count = 1
    current = text[0]
    
    for char in text[1:]:
        if char == current:
            count += 1
        else:
            compressed.append(f"{current}{count}")
            current = char
            count = 1
    
    compressed.append(f"{current}{count}")
    
    result = "".join(compressed)
    return result if len(result) < len(text) else text

# Test
print(compress_string("aaabbbcc"))  # Output: "a3b3c2"
print(compress_string("abc"))       # Output: "abc" (no compression)
```

**Solution 5:**
```python
def is_valid_palindrome(text):
    # Keep only alphanumeric characters and convert to lowercase
    cleaned = ''.join(char.lower() for char in text if char.isalnum())
    return cleaned == cleaned[::-1]

# Test
print(is_valid_palindrome("A man, a plan, a canal: Panama"))  # Output: True
print(is_valid_palindrome("race a car"))  # Output: False
```

**Solution 6:**
```python
def is_rotation(s1, s2):
    # Check if s1 and s2 have same length and s1 is not empty
    if len(s1) != len(s2) or len(s1) == 0:
        return False
    
    # s1 is rotation of s2 if s1 is substring of s2+s2
    return s1 in (s2 + s2)

# Test
print(is_rotation("waterbottle", "erbottlewat"))  # Output: True
print(is_rotation("hello", "lohel"))  # Output: True
print(is_rotation("hello", "world"))  # Output: False
```

**Solution 7:**
```python
def extract_numbers(text):
    import re
    # Find all sequences of digits
    numbers = re.findall(r'\d+', text)
    return [int(num) for num in numbers]

# Alternative without regex
def extract_numbers_no_regex(text):
    numbers = []
    current_num = ""
    
    for char in text:
        if char.isdigit():
            current_num += char
        elif current_num:
            numbers.append(int(current_num))
            current_num = ""
    
    if current_num:
        numbers.append(int(current_num))
    
    return numbers

# Test
print(extract_numbers("abc123def456ghi"))  # Output: [123, 456]
print(extract_numbers_no_regex("abc123def456ghi"))  # Output: [123, 456]
```

**Solution 8:**
```python
def camel_to_snake(text):
    import re
    # Insert underscore before uppercase letters and convert to lowercase
    snake = re.sub(r'(?<!^)(?=[A-Z])', '_', text).lower()
    return snake

# Alternative without regex
def camel_to_snake_no_regex(text):
    result = []
    for i, char in enumerate(text):
        if char.isupper() and i > 0:
            result.append('_')
        result.append(char.lower())
    return ''.join(result)

# Test
print(camel_to_snake("myVariableName"))  # Output: "my_variable_name"
print(camel_to_snake("PascalCaseExample"))  # Output: "pascal_case_example"
print(camel_to_snake_no_regex("myVariableName"))  # Output: "my_variable_name"
```
