---
tags: [learning, javascript]
topic: JavaScript Basics
category: Programming Languages
---

# 🌐 JavaScript Basics

## What Is It?

JavaScript (JS) is the **programming language of the web**. Every website you visit uses JavaScript to make things interactive — buttons that respond to clicks, forms that validate input, content that updates without refreshing the page. It runs in the browser and (with Node.js) on servers too.

If HTML is the structure of a house and CSS is the paint and decoration, JavaScript is the electricity — it makes things work.

## Why Is It Important?

- **The only language that runs in browsers** — essential for web development
- **Full-stack capable** — frontend (React) and backend (Node.js, Express)
- **Massive ecosystem** — npm has millions of packages
- **Required for React** — your frontend framework of choice
- **Job market** — most in-demand programming language worldwide

## Syntax / Concepts

### Variables
```javascript
let name = "Jeho";          // Can be reassigned
const age = 21;             // Cannot be reassigned
var oldWay = "avoid this";  // Old syntax, don't use

// Use const by default, let when you need to reassign
```

### Data Types
```javascript
"Hello"          // String
42               // Number
true / false     // Boolean
null             // Intentionally empty
undefined        // Not yet assigned
[1, 2, 3]       // Array
{name: "Jeho"}  // Object
```

### Functions
```javascript
// Regular function
function greet(name) {
    return `Hello, ${name}!`;
}

// Arrow function (modern, preferred)
const greet = (name) => `Hello, ${name}!`;

// Arrow function with body
const add = (a, b) => {
    const sum = a + b;
    return sum;
};
```

### Arrays
```javascript
const projects = ["Bayanihan Hub", "Incident System", "Portfolio"];
projects.push("New Project");          // Add to end
projects.filter(p => p.includes("B")); // Filter
projects.map(p => p.toUpperCase());    // Transform each
projects.forEach(p => console.log(p)); // Loop through
```

### Objects
```javascript
const project = {
    name: "Bayanihan Hub",
    status: "In Progress",
    tech: ["React", "Flask"],
    getInfo() {
        return `${this.name} — ${this.status}`;
    }
};
console.log(project.name);
console.log(project.getInfo());
```

### Destructuring
```javascript
const { name, status } = project;       // Object destructuring
const [first, ...rest] = projects;       // Array destructuring
```

### Async/Await (for API calls)
```javascript
const fetchUsers = async () => {
    try {
        const response = await fetch('/api/users');
        const data = await response.json();
        return data;
    } catch (error) {
        console.error("Failed to fetch users:", error);
    }
};
```

## Example

```javascript
// Simple donation item manager
const donations = [];

const addDonation = (item, donor) => {
    donations.push({
        id: donations.length + 1,
        item,
        donor,
        status: "available",
        createdAt: new Date().toISOString()
    });
};

const getAvailable = () => 
    donations.filter(d => d.status === "available");

const claimItem = (id) => {
    const donation = donations.find(d => d.id === id);
    if (donation) {
        donation.status = "claimed";
        return true;
    }
    return false;
};

// Usage
addDonation("Laptop", "Jeho");
addDonation("Books", "Maria");
console.log(getAvailable());
```

## How It Works

1. JavaScript runs in the **browser's JavaScript engine** (V8 in Chrome)
2. It's **event-driven** — it responds to user actions (clicks, typing, scrolling)
3. It's **single-threaded** — but uses **async/await** to handle things like API calls
4. **DOM manipulation** — JS can change the HTML and CSS of a page
5. With **Node.js**, JavaScript can also run on servers

## Common Mistakes

1. **Using `==` instead of `===`** — `==` does type coercion (`"5" == 5` is true), `===` checks type too
2. **Forgetting `async/await`** — API calls return Promises, not data. You need to `await` them
3. **`this` confusion** — `this` works differently in regular vs arrow functions
4. **Not handling errors** — always use try/catch with async code
5. **Mutating state directly** — in React, never modify state directly; use `setState` or `useState`

## Debugging Tips

- **`console.log()`** — your best friend for quick debugging
- **Browser DevTools** — F12 → Console tab shows errors and logs
- **`typeof variable`** — check what type a variable is
- **Network tab** — see API requests and responses in DevTools
- **Breakpoints** — click line numbers in DevTools Sources tab

## Practice

- [ ] Write a function that reverses a string
- [ ] Create an array of objects and use `.filter()`, `.map()`, and `.find()`
- [ ] Write an async function that fetches data from a public API
- [ ] Practice destructuring with objects and arrays
- [ ] Build a simple todo list in the browser console

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[React Basics]]
- [[HTML and CSS]]
- [[REST APIs]]
- [[Flask Basics]]
