---
tags: [learning, python]
topic: Python Functions
category: Programming Languages
---

# 🐍 Python Functions

## What Is It?

A function is a **reusable block of code** that performs a specific task. Instead of writing the same code over and over, you write it once inside a function and call it whenever you need it. Functions help keep your code organized, readable, and DRY (Don't Repeat Yourself).

## Why Is It Important?

- **Reusability** — write once, use many times
- **Organization** — break big problems into smaller, manageable pieces
- **Readability** — `calculate_total()` is clearer than 10 lines of math
- **Testing** — easier to test small functions than a huge script
- **Collaboration** — team members can work on different functions

## Syntax / Concepts

```python
# Basic function
def greet(name):
    return f"Hello, {name}!"

# Default parameters
def create_user(name, role="Community Member"):
    return {"name": name, "role": role}

# Multiple return values
def get_stats(numbers):
    return min(numbers), max(numbers), sum(numbers) / len(numbers)

# *args and **kwargs
def log(*messages):
    for msg in messages:
        print(f"[LOG] {msg}")

def create_item(**details):
    return details

# Lambda functions (one-line functions)
square = lambda x: x ** 2
```

## Example

```python
# API response handler for a Flask project
def format_response(data, status="success", code=200):
    return {
        "status": status,
        "code": code,
        "data": data
    }

def validate_email(email):
    if "@" not in email or "." not in email:
        return False, "Invalid email format"
    return True, "Email is valid"

# Usage
response = format_response({"user": "Jeho"})
is_valid, message = validate_email("jeho@email.com")
```

## How It Works

1. `def` keyword **defines** the function
2. Parameters go inside the **parentheses**
3. The function body is **indented**
4. `return` sends a value back to the caller
5. You **call** the function by writing its name with parentheses

## Common Mistakes

1. **Forgetting `return`** — without it, the function returns `None`
2. **Mutable default arguments** — never use `def func(items=[])`, use `items=None` instead
3. **Too many parameters** — if a function needs 10+ parameters, refactor it
4. **Not handling edge cases** — always think about what happens with empty inputs

## Debugging Tips

- Print the inputs and outputs of a function to trace data flow
- Use Python's `help(function_name)` to check documentation
- Test functions with simple inputs first before using complex data

## Practice

- [ ] Write a function that validates a password (min 8 chars, has a number, has a letter)
- [ ] Write a function that formats a date string from "2026-09-15" to "September 15, 2026"
- [ ] Create a function that calculates the total price of items in a shopping cart
- [ ] Practice using *args: write a function that accepts any number of project names and prints them
- [ ] Write a decorator function that logs when a function is called

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Python Basics]]
- [[Python OOP]]
- [[Python Debugging]]
- [[Flask Basics]]
