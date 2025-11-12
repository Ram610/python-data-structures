# File I/O in Python

## Overview
File Input/Output operations allow you to read from and write to files on your computer. Python provides built-in functions to handle file operations efficiently.

## Opening Files

### Basic Syntax

```python
# Open file
file = open('filename.txt', 'mode')

# Perform operations
# ...

# Close file (important!)
file.close()
```

### File Modes

| Mode | Description |
|------|-------------|
| `'r'` | Read (default) - file must exist |
| `'w'` | Write - creates new or overwrites existing |
| `'a'` | Append - adds to end of file |
| `'x'` | Exclusive creation - fails if file exists |
| `'r+'` | Read and write |
| `'b'` | Binary mode (e.g., `'rb'`, `'wb'`) |
| `'t'` | Text mode (default) |

## Reading Files

### Read Entire File

```python
# Method 1: read()
file = open('data.txt', 'r')
content = file.read()
print(content)
file.close()

# Method 2: Using with statement (recommended)
with open('data.txt', 'r') as file:
    content = file.read()
    print(content)
# File automatically closed after with block
```

### Read Line by Line

```python
# Method 1: readline()
with open('data.txt', 'r') as file:
    line1 = file.readline()  # Read first line
    line2 = file.readline()  # Read second line
    print(line1, line2)

# Method 2: readlines() - returns list
with open('data.txt', 'r') as file:
    lines = file.readlines()  # Returns list of all lines
    for line in lines:
        print(line.strip())  # strip() removes \n

# Method 3: Iterate directly (memory efficient)
with open('data.txt', 'r') as file:
    for line in file:
        print(line.strip())
```

### Read Specific Amount

```python
with open('data.txt', 'r') as file:
    # Read first 50 characters
    chunk = file.read(50)
    print(chunk)
    
    # Read next 50 characters
    chunk2 = file.read(50)
    print(chunk2)
```

## Writing Files

### Write to File

```python
# Write mode - overwrites existing content
with open('output.txt', 'w') as file:
    file.write("Hello World\n")
    file.write("Python is awesome!")

# Write list of lines
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]
with open('output.txt', 'w') as file:
    file.writelines(lines)
```

### Append to File

```python
# Append mode - adds to end of file
with open('output.txt', 'a') as file:
    file.write("\nThis is appended")
    file.write("\nAnother line")
```

## File Operations

### Check if File Exists

```python
import os

# Method 1: os.path.exists()
if os.path.exists('file.txt'):
    print("File exists")
else:
    print("File does not exist")

# Method 2: os.path.isfile()
if os.path.isfile('file.txt'):
    print("File exists and is a file")

# Method 3: Using pathlib (Python 3.4+)
from pathlib import Path

file = Path('file.txt')
if file.exists():
    print("File exists")
if file.is_file():
    print("Is a file")
```

### Get File Information

```python
import os

# File size
size = os.path.getsize('file.txt')
print(f"Size: {size} bytes")

# File modification time
import time
mod_time = os.path.getmtime('file.txt')
print(f"Modified: {time.ctime(mod_time)}")

# Using pathlib
from pathlib import Path
file = Path('file.txt')
print(f"Size: {file.stat().st_size} bytes")
print(f"Modified: {time.ctime(file.stat().st_mtime)}")
```

### Delete Files

```python
import os

# Delete file
if os.path.exists('file.txt'):
    os.remove('file.txt')
    print("File deleted")

# Using pathlib
from pathlib import Path
file = Path('file.txt')
if file.exists():
    file.unlink()
    print("File deleted")
```

### Rename/Move Files

```python
import os

# Rename file
os.rename('old_name.txt', 'new_name.txt')

# Move file
os.rename('file.txt', 'folder/file.txt')

# Using pathlib
from pathlib import Path
file = Path('old_name.txt')
file.rename('new_name.txt')
```

## Working with Directories

```python
import os

# Get current directory
current_dir = os.getcwd()
print(current_dir)

# Change directory
os.chdir('/path/to/directory')

# List files in directory
files = os.listdir('.')
print(files)

# Create directory
os.mkdir('new_folder')

# Create nested directories
os.makedirs('parent/child/grandchild')

# Remove directory
os.rmdir('folder')  # Only empty directories

# Remove directory tree
import shutil
shutil.rmtree('folder')  # Removes folder and all contents
```

## Binary Files

```python
# Write binary file
data = b'\x00\x01\x02\x03'
with open('file.bin', 'wb') as file:
    file.write(data)

# Read binary file
with open('file.bin', 'rb') as file:
    data = file.read()
    print(data)

# Copy binary file
with open('source.jpg', 'rb') as source:
    with open('destination.jpg', 'wb') as dest:
        dest.write(source.read())
```

## Working with CSV Files

```python
import csv

# Writing CSV
data = [
    ['Name', 'Age', 'City'],
    ['Alice', '25', 'New York'],
    ['Bob', '30', 'Paris']
]

with open('data.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(data)

# Reading CSV
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

# Using DictReader/DictWriter
with open('data.csv', 'r') as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row['Name'], row['Age'])
```

## Working with JSON Files

```python
import json

# Writing JSON
data = {
    'name': 'Alice',
    'age': 25,
    'courses': ['Math', 'CS']
}

with open('data.json', 'w') as file:
    json.dump(data, file, indent=4)

# Reading JSON
with open('data.json', 'r') as file:
    data = json.load(file)
    print(data['name'])

# JSON string operations
json_string = json.dumps(data)  # Convert to string
data = json.loads(json_string)  # Parse from string
```

## Context Managers and with Statement

```python
# Why use 'with'?
# 1. Automatically closes file
# 2. Handles exceptions properly
# 3. Cleaner code

# Without with (not recommended)
file = open('file.txt', 'r')
try:
    content = file.read()
finally:
    file.close()

# With 'with' statement (recommended)
with open('file.txt', 'r') as file:
    content = file.read()
# File automatically closed

# Multiple files
with open('input.txt', 'r') as infile, open('output.txt', 'w') as outfile:
    content = infile.read()
    outfile.write(content.upper())
```

---

## Practice Questions

### Multiple Choice Questions

**1. Which mode opens a file for reading?**
a) `'w'`  
b) `'r'`  
c) `'a'`  
d) `'x'`

**2. What happens if you open a file in `'w'` mode?**
a) File is created if it doesn't exist  
b) Existing content is overwritten  
c) Both a and b  
d) Error if file doesn't exist

**3. Which method reads the entire file content?**
a) `readline()`  
b) `readlines()`  
c) `read()`  
d) `readall()`

**4. What is the advantage of using `with` statement?**
a) Automatically closes the file  
b) Handles exceptions  
c) Cleaner code  
d) All of the above

**5. Which mode appends to a file?**
a) `'w'`  
b) `'r+'`  
c) `'a'`  
d) `'x'`

**6. What does `readlines()` return?**
a) String  
b) List of strings  
c) Dictionary  
d) Tuple

**7. How to check if a file exists?**
a) `os.path.exists()`  
b) `file.exists()`  
c) `exists(file)`  
d) `check_file()`

**8. Which module is used for JSON operations?**
a) `csv`  
b) `json`  
c) `file`  
d) `io`

---

### Coding Exercises

**Exercise 1: Word Counter**
Write a function that reads a text file and returns the total number of words.

**Exercise 2: File Copy**
Create a function that copies the content from one file to another.

**Exercise 3: Line Numbers**
Write a program that reads a file and writes it to another file with line numbers.

**Exercise 4: Find and Replace**
Create a function that finds and replaces all occurrences of a word in a file.

**Exercise 5: CSV Analyzer**
Write a function that reads a CSV file and returns:
- Total rows
- Column names
- Average of a numeric column

**Exercise 6: Log File Parser**
Create a function that reads a log file and extracts all lines containing "ERROR".

**Exercise 7: JSON Config**
Write functions to save and load configuration settings using JSON files.

**Exercise 8: Large File Processing**
Create a function that processes a large file line by line without loading the entire file into memory.

---

## Answers

### Multiple Choice Answers
1. **b** - `'r'` mode opens file for reading
2. **c** - `'w'` mode creates file and overwrites existing content
3. **c** - `read()` reads entire file content
4. **d** - `with` statement provides all these benefits
5. **c** - `'a'` mode appends to file
6. **b** - `readlines()` returns list of strings
7. **a** - `os.path.exists()` checks file existence
8. **b** - `json` module handles JSON operations

### Coding Exercise Solutions

**Solution 1:**
```python
def count_words(filename):
    try:
        with open(filename, 'r') as file:
            content = file.read()
            words = content.split()
            return len(words)
    except FileNotFoundError:
        return "File not found"

# Test
print(count_words('sample.txt'))
```

**Solution 2:**
```python
def copy_file(source, destination):
    try:
        with open(source, 'r') as src, open(destination, 'w') as dest:
            content = src.read()
            dest.write(content)
        return "File copied successfully"
    except FileNotFoundError:
        return "Source file not found"

# Test
print(copy_file('input.txt', 'output.txt'))
```

**Solution 3:**
```python
def add_line_numbers(input_file, output_file):
    try:
        with open(input_file, 'r') as infile, open(output_file, 'w') as outfile:
            for line_num, line in enumerate(infile, 1):
                outfile.write(f"{line_num}: {line}")
        return "Line numbers added successfully"
    except FileNotFoundError:
        return "Input file not found"

# Test
print(add_line_numbers('input.txt', 'numbered.txt'))
```

**Solution 4:**
```python
def find_and_replace(filename, find_word, replace_word):
    try:
        with open(filename, 'r') as file:
            content = file.read()
        
        content = content.replace(find_word, replace_word)
        
        with open(filename, 'w') as file:
            file.write(content)
        
        return f"Replaced all occurrences of '{find_word}' with '{replace_word}'"
    except FileNotFoundError:
        return "File not found"

# Test
print(find_and_replace('sample.txt', 'old', 'new'))
```

**Solution 5:**
```python
import csv

def analyze_csv(filename, numeric_column):
    try:
        with open(filename, 'r') as file:
            reader = csv.DictReader(file)
            rows = list(reader)
            
            total_rows = len(rows)
            column_names = reader.fieldnames
            
            # Calculate average of numeric column
            values = [float(row[numeric_column]) for row in rows if row[numeric_column].replace('.','').isdigit()]
            average = sum(values) / len(values) if values else 0
            
            return {
                'total_rows': total_rows,
                'columns': column_names,
                f'average_{numeric_column}': average
            }
    except FileNotFoundError:
        return "File not found"
    except KeyError:
        return f"Column '{numeric_column}' not found"

# Test
print(analyze_csv('data.csv', 'age'))
```

**Solution 6:**
```python
def extract_errors(log_file, output_file):
    try:
        error_count = 0
        with open(log_file, 'r') as infile, open(output_file, 'w') as outfile:
            for line in infile:
                if 'ERROR' in line:
                    outfile.write(line)
                    error_count += 1
        return f"Found {error_count} errors"
    except FileNotFoundError:
        return "Log file not found"

# Test
print(extract_errors('app.log', 'errors.txt'))
```

**Solution 7:**
```python
import json

def save_config(filename, config):
    with open(filename, 'w') as file:
        json.dump(config, file, indent=4)
    return "Configuration saved"

def load_config(filename):
    try:
        with open(filename, 'r') as file:
            return json.load(file)
    except FileNotFoundError:
        return {}

# Test
config = {
    'host': 'localhost',
    'port': 8080,
    'debug': True
}
save_config('config.json', config)
loaded = load_config('config.json')
print(loaded)
```

**Solution 8:**
```python
def process_large_file(filename, process_function):
    """
    Process large file line by line
    process_function: function to apply to each line
    """
    try:
        results = []
        with open(filename, 'r') as file:
            for line in file:
                result = process_function(line.strip())
                if result is not None:
                    results.append(result)
        return results
    except FileNotFoundError:
        return "File not found"

# Example: Extract lines with specific keyword
def filter_keyword(line):
    return line if 'python' in line.lower() else None

# Test
results = process_large_file('large_file.txt', filter_keyword)
print(f"Found {len(results)} matching lines")
```
