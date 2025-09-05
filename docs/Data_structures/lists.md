# Python Lists

## Introduction
A **list** in Python is a mutable, ordered collection of items. Lists can store elements of different types (integers, strings, objects, etc.).

## Creating Lists
```python
empty_list = []
numbers = [1, 2, 3, 4, 5]
mixed = [1, "apple", 3.14, True]
```

## Accessing Elements
- **Indexing**: `list[index]`
- **Negative Indexing**: `list[-1]` (last element)
- **Slicing**: `list[start:stop:step]`
```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])      # apple
print(fruits[-1])     # cherry
print(fruits[1:3])    # ['banana', 'cherry']
```

## Modifying Lists
- **Change Value**: `list[index] = value`
- **Append**: `list.append(value)`
- **Insert**: `list.insert(index, value)`
- **Extend**: `list.extend([values])`
- **Remove**: `list.remove(value)`
- **Pop**: `list.pop(index)`
- **Clear**: `list.clear()`
```python
numbers = [1, 2, 3]
numbers.append(4)         # [1, 2, 3, 4]
numbers.insert(1, 5)      # [1, 5, 2, 3, 4]
numbers.remove(2)         # [1, 5, 3, 4]
numbers.pop()             # [1, 5, 3]
```

## List Operations
- **Concatenation**: `list1 + list2`
- **Repetition**: `list * n`
- **Membership**: `value in list`
- **Length**: `len(list)`
- **Sorting**: `list.sort()`, `sorted(list)`
- **Reverse**: `list.reverse()`
```python
a = [1, 2]
b = [3, 4]
print(a + b)         # [1, 2, 3, 4]
print(a * 2)         # [1, 2, 1, 2]
print(2 in a)        # True
```

## List Comprehensions
A concise way to create lists.
```python
squares = [x*x for x in range(5)]  # [0, 1, 4, 9, 16]
even = [x for x in range(10) if x % 2 == 0]
```

## Common Built-in Functions
- `len(list)`
- `min(list)`
- `max(list)`
- `sum(list)`
- `list()`

## Nested Lists
Lists can contain other lists.
```python
matrix = [[1, 2], [3, 4], [5, 6]]
print(matrix[1][0])  # 3
```

## Interview Questions
1. What is the difference between a list and a tuple in Python?
2. How do you remove duplicates from a list?
3. How do you reverse a list?
4. How do you find the index of an element in a list?
5. How do you sort a list of dictionaries by a key?

## Most Asked Interview Problems
- **Find the second largest element in a list**
- **Remove duplicates from a list**
- **Reverse a list in-place**
- **Find all pairs in a list that sum to a specific value**
- **Flatten a nested list**
- **Rotate a list by k elements**
- **Find the frequency of elements in a list**

## Additional Tips
- Lists are mutable; changes affect the original list.
- Use list comprehensions for cleaner, faster code.
- For large data, consider using `collections.deque` for faster append/pop operations.
- Lists can be used to implement stacks and queues.

## References
- [Python Official Documentation - Lists](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
- [Real Python - Lists and Tuples](https://realpython.com/python-lists-tuples/)

## Multiple Choice Questions on Python Lists

### Questions

1. What is the correct way to create an empty list in Python?
    - a) `list = ()`
    - b) `list = []`
    - c) `list = {}`
    - d) `list = ""`

2. Which method adds an element to the end of a list?
    - a) `add()`
    - b) `insert()`
    - c) `append()`
    - d) `extend()`

3. What is the output of `len([1, 2, 3, 4])`?
    - a) 3
    - b) 4
    - c) 5
    - d) Error

4. How do you access the last element of a list `a`?
    - a) `a[last]`
    - b) `a[-1]`
    - c) `a[len(a)]`
    - d) `a[0]`

5. Which of the following is NOT a valid list operation?
    - a) `list1 + list2`
    - b) `list1 * 2`
    - c) `list1 / 2`
    - d) `list1.append(5)`

6. What does `list.pop()` do?
    - a) Removes the first element
    - b) Removes the last element
    - c) Removes all elements
    - d) Adds an element

7. How do you reverse a list `a` in-place?
    - a) `a.reverse()`
    - b) `reverse(a)`
    - c) `a = a[::-1]`
    - d) `a.sort(reverse=True)`

8. Which function returns a sorted copy of a list?
    - a) `sort(list)`
    - b) `list.sort()`
    - c) `sorted(list)`
    - d) `list.reverse()`

9. What is the output of `[1, 2, 3] * 2`?
    - a) `[2, 4, 6]`
    - b) `[1, 2, 3, 1, 2, 3]`
    - c) `[1, 2, 3, 2]`
    - d) `[1, 1, 2, 2, 3, 3]`

10. How do you remove all elements from a list?
    - a) `list.remove()`
    - b) `list.clear()`
    - c) `del list`
    - d) `list.pop()`

11. Which method inserts an element at a specific index?
    - a) `append()`
    - b) `insert()`
    - c) `extend()`
    - d) `add()`

12. What is the result of `list(range(3))`?
    - a) `[1, 2, 3]`
    - b) `[0, 1, 2]`
    - c) `[0, 1, 2, 3]`
    - d) `[3, 2, 1]`

13. Which of the following creates a nested list?
    - a) `[1, 2, 3]`
    - b) `[[1, 2], [3, 4]]`
    - c) `[1, [2, 3]]`
    - d) Both b and c

14. What does `list.remove(2)` do?
    - a) Removes the element at index 2
    - b) Removes the first occurrence of value 2
    - c) Removes all occurrences of value 2
    - d) Removes the last element

15. Which statement checks if 5 is in the list `a`?
    - a) `5 in a`
    - b) `a.has(5)`
    - c) `a.contains(5)`
    - d) `a[5]`

16. What is the output of `sum([1, 2, 3])`?
    - a) 6
    - b) 5
    - c) 3
    - d) Error

17. How do you copy a list `a`?
    - a) `a.copy()`
    - b) `copy(a)`
    - c) `a[:]`
    - d) Both a and c

18. Which method adds multiple elements to a list?
    - a) `append()`
    - b) `extend()`
    - c) `insert()`
    - d) `add()`

19. What is the output of `[x for x in range(5) if x % 2 == 0]`?
    - a) `[0, 2, 4]`
    - b) `[1, 3, 5]`
    - c) `[2, 4, 6]`
    - d) `[0, 1, 2, 3, 4]`

20. Which statement flattens a nested list `[[1, 2], [3, 4]]`?
    - a) `[item for sublist in l for item in sublist]`
    - b) `l.flatten()`
    - c) `l.flat()`
    - d) `l.extend()`

### Answers

1. b  
2. c  
3. b  
4. b  
5. c  
6. b  
7. a  
8. c  
9. b  
10. b  
11. b  
12. b  
13. d  
14. b  
15. a  
16. a  
17. d  
18. b  
19. a  
20. a  