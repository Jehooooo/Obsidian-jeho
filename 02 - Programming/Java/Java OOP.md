---
tags: [learning, java]
topic: Java OOP
category: Programming Languages
---

# ☕ Java OOP (Object-Oriented Programming)

## What Is It?

Java is a **strongly-typed, object-oriented programming language**. Unlike Python where OOP is optional, in Java **everything** lives inside a class. Java is one of the most widely used languages in enterprise software, Android development, and large-scale systems.

OOP in Java follows the same four pillars as Python (Encapsulation, Inheritance, Polymorphism, Abstraction) but with stricter syntax and type checking.

## Why Is It Important?

- **Enterprise standard** — used by banks, governments, large corporations
- **Android development** — traditional language for Android apps
- **Strong typing** — catches errors at compile time, before your code even runs
- **Career opportunities** — huge demand for Java developers
- **CS fundamentals** — teaches you proper OOP discipline

## Syntax / Concepts

### Classes and Objects
```java
public class User {
    // Attributes (fields)
    private String name;
    private String email;
    private String role;
    
    // Constructor
    public User(String name, String email) {
        this.name = name;
        this.email = email;
        this.role = "Community Member";
    }
    
    // Methods
    public String greet() {
        return "Hello, I'm " + this.name + "!";
    }
    
    // Getters and Setters
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}

// Usage
User jeho = new User("Jeho", "jeho@email.com");
System.out.println(jeho.greet());
```

### Inheritance
```java
public class Admin extends User {
    private String department;
    
    public Admin(String name, String email, String department) {
        super(name, email);  // Call parent constructor
        this.department = department;
    }
    
    public void manageUsers() {
        System.out.println("Managing users...");
    }
}
```

### Interfaces
```java
public interface Reportable {
    String generateReport();
    void exportPDF();
}

public class Incident implements Reportable {
    @Override
    public String generateReport() {
        return "Incident Report...";
    }
    
    @Override
    public void exportPDF() {
        // PDF generation logic
    }
}
```

## Example

```java
// Simple incident class for the monitoring system
public class Incident {
    private String title;
    private String location;
    private String status;
    
    public Incident(String title, String location) {
        this.title = title;
        this.location = location;
        this.status = "Pending";
    }
    
    public void updateStatus(String newStatus) {
        String[] validStatuses = {"Pending", "In Progress", "Solved"};
        for (String valid : validStatuses) {
            if (valid.equals(newStatus)) {
                this.status = newStatus;
                System.out.println("Status updated to: " + newStatus);
                return;
            }
        }
        System.out.println("Invalid status!");
    }
    
    @Override
    public String toString() {
        return "[" + status + "] " + title + " at " + location;
    }
}
```

## How It Works

1. Everything in Java lives inside a **class**
2. You must **declare the type** of every variable (`String name`, `int age`)
3. Code is **compiled** before running (unlike Python which is interpreted)
4. `public`, `private`, `protected` control **access levels**
5. Java uses **garbage collection** to manage memory automatically

## Common Mistakes

1. **Forgetting semicolons** — every statement ends with `;`
2. **Using `==` for strings** — use `.equals()` to compare strings in Java
3. **NullPointerException** — accessing a method on a null object
4. **Forgetting `new`** — `User jeho = new User()` (not just `User()`)
5. **Not handling exceptions** — use try/catch for risky operations

## Debugging Tips

- Read the **stack trace** — it shows you the exact line that crashed
- Use `System.out.println()` for quick debugging
- Use your IDE's debugger (IntelliJ, Eclipse, VS Code) for breakpoints
- Check for `null` before calling methods on objects

## Practice

- [ ] Create a `Student` class with name, course, year, and a `toString()` method
- [ ] Practice inheritance: create `Admin` and `Staff` classes extending `User`
- [ ] Create an interface `Printable` with a `print()` method and implement it
- [ ] Build a simple ArrayList-based task manager
- [ ] Write a class with proper getters, setters, and constructor overloading

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Java Swing]]
- [[Python OOP]]
- [[Software Engineering]]
- [[Data Structures and Algorithms]]
