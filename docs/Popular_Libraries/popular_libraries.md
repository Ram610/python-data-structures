# Popular Python Libraries

## NumPy - Numerical Computing

### Installation
```bash
pip install numpy
```

### Basic Operations
```python
import numpy as np

# Create arrays
arr = np.array([1, 2, 3, 4, 5])
matrix = np.array([[1, 2], [3, 4]])

# Array operations
print(arr * 2)  # [2 4 6 8 10]
print(arr + 10)  # [11 12 13 14 15]
print(arr.mean())  # 3.0
print(arr.sum())  # 15

# Matrix operations
print(matrix.T)  # Transpose
print(matrix.shape)  # (2, 2)
```

## pandas - Data Analysis

### Installation
```bash
pip install pandas
```

### DataFrames
```python
import pandas as pd

# Create DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['NYC', 'LA', 'Chicago']
}
df = pd.DataFrame(data)

# Operations
print(df.head())
print(df.describe())
print(df['Age'].mean())

# Read CSV
df = pd.read_csv('data.csv')

# Filter data
young = df[df['Age'] < 30]

# Group by
grouped = df.groupby('City').mean()
```

## matplotlib - Visualization

### Installation
```bash
pip install matplotlib
```

### Basic Plot
```python
import matplotlib.pyplot as plt

# Line plot
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
plt.plot(x, y)
plt.xlabel('X axis')
plt.ylabel('Y axis')
plt.title('Line Plot')
plt.show()

# Bar chart
categories = ['A', 'B', 'C']
values = [10, 15, 7]
plt.bar(categories, values)
plt.show()

# Scatter plot
plt.scatter(x, y)
plt.show()
```

## requests - HTTP Library

### Installation
```bash
pip install requests
```

### Making Requests
```python
import requests

# GET request
response = requests.get('https://api.github.com')
print(response.status_code)
print(response.json())

# POST request
data = {'key': 'value'}
response = requests.post('https://httpbin.org/post', json=data)

# With parameters
params = {'q': 'python'}
response = requests.get('https://api.github.com/search/repositories', params=params)
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is NumPy used for?**
a) Web development  
b) Numerical computing  
c) Database management  
d) Graphics

**2. What data structure does pandas use?**
a) Array  
b) List  
c) DataFrame  
d) Dictionary

**3. What does matplotlib create?**
a) Web pages  
b) Visualizations  
c) APIs  
d) Databases

**4. What does requests library do?**
a) HTTP requests  
b) File I/O  
c) Math operations  
d) Testing

---

## Answers

**1.** b - NumPy for numerical computing  
**2.** c - pandas uses DataFrames  
**3.** b - matplotlib creates visualizations  
**4.** a - requests makes HTTP requests
