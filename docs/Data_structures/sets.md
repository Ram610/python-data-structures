# Sets in Python

## Overview
Sets are **unordered** collections of **unique** elements. They are mutable and provide efficient membership testing and set operations.

## Key Characteristics
- **Unordered**: No guaranteed order of elements
- **Unique elements**: No duplicates allowed
- **Mutable**: Can add/remove elements
- **No indexing**: Cannot access by index
- **Only immutable elements**: Cannot contain lists or dictionaries

## Creating Sets

```python
# Empty set (must use set())
empty_set = set()  # Correct
not_a_set = {}     # This creates an empty dictionary

# Set with elements
numbers = {1, 2, 3, 4, 5}
mixed = {1, "hello", 3.14, True}

# Set from iterable
list_to_set = set([1, 2, 3, 2, 1])  # {1, 2, 3}
string_to_set = set("hello")  # {'h', 'e', 'l', 'o'}

# Removing duplicates
with_duplicates = {1, 2, 2, 3, 3, 3}
print(with_duplicates)  # Output: {1, 2, 3}
```

## Set Methods

### Adding Elements

```python
fruits = {"apple", "banana"}

# add() - adds a single element
fruits.add("cherry")
print(fruits)  # {'apple', 'banana', 'cherry'}

# update() - adds multiple elements
fruits.update(["date", "elderberry"])
print(fruits)  # {'apple', 'banana', 'cherry', 'date', 'elderberry'}

# update with multiple iterables
fruits.update(["fig"], {"grape"})
```

### Removing Elements

```python
numbers = {1, 2, 3, 4, 5}

# remove() - raises KeyError if element doesn't exist
numbers.remove(3)  # {1, 2, 4, 5}
# numbers.remove(10)  # KeyError

# discard() - doesn't raise error if element doesn't exist
numbers.discard(4)  # {1, 2, 5}
numbers.discard(10)  # No error

# pop() - removes and returns an arbitrary element
element = numbers.pop()  # Removes random element
print(element)

# clear() - removes all elements
numbers.clear()  # set()
```

## Set Operations

### Mathematical Set Operations

```python
set1 = {1, 2, 3, 4, 5}
set2 = {4, 5, 6, 7, 8}

# Union - all elements from both sets
union1 = set1 | set2
union2 = set1.union(set2)
print(union1)  # {1, 2, 3, 4, 5, 6, 7, 8}

# Intersection - elements common to both sets
intersection1 = set1 & set2
intersection2 = set1.intersection(set2)
print(intersection1)  # {4, 5}

# Difference - elements in set1 but not in set2
difference1 = set1 - set2
difference2 = set1.difference(set2)
print(difference1)  # {1, 2, 3}

# Symmetric Difference - elements in either set but not both
sym_diff1 = set1 ^ set2
sym_diff2 = set1.symmetric_difference(set2)
print(sym_diff1)  # {1, 2, 3, 6, 7, 8}
```

### Set Comparisons

```python
set_a = {1, 2, 3}
set_b = {1, 2, 3, 4, 5}
set_c = {1, 2, 3}

# Subset - all elements of set_a are in set_b
print(set_a <= set_b)  # True
print(set_a.issubset(set_b))  # True

# Proper subset - subset but not equal
print(set_a < set_b)  # True

# Superset - all elements of set_a are in set_b
print(set_b >= set_a)  # True
print(set_b.issuperset(set_a))  # True

# Proper superset
print(set_b > set_a)  # True

# Disjoint - no common elements
set_d = {6, 7, 8}
print(set_a.isdisjoint(set_d))  # True
```

## Frozen Sets

Immutable version of sets - can be used as dictionary keys or elements of other sets.

```python
# Creating frozen set
frozen = frozenset([1, 2, 3, 4])

# Can be used as dictionary key
dict_with_frozen = {frozen: "value"}

# Can be element of set
set_of_frozensets = {
    frozenset([1, 2]),
    frozenset([3, 4])
}

# Cannot modify
# frozen.add(5)  # AttributeError
```

## Common Use Cases

### Remove Duplicates

```python
def remove_duplicates(items):
    return list(set(items))

numbers = [1, 2, 2, 3, 3, 3, 4, 5, 5]
unique = remove_duplicates(numbers)
print(unique)  # [1, 2, 3, 4, 5] (order may vary)
```

### Membership Testing

```python
# Sets are much faster for membership testing than lists
large_set = set(range(1000000))
large_list = list(range(1000000))

# Fast
print(999999 in large_set)  # O(1)

# Slow
print(999999 in large_list)  # O(n)
```

### Finding Common Elements

```python
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]

common = set(list1) & set(list2)
print(common)  # {4, 5}
```

## Set Comprehensions

```python
# Basic set comprehension
squares = {x**2 for x in range(10)}
print(squares)  # {0, 1, 4, 9, 16, 25, 36, 49, 64, 81}

# With condition
even_squares = {x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0, 4, 16, 36, 64}

# From string
vowels = {char.lower() for char in "Hello World" if char.lower() in 'aeiou'}
print(vowels)  # {'e', 'o'}
```

---

## Practice Questions

### Multiple Choice Questions

**1. What is the output of the following code?**
```python
s = {1, 2, 3, 2, 1}
print(len(s))
```
a) 5  
b) 3  
c) 2  
d) Error

**2. Which method adds multiple elements to a set?**
a) `add()`  
b) `append()`  
c) `update()`  
d) `extend()`

**3. What is the time complexity of checking if an element exists in a set?**
a) O(n)  
b) O(log n)  
c) O(1)  
d) O(n²)

**4. Which of the following CANNOT be an element of a set?**
a) Integer  
b) String  
c) List  
d) Tuple

**5. What operator performs set union?**
a) `&`  
b) `|`  
c) `^`  
d) `-`

**6. What is the output?**
```python
s1 = {1, 2, 3}
s2 = {3, 4, 5}
print(s1 & s2)
```
a) `{1, 2, 3, 4, 5}`  
b) `{3}`  
c) `{1, 2, 4, 5}`  
d) Error

**7. How do you create an empty set?**
a) `s = {}`  
b) `s = set()`  
c) `s = []`  
d) `s = ()`

**8. What does `symmetric_difference` return?**
a) Elements common to both sets  
b) Elements in either set but not both  
c) All elements from both sets  
d) Elements in the first set only

**9. Can sets contain duplicate elements?**
a) Yes, always  
b) No, never  
c) Only if specified  
d) Only frozen sets can

**10. What is a frozenset?**
a) A mutable set  
b) An immutable set  
c) A sorted set  
d) A set with only numbers

---

### Coding Exercises

**Exercise 1: Basic Set Operations**
Write a function that takes two lists and returns:
- Elements in both lists
- Elements only in the first list
- Elements only in the second list
- All unique elements from both lists

**Exercise 2: Remove Duplicates**
Create a function that removes duplicates from a list while maintaining the original order (unlike converting to a set).

**Exercise 3: Set Operations**
Given three sets A, B, and C, write a function to find:
- Elements in A but not in B or C
- Elements common to all three sets
- Elements in exactly two of the three sets

**Exercise 4: Word Analysis**
Write a function that takes two sentences and returns:
- Common words in both sentences
- Words unique to each sentence
- Total unique words across both sentences

**Exercise 5: Data Validation**
Create a function that checks if a list of email addresses has:
- Any duplicates
- All unique domains
- The most common domain

---

## Answers

### Multiple Choice Answers
1. **b** - Sets automatically remove duplicates, leaving {1, 2, 3}
2. **c** - `update()` adds multiple elements from an iterable
3. **c** - Set membership testing is O(1) average case
4. **c** - Lists are mutable and cannot be set elements
5. **b** - `|` operator performs union
6. **b** - `&` operator performs intersection, result is {3}
7. **b** - `set()` creates an empty set; `{}` creates a dictionary
8. **b** - Symmetric difference returns elements in either but not both
9. **b** - Sets cannot contain duplicates by definition
10. **b** - Frozensets are immutable versions of sets

### Coding Exercise Solutions

**Solution 1:**
```python
def analyze_lists(list1, list2):
    set1 = set(list1)
    set2 = set(list2)
    
    return {
        'common': list(set1 & set2),
        'only_first': list(set1 - set2),
        'only_second': list(set2 - set1),
        'all_unique': list(set1 | set2)
    }

# Test
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]
print(analyze_lists(list1, list2))
# Output: {'common': [4, 5], 'only_first': [1, 2, 3], 
#          'only_second': [6, 7, 8], 'all_unique': [1, 2, 3, 4, 5, 6, 7, 8]}
```

**Solution 2:**
```python
def remove_duplicates_ordered(lst):
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

# Test
numbers = [1, 2, 2, 3, 1, 4, 5, 3, 5]
print(remove_duplicates_ordered(numbers))  # Output: [1, 2, 3, 4, 5]
```

**Solution 3:**
```python
def three_set_analysis(A, B, C):
    # Elements in A but not in B or C
    only_a = A - B - C
    
    # Elements common to all three
    common_all = A & B & C
    
    # Elements in exactly two sets
    in_ab = (A & B) - C
    in_ac = (A & C) - B
    in_bc = (B & C) - A
    exactly_two = in_ab | in_ac | in_bc
    
    return {
        'only_in_A': only_a,
        'common_to_all': common_all,
        'in_exactly_two': exactly_two
    }

# Test
A = {1, 2, 3, 4, 5}
B = {3, 4, 5, 6, 7}
C = {5, 6, 7, 8, 9}
print(three_set_analysis(A, B, C))
# Output: {'only_in_A': {1, 2}, 'common_to_all': {5}, 
#          'in_exactly_two': {3, 4, 6, 7}}
```

**Solution 4:**
```python
def analyze_sentences(sentence1, sentence2):
    # Convert to lowercase and split into words
    words1 = set(sentence1.lower().split())
    words2 = set(sentence2.lower().split())
    
    return {
        'common_words': words1 & words2,
        'unique_to_first': words1 - words2,
        'unique_to_second': words2 - words1,
        'total_unique': len(words1 | words2)
    }

# Test
s1 = "the quick brown fox jumps over the lazy dog"
s2 = "the lazy cat sleeps on the warm mat"
print(analyze_sentences(s1, s2))
# Output: {'common_words': {'the', 'lazy'}, 
#          'unique_to_first': {'quick', 'brown', 'fox', 'jumps', 'over', 'dog'},
#          'unique_to_second': {'cat', 'sleeps', 'on', 'warm', 'mat'},
#          'total_unique': 14}
```

**Solution 5:**
```python
def validate_emails(emails):
    from collections import Counter
    
    # Check for duplicates
    has_duplicates = len(emails) != len(set(emails))
    
    # Extract domains
    domains = [email.split('@')[1] for email in emails if '@' in email]
    unique_domains = set(domains)
    
    # Most common domain
    domain_counts = Counter(domains)
    most_common = domain_counts.most_common(1)[0] if domain_counts else None
    
    return {
        'has_duplicates': has_duplicates,
        'unique_domains': unique_domains,
        'most_common_domain': most_common
    }

# Test
emails = [
    "user1@gmail.com",
    "user2@yahoo.com",
    "user3@gmail.com",
    "user1@gmail.com",  # duplicate
    "user4@hotmail.com"
]
print(validate_emails(emails))
# Output: {'has_duplicates': True, 
#          'unique_domains': {'gmail.com', 'yahoo.com', 'hotmail.com'},
#          'most_common_domain': ('gmail.com', 3)}
```
