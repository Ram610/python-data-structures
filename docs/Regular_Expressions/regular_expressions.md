# Regular Expressions in Python

## Overview
Regular expressions (regex) are patterns used to match character combinations in strings.

## Basic Patterns

### Importing re Module
```python
import re
```

### Simple Matching
```python
# Search for pattern
text = "Python is awesome"
match = re.search(r'Python', text)
if match:
    print("Found:", match.group())  # Found: Python

# Match at start
match = re.match(r'Python', text)
print(match.group() if match else "Not found")

# Find all occurrences
text = "cat bat rat"
matches = re.findall(r'[cbr]at', text)
print(matches)  # ['cat', 'bat', 'rat']
```

## Metacharacters

| Pattern | Description |
|---------|-------------|
| `.` | Any character except newline |
| `^` | Start of string |
| `$` | End of string |
| `*` | 0 or more repetitions |
| `+` | 1 or more repetitions |
| `?` | 0 or 1 repetition |
| `{m,n}` | m to n repetitions |
| `[]` | Character class |
| `|` | OR operator |
| `()` | Capturing group |
| `\` | Escape special char |

## Character Classes

```python
# Digits
pattern = r'\d+'  # One or more digits
text = "Room 123"
match = re.search(pattern, text)
print(match.group())  # 123

# Word characters [a-zA-Z0-9_]
pattern = r'\w+'
text = "hello_world"
print(re.findall(pattern, text))  # ['hello_world']

# Whitespace
pattern = r'\s+'
text = "hello    world"
print(re.split(pattern, text))  # ['hello', 'world']

# Non-digit
pattern = r'\D+'
text = "abc123def"
print(re.findall(pattern, text))  # ['abc', 'def']
```

## Common Patterns

### Email Validation
```python
def validate_email(email):
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, email))

print(validate_email("user@example.com"))  # True
print(validate_email("invalid.email"))  # False
```

### Phone Number
```python
def extract_phone(text):
    pattern = r'\b\d{3}[-.]?\d{3}[-.]?\d{4}\b'
    return re.findall(pattern, text)

text = "Call 123-456-7890 or 987.654.3210"
print(extract_phone(text))  # ['123-456-7890', '987.654.3210']
```

### URL Extraction
```python
def extract_urls(text):
    pattern = r'https?://(?:www\.)?[a-zA-Z0-9./]+'
    return re.findall(pattern, text)

text = "Visit https://www.python.org and http://github.com"
print(extract_urls(text))
```

## re Module Functions

### search() vs match()
```python
# match() checks at beginning
text = "hello world"
print(re.match(r'world', text))  # None
print(re.search(r'world', text))  # Match object

# findall() returns all matches
text = "cat bat rat"
print(re.findall(r'\w+at', text))  # ['cat', 'bat', 'rat']

# finditer() returns iterator
for match in re.finditer(r'\w+at', text):
    print(match.group(), match.span())
```

### Substitution
```python
# sub() - replace matches
text = "Hello World"
result = re.sub(r'World', 'Python', text)
print(result)  # Hello Python

# subn() - replace and count
text = "cat bat cat rat"
result, count = re.subn(r'cat', 'dog', text)
print(result, count)  # dog bat dog rat, 2
```

### Split
```python
# Split by pattern
text = "apple,banana;cherry:date"
fruits = re.split(r'[,;:]', text)
print(fruits)  # ['apple', 'banana', 'cherry', 'date']
```

## Groups and Capturing

```python
# Capturing groups
pattern = r'(\d{3})-(\d{3})-(\d{4})'
text = "Phone: 123-456-7890"
match = re.search(pattern, text)
if match:
    print(match.group(0))  # 123-456-7890 (entire match)
    print(match.group(1))  # 123
    print(match.group(2))  # 456
    print(match.group(3))  # 7890

# Named groups
pattern = r'(?P<area>\d{3})-(?P<exchange>\d{3})-(?P<number>\d{4})'
match = re.search(pattern, text)
if match:
    print(match.group('area'))  # 123
    print(match.groupdict())  # {'area': '123', 'exchange': '456', 'number': '7890'}
```

## Flags

```python
# re.IGNORECASE or re.I
print(re.search(r'python', 'Python', re.IGNORECASE))  # Match

# re.MULTILINE or re.M
text = "line1\nline2\nline3"
print(re.findall(r'^line', text, re.MULTILINE))  # ['line', 'line', 'line']

# re.DOTALL or re.S (dot matches newline)
text = "first\nsecond"
print(re.search(r'first.second', text, re.DOTALL))  # Match
```

---

## Practice Questions

### Multiple Choice Questions

**1. What does `.` match?**
a) Any character except newline  
b) Only letters  
c) Only digits  
d) Nothing

**2. What does `\d` represent?**
a) Letter  
b) Digit  
c) Whitespace  
d) Word

**3. What does `+` mean?**
a) Exactly one  
b) Zero or more  
c) One or more  
d) Optional

**4. Which function finds all matches?**
a) `search()`  
b) `match()`  
c) `findall()`  
d) `find()`

**5. What does `^` match?**
a) End of string  
b) Start of string  
c) Any character  
d) Newline

---

## Coding Exercises

**Exercise 1:** Extract all email addresses from text.

**Exercise 2:** Validate password (8+ chars, 1 uppercase, 1 digit).

**Exercise 3:** Find all hashtags in social media text.

**Exercise 4:** Replace multiple spaces with single space.

**Exercise 5:** Extract date in format DD-MM-YYYY.

---

## Answers

**Solution 1:**
```python
def extract_emails(text):
    pattern = r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}'
    return re.findall(pattern, text)

text = "Contact us: info@example.com or support@test.org"
print(extract_emails(text))
```

**Solution 2:**
```python
def validate_password(password):
    pattern = r'^(?=.*[A-Z])(?=.*\d).{8,}$'
    return bool(re.match(pattern, password))

print(validate_password("Secure123"))  # True
print(validate_password("weak"))  # False
```

**Solution 3:**
```python
def extract_hashtags(text):
    pattern = r'#\w+'
    return re.findall(pattern, text)

text = "Love #Python and #Programming #Code"
print(extract_hashtags(text))  # ['#Python', '#Programming', '#Code']
```

**Solution 4:**
```python
def normalize_spaces(text):
    return re.sub(r'\s+', ' ', text)

text = "Hello    World   Python"
print(normalize_spaces(text))  # "Hello World Python"
```

**Solution 5:**
```python
def extract_dates(text):
    pattern = r'\b(\d{2})-(\d{2})-(\d{4})\b'
    return re.findall(pattern, text)

text = "Events on 25-12-2023 and 01-01-2024"
print(extract_dates(text))  # [('25', '12', '2023'), ('01', '01', '2024')]
```
