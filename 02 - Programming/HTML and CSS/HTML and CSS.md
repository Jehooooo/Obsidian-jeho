---
tags: [learning, html, css]
topic: HTML and CSS
category: Frontend Development
---

# 🎨 HTML and CSS

## What Is It?

**HTML (HyperText Markup Language)** defines the **structure** of a web page — headings, paragraphs, images, forms, buttons. It's the skeleton of every website.

**CSS (Cascading Style Sheets)** defines the **appearance** — colors, fonts, layouts, spacing, animations. It's the skin and clothes.

Together, they create the visual web pages you see every day.

## Why Is It Important?

- **Foundation of web development** — every website uses HTML and CSS
- **Required for React** — JSX is basically HTML inside JavaScript
- **UI/UX skills** — understanding layout and styling is essential
- **Responsive design** — making websites work on all screen sizes
- **Your projects need it** — Tailwind CSS (used in your projects) is built on CSS

## Syntax / Concepts

### HTML Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bayanihan Hub</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <nav>
            <a href="/">Home</a>
            <a href="/donations">Donations</a>
        </nav>
    </header>
    <main>
        <h1>Welcome to Bayanihan Hub</h1>
        <p>A community platform for sharing and helping.</p>
    </main>
    <footer>
        <p>&copy; 2026 Bayanihan Hub</p>
    </footer>
</body>
</html>
```

### Semantic HTML
```html
<!-- Use meaningful tags, not just <div> everywhere -->
<header>    <!-- Page header / navigation -->
<nav>       <!-- Navigation links -->
<main>      <!-- Main content -->
<section>   <!-- Thematic grouping -->
<article>   <!-- Self-contained content -->
<aside>     <!-- Sidebar content -->
<footer>    <!-- Page footer -->
<form>      <!-- User input form -->
```

### CSS Fundamentals
```css
/* Selectors */
h1 { color: purple; }                /* Element */
.card { padding: 16px; }             /* Class */
#hero { background: black; }         /* ID */
.card:hover { transform: scale(1.02); }  /* Pseudo-class */

/* Box Model */
.box {
    margin: 16px;      /* Outside spacing */
    padding: 16px;     /* Inside spacing */
    border: 1px solid #333;
    width: 300px;
}

/* Flexbox (most useful layout tool) */
.container {
    display: flex;
    justify-content: space-between;  /* Horizontal alignment */
    align-items: center;             /* Vertical alignment */
    gap: 16px;                       /* Space between items */
}

/* CSS Grid (for complex layouts) */
.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
}

/* Responsive Design */
@media (max-width: 768px) {
    .grid {
        grid-template-columns: 1fr;  /* Stack on mobile */
    }
}
```

## Example

```css
/* Dark theme card component (purple accent) */
.donation-card {
    background: rgba(30, 30, 30, 0.9);
    border: 1px solid rgba(128, 0, 255, 0.3);
    border-radius: 12px;
    padding: 20px;
    color: #e0e0e0;
    transition: transform 0.2s, border-color 0.2s;
}

.donation-card:hover {
    transform: translateY(-2px);
    border-color: rgba(128, 0, 255, 0.6);
}

.donation-card h3 {
    color: #b366ff;
    margin-bottom: 8px;
}

.donation-card .status {
    display: inline-block;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.85rem;
    background: rgba(128, 0, 255, 0.2);
    color: #b366ff;
}
```

## Common Mistakes

1. **Using `<div>` for everything** — use semantic HTML tags
2. **Not making it responsive** — always test on mobile screen sizes
3. **Inline styles** — use CSS classes instead of `style="..."` attributes
4. **Not using Flexbox/Grid** — don't use floats or absolute positioning for layouts
5. **Forgetting the viewport meta tag** — mobile browsers won't scale properly without it

## Practice

- [ ] Build a simple page with header, main content, and footer using semantic HTML
- [ ] Style a card component with CSS (dark theme, purple accent)
- [ ] Create a responsive navigation bar using Flexbox
- [ ] Build a 3-column grid layout that stacks on mobile
- [ ] Create a form with proper labels and styling

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[JavaScript Basics]]
- [[React Basics]]
- [[Software Engineering]]
