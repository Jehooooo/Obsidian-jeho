---
tags: [learning, python]
topic: Python Data Structures
category: Programming Languages
---

# 🐍 Python Data Structures

## What Is It?

Data structures are ways to **organize and store data** so you can use it efficiently. Python has several built-in data structures, each designed for different use cases. Choosing the right data structure is one of the most important skills in programming.

## Why Is It Important?

- **Performance** — the right data structure makes your code faster
- **Organization** — keeps your data structured and accessible
- **Problem-solving** — many coding problems are really about choosing the right data structure
- **Interviews** — data structures are heavily tested in technical interviews

## Syntax / Concepts

### Lists — Ordered, Mutable Collection
```python
projects = ["Bayanihan Hub", "Incident System", "Portfolio"]
projects.append("New Project")     # Add to end
projects.insert(0, "First")       # Insert at index
projects.remove("First")          # Remove by value
print(projects[0])                # Access by index
print(len(projects))              # Length
```

### Dictionaries — Key-Value Pairs
```python
project = {
    "name": "Bayanihan Hub",
    "status": "In Progress",
    "tech": ["React", "Flask", "MySQL"]
}
print(project["name"])            # Access by key
project["deadline"] = "2026-12-01"  # Add new key
```

### Tuples — Ordered, Immutable Collection
```python
coordinates = (14.5995, 120.9842)  # Can't modify after creation
lat, lng = coordinates              # Tuple unpacking
```

### Sets — Unique, Unordered Values
```python
skills = {"Python", "React", "Flask", "Python"}  # Duplicates removed
print(skills)  # {"Python", "React", "Flask"}
skills.add("MySQL")
```

### List Comprehensions — Create Lists in One Line
```python
numbers = [1, 2, 3, 4, 5]
squares = [n ** 2 for n in numbers]           # [1, 4, 9, 16, 25]
evens = [n for n in numbers if n % 2 == 0]    # [2, 4]
```

## Example

```python
# Bug tracker using dictionaries and lists
bugs = []

def add_bug(title, project, priority="Medium"):
    bug = {
        "title": title,
        "project": project,
        "priority": priority,
        "status": "Open"
    }
    bugs.append(bug)

def get_open_bugs():
    return [b for b in bugs if b["status"] == "Open"]

def fix_bug(title):
    for bug in bugs:
        if bug["title"] == title:
            bug["status"] = "Fixed"
            return True
    return False

# Usage
add_bug("Messages disappearing", "Bayanihan Hub", "High")
add_bug("Responsive layout broken", "Bayanihan Hub", "Medium")
print(f"Open bugs: {len(get_open_bugs())}")
```

## How It Works

| Structure | Ordered? | Mutable? | Duplicates? | Use Case |
|-----------|----------|----------|-------------|----------|
| List | ✅ | ✅ | ✅ | General collections |
| Dictionary | ✅* | ✅ | Keys: ❌ | Lookup by key |
| Tuple | ✅ | ❌ | ✅ | Fixed data |
| Set | ❌ | ✅ | ❌ | Unique values |

*Dictionaries maintain insertion order in Python 3.7+

## Common Mistakes

1. **Using a list when you need a dictionary** — if you're searching by a key, use a dict
2. **Modifying a list while iterating** — creates bugs; use list comprehension instead
3. **Forgetting that dictionaries need unique keys** — duplicate keys overwrite previous values
4. **Using mutable objects as dictionary keys** — only use strings, numbers, or tuples as keys

## Debugging Tips

- Use `print(type(variable))` to verify the data type
- Use `print(len(collection))` to check size
- Use `"key" in dictionary` to check if a key exists before accessing it

## Practice

- [ ] Create a dictionary representing a user profile with name, email, role
- [ ] Write a function that counts how many items are in each category (using a dictionary)
- [ ] Practice list comprehensions: filter a list of numbers to only even numbers
- [ ] Use a set to find unique technologies across all your projects
- [ ] Build a simple contact book using a list of dictionaries

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Python Basics]]
- [[Python Functions]]
- [[Data Structures and Algorithms]]
