---
tags: [learning, python]
topic: Python Basics
category: Programming Languages
---

# 🐍 Python Basics

## What Is It?

Python is a high-level, general-purpose programming language. It's designed to be easy to read and write — almost like writing English. Python is one of the most popular programming languages in the world and is used for web development, data science, automation, AI, and more.

Think of Python as a friendly language that lets you tell the computer what to do without worrying too much about complex syntax.

## Why Is It Important?

- **Beginner-friendly** — easiest language to learn as your first programming language
- **Versatile** — used in web dev (Flask, Django), data science, AI, automation, cybersecurity
- **Huge community** — tons of tutorials, libraries, and help available
- **In-demand** — one of the most requested skills in software engineering jobs
- **Rapid development** — write less code, build things faster

## Syntax / Concepts

### Variables
```python
name = "Jeho"          # String
age = 21               # Integer
gpa = 1.75             # Float
is_student = True      # Boolean
```

### Data Types
```python
str       # Text: "hello"
int       # Whole numbers: 42
float     # Decimal numbers: 3.14
bool      # True or False
list      # Ordered collection: [1, 2, 3]
dict      # Key-value pairs: {"name": "Jeho"}
tuple     # Immutable collection: (1, 2, 3)
set       # Unique values: {1, 2, 3}
```

### Print and Input
```python
print("Hello, World!")
name = input("What is your name? ")
print(f"Hello, {name}!")
```

### Conditionals
```python
age = 18
if age >= 18:
    print("You can vote")
elif age >= 13:
    print("You're a teenager")
else:
    print("You're a kid")
```

### Loops
```python
# For loop
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# While loop
count = 0
while count < 5:
    print(count)
    count += 1

# Loop through a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

## Example

A simple program that tracks donation items (related to Bayanihan Hub):

```python
# Simple donation tracker
donations = []

def add_donation(item, donor):
    donation = {
        "item": item,
        "donor": donor,
        "status": "available"
    }
    donations.append(donation)
    print(f"Added: {item} from {donor}")

def show_donations():
    if not donations:
        print("No donations yet.")
        return
    for i, d in enumerate(donations, 1):
        print(f"{i}. {d['item']} — donated by {d['donor']} [{d['status']}]")

# Usage
add_donation("Laptop", "Jeho")
add_donation("Books", "Maria")
show_donations()
```

## How It Works

1. Python reads your code **top to bottom**, line by line
2. **Variables** store data in memory
3. **Functions** group reusable code together
4. **Indentation** (4 spaces) defines code blocks — this is mandatory in Python!
5. Python is **interpreted** — it runs directly without compiling

## Common Mistakes

1. **Forgetting indentation** — Python uses indentation instead of `{}` brackets. Wrong indentation = error.
2. **Using `=` instead of `==`** — `=` assigns a value, `==` compares values.
3. **Not converting types** — `input()` always returns a string. Use `int()` or `float()` to convert.
4. **Modifying a list while looping** — this causes unexpected behavior. Create a new list instead.
5. **Forgetting `self` in class methods** — every method in a class needs `self` as the first parameter.

## Debugging Tips

- **Read the error message** — Python error messages tell you the file, line number, and what went wrong
- **Use `print()` statements** — print variables to see their values at different points
- **Check types** — use `type(variable)` to see what type a variable is
- **Google the error** — copy the error message and search for it
- **Use a debugger** — VS Code has a built-in Python debugger

## Practice

- [ ] Write a program that asks for your name and age, then prints a greeting
- [ ] Create a list of 5 items and loop through them with a for loop
- [ ] Write a function that takes two numbers and returns their sum
- [ ] Build a simple to-do list program using a list and functions
- [ ] Create a dictionary of your project names and their statuses

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Python OOP]]
- [[Python Data Structures]]
- [[Python Functions]]
- [[Python Debugging]]
- [[Flask Basics]]
