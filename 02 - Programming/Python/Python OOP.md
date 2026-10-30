---
tags: [learning, python]
topic: Python OOP
category: Programming Languages
---

# 🐍 Python OOP (Object-Oriented Programming)

## What Is It?

OOP is a way of organizing your code by creating **objects** — things that have both data (attributes) and actions (methods). Instead of writing a bunch of loose functions and variables, you group related code together into **classes**.

Think of it like a blueprint. A class is the blueprint, and an object is the actual thing built from that blueprint. For example, a `User` class is the blueprint, and `jeho_account` is one specific user built from it.

## Why Is It Important?

- **Organizes code** — keeps related data and functions together
- **Reusable** — write a class once, create many objects from it
- **Maintainable** — easier to update and debug large projects
- **Real-world modeling** — software objects mirror real-world things (users, products, incidents)
- **Used everywhere** — Java, Python, JavaScript, C# all use OOP

## Syntax / Concepts

### Classes and Objects
```python
class User:
    def __init__(self, name, email):
        self.name = name      # attribute
        self.email = email    # attribute
    
    def greet(self):          # method
        return f"Hello, I'm {self.name}!"

# Create an object (instance)
jeho = User("Jeho", "jeho@example.com")
print(jeho.greet())  # "Hello, I'm Jeho!"
```

### The Four Pillars of OOP

**1. Encapsulation** — Hide internal details, expose only what's needed
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # private attribute (double underscore)
    
    def deposit(self, amount):
        self.__balance += amount
    
    def get_balance(self):
        return self.__balance
```

**2. Inheritance** — Create new classes based on existing ones
```python
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):  # Student inherits from Person
    def __init__(self, name, student_id):
        super().__init__(name)  # call parent's __init__
        self.student_id = student_id
```

**3. Polymorphism** — Same method name, different behavior
```python
class Dog:
    def speak(self):
        return "Woof!"

class Cat:
    def speak(self):
        return "Meow!"

animals = [Dog(), Cat()]
for animal in animals:
    print(animal.speak())  # Each animal speaks differently
```

**4. Abstraction** — Show only essential features, hide complexity
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
```

## Example

A practical example related to the Incident Monitoring System:

```python
class Incident:
    VALID_STATUSES = ["Pending", "In Progress", "Solved"]
    
    def __init__(self, title, location, cause, reporter):
        self.title = title
        self.location = location
        self.cause = cause
        self.reporter = reporter
        self.status = "Pending"
        self.notes = []
    
    def update_status(self, new_status):
        if new_status in self.VALID_STATUSES:
            self.status = new_status
            return f"Status updated to {new_status}"
        return "Invalid status"
    
    def add_note(self, note):
        self.notes.append(note)
    
    def __str__(self):
        return f"[{self.status}] {self.title} at {self.location}"

# Usage
incident = Incident("Flooding", "Main Building", "Heavy Rain", "Jeho")
print(incident)                              # [Pending] Flooding at Main Building
incident.update_status("In Progress")
incident.add_note("Evacuation started")
```

## How It Works

1. You **define a class** with `class ClassName:`
2. `__init__` is the **constructor** — it runs when you create a new object
3. `self` refers to **the specific object** being created or used
4. You create objects by **calling the class** like a function: `obj = ClassName()`
5. Objects have **attributes** (data) and **methods** (actions)

## Common Mistakes

1. **Forgetting `self`** — every method needs `self` as its first parameter
2. **Not calling `super().__init__()`** — when inheriting, you must initialize the parent class
3. **Confusing class vs instance variables** — class variables are shared by all instances
4. **Overcomplicating inheritance** — don't create deep inheritance hierarchies; prefer composition

## Debugging Tips

- Use `print(type(obj))` to check what class an object belongs to
- Use `print(vars(obj))` to see all attributes of an object
- Use `isinstance(obj, ClassName)` to check if an object is of a certain type

## Practice

- [ ] Create a `Student` class with name, course, and year attributes
- [ ] Add a method that returns a formatted introduction string
- [ ] Create a `DonationItem` class for the Bayanihan Hub project
- [ ] Practice inheritance: create `Admin` and `CommunityMember` classes that inherit from `User`
- [ ] Build a simple inventory system using OOP

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Python Basics]]
- [[Python Data Structures]]
- [[Java OOP]]
- [[Software Engineering]]
