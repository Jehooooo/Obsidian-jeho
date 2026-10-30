---
tags: [learning, dsa]
topic: Data Structures and Algorithms
category: Computer Science
---

# 📊 Data Structures and Algorithms

## What Is It?

**Data Structures** are ways to organize data (arrays, linked lists, trees, hash maps). **Algorithms** are step-by-step procedures to solve problems (searching, sorting, pathfinding).

Together, they are the **foundation of computer science** and determine how efficient your code is. A program that takes 1 second vs 1 hour to finish often comes down to choosing the right data structure and algorithm.

## Why Is It Important?

- **Technical interviews** — the #1 topic in software engineering interviews
- **Efficient code** — choosing the right structure makes your code faster
- **Problem-solving** — teaches you to think like a programmer
- **CS fundamentals** — required in your degree and career
- **Better software** — understanding DSA helps you build scalable systems

## Syntax / Concepts

### Common Data Structures

| Structure | What It Is | Good For | Python | Time Complexity (Access) |
|-----------|-----------|----------|--------|-------------------------|
| Array/List | Ordered items | Sequential data | `list` | O(1) |
| Dictionary/HashMap | Key-value pairs | Fast lookups | `dict` | O(1) |
| Stack | Last In, First Out | Undo, backtracking | `list` (use append/pop) | O(1) |
| Queue | First In, First Out | Task scheduling | `collections.deque` | O(1) |
| Linked List | Nodes with pointers | Dynamic size | Custom class | O(n) |
| Tree | Hierarchical | File systems, DOM | Custom class | O(log n) |
| Graph | Nodes + edges | Social networks, maps | `dict` of lists | Varies |

### Big O Notation

| Notation | Name | Example |
|----------|------|---------|
| O(1) | Constant | Dictionary lookup |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Loop through a list |
| O(n log n) | Linearithmic | Good sorting (merge sort) |
| O(n²) | Quadratic | Nested loops |
| O(2ⁿ) | Exponential | Brute-force subsets |

### Common Algorithms

```python
# Linear Search — O(n)
def linear_search(items, target):
    for i, item in enumerate(items):
        if item == target:
            return i
    return -1

# Binary Search — O(log n) — list must be sorted!
def binary_search(items, target):
    low, high = 0, len(items) - 1
    while low <= high:
        mid = (low + high) // 2
        if items[mid] == target:
            return mid
        elif items[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1

# Bubble Sort — O(n²) — simple but slow
def bubble_sort(items):
    n = len(items)
    for i in range(n):
        for j in range(0, n - i - 1):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
    return items
```

## Example

```python
# Using a stack to check balanced parentheses
def is_balanced(expression):
    stack = []
    pairs = {')': '(', ']': '[', '}': '{'}
    
    for char in expression:
        if char in '([{':
            stack.append(char)
        elif char in ')]}':
            if not stack or stack[-1] != pairs[char]:
                return False
            stack.pop()
    
    return len(stack) == 0

print(is_balanced("(hello [world])"))  # True
print(is_balanced("(hello [world)"))   # False
```

## Common Mistakes

1. **Off-by-one errors** — loops starting at 0 vs 1, or using `<` vs `<=`
2. **Not considering edge cases** — empty list, single element, duplicate values
3. **Using brute force** — always think if there's a more efficient approach
4. **Forgetting to sort before binary search** — binary search requires sorted data

## Practice

- [ ] Implement linear search and binary search
- [ ] Implement bubble sort and understand why it's O(n²)
- [ ] Use a stack to reverse a string
- [ ] Use a dictionary to count character frequencies in a string
- [ ] Solve 3 easy problems on LeetCode using Python

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Python Data Structures]]
- [[Python Basics]]
- [[Software Engineering]]
- [[Interview Preparation]]
