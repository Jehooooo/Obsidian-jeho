---
tags: [learning, python]
topic: Python Debugging
category: Programming Languages
---

# 🐍 Python Debugging

## What Is It?

Debugging is the process of **finding and fixing errors** in your code. Bugs are mistakes that cause your program to crash, produce wrong results, or behave unexpectedly. Debugging is one of the most important skills a developer can have — you'll spend almost as much time debugging as writing new code.

## Why Is It Important?

- **Every developer debugs constantly** — it's a core part of the job
- **Saves time** — systematic debugging is faster than random guessing
- **Builds understanding** — debugging teaches you how code actually works
- **Independence** — good debugging skills mean you can solve problems without always asking for help
- **Career skill** — employers value developers who can troubleshoot effectively

## Syntax / Concepts

### Types of Errors

**1. Syntax Errors** — Python can't understand your code
```python
# Missing colon
if True
    print("hello")  # SyntaxError: expected ':'
```

**2. Runtime Errors** — Code crashes while running
```python
numbers = [1, 2, 3]
print(numbers[5])  # IndexError: list index out of range
```

**3. Logic Errors** — Code runs but gives wrong results
```python
# Bug: should be (a + b) / 2, not a + b / 2
def average(a, b):
    return a + b / 2  # Wrong! This does a + (b/2)
```

### Debugging Tools

```python
# 1. Print debugging
print(f"DEBUG: variable = {variable}")
print(f"DEBUG: type = {type(variable)}")

# 2. Try/except
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Error: {e}")

# 3. Breakpoint (Python 3.7+)
breakpoint()  # Opens interactive debugger

# 4. Logging (better than print for real projects)
import logging
logging.basicConfig(level=logging.DEBUG)
logging.debug(f"Processing item: {item}")
```

## Example

```python
# Common debugging scenario in a Flask API
def get_user_by_id(user_id):
    # Step 1: Check input
    print(f"DEBUG: user_id = {user_id}, type = {type(user_id)}")
    
    # Step 2: Check database query
    try:
        user = db.execute("SELECT * FROM users WHERE id = ?", (user_id,))
        print(f"DEBUG: query result = {user}")
    except Exception as e:
        print(f"DEBUG: Database error = {e}")
        return None
    
    # Step 3: Check output
    if user is None:
        print(f"DEBUG: No user found with id {user_id}")
    
    return user
```

## How It Works

**The Debugging Process:**
1. **Reproduce** — make the bug happen consistently
2. **Isolate** — find exactly which line/function causes the issue
3. **Understand** — figure out WHY it's happening
4. **Fix** — change the code to correct the behavior
5. **Test** — verify the fix works and doesn't break anything else
6. **Document** — write down what the bug was and how you fixed it

## Common Mistakes

1. **Not reading the error message** — Python tells you exactly what went wrong and where
2. **Changing random things** — don't guess; understand the problem first
3. **Not testing after fixing** — always verify your fix actually works
4. **Ignoring edge cases** — test with empty inputs, None, zero, very large values
5. **Over-relying on AI** — use AI to help, but understand the fix yourself

## Debugging Tips

- **Read the full traceback** — start from the bottom, it shows the actual error
- **Rubber duck debugging** — explain the problem out loud (even to yourself)
- **Binary search debugging** — comment out half the code to find which half has the bug
- **Check recent changes** — what did you change last? That's probably where the bug is
- **Use VS Code debugger** — set breakpoints and step through code line by line

## Practice

- [ ] Intentionally create a syntax error, runtime error, and logic error — then fix each one
- [ ] Practice reading Python tracebacks: find the file, line number, and error type
- [ ] Debug a function that should calculate averages but gives wrong results
- [ ] Use try/except to handle a file-not-found error gracefully
- [ ] Use VS Code's debugger to step through a function line by line

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Python Basics]]
- [[Python Functions]]
- [[Flask Basics]]
