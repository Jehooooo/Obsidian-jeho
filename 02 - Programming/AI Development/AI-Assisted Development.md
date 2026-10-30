---
tags: [learning, ai]
topic: AI-Assisted Development
category: AI and Tools
---

# 🤖 AI-Assisted Development

## What Is It?

AI-Assisted Development is using **AI tools (like ChatGPT, Gemini, Claude, GitHub Copilot) to help you write, debug, and understand code faster**. It's not about replacing your skills — it's about multiplying them. The AI helps with the tedious parts so you can focus on the creative and architectural decisions.

## Why Is It Important?

- **Your workflow** — you already use AI to build and debug applications
- **Productivity** — build features faster with AI assistance
- **Learning tool** — AI can explain concepts and code in beginner-friendly ways
- **Mayerfeld Practicum** — the practicum focuses on AI-assisted frontend development
- **Industry trend** — more and more companies expect developers to use AI tools

## Syntax / Concepts

### Effective AI Prompting

**Be specific:**
```
❌ Bad: "Fix my code"
✅ Good: "I have a Flask API endpoint that should return a list of users from 
MySQL, but I'm getting a 500 error. Here's my code: [code]. The error 
message says: [error]. What's wrong and how do I fix it?"
```

**Provide context:**
```
✅ Good: "I'm building a React component for my Bayanihan Hub project. 
The component should:
1. Fetch donation items from /api/items
2. Display them in a card grid
3. Show loading and error states
4. Each card shows title, donor, and status

I'm using React with useState and useEffect hooks. 
I'm using Tailwind CSS for styling."
```

**Ask for explanations:**
```
✅ Good: "Explain step by step how this useEffect hook works. 
I'm a beginner and want to understand WHY it works, not just 
copy the code."
```

### AI Workflow for Development

```
1. Plan what you want to build (don't skip this!)
2. Write initial code yourself (build the structure)
3. Use AI to fill in complex parts (specific functions, queries)
4. Ask AI to review your code (find bugs, suggest improvements)
5. ALWAYS read and understand the generated code
6. Test everything (don't trust AI output blindly)
7. Debug with AI help (provide error messages and context)
8. Document what you learned
```

### When to Use AI vs. When to Code Yourself

| Use AI For | Do It Yourself |
|-----------|----------------|
| Boilerplate code | Architecture decisions |
| Complex regex patterns | Understanding the code |
| SQL query optimization | Project planning |
| Debugging error messages | Testing and verification |
| Learning new concepts | Writing commit messages |
| Documentation drafts | Code review judgment |

## Example

A practical AI-assisted debugging session:

```
YOUR PROMPT:
"I'm working on the messaging feature in Bayanihan Hub (React + Flask). 
When a user sends a message, it disappears from the input field but 
doesn't appear in the chat. 

Here's my React component: [paste code]
Here's my Flask endpoint: [paste code]

The browser console shows no errors. The Network tab shows the POST 
request returns 201. But the message doesn't show up in the chat until 
I refresh the page.

What could cause this?"

WHAT TO EXPECT:
The AI should identify that after sending, you need to either:
- Add the new message to your local state
- Re-fetch the messages
- Use optimistic UI updates
```

## How It Works

1. **AI generates code** based on your prompt and context
2. **You review and understand** every line it produces
3. **You test and verify** the code actually works
4. **You adapt and integrate** it into your project
5. **You document** what you learned from the process

## Common Mistakes

1. **Copy-pasting without understanding** — ALWAYS understand what the code does
2. **Not providing enough context** — AI gives better answers with more context
3. **Trusting AI blindly** — AI can generate incorrect or insecure code
4. **Not learning from AI** — use it to learn, not just to get code
5. **Over-depending on AI** — build independent debugging and problem-solving skills

## Debugging Tips

- Always share the **exact error message** with the AI
- Include the **relevant code** (not your entire project)
- Mention your **tech stack** (React, Flask, MySQL, etc.)
- Ask the AI to **explain WHY** the fix works, not just what to change
- Verify the fix makes sense before applying it

## Practice

- [ ] Write a detailed AI prompt for a feature you need to build
- [ ] Practice debugging with AI: give it an error and see if the fix works
- [ ] Ask AI to explain a concept, then write your own explanation
- [ ] Use AI to review your code and identify improvements
- [ ] Build a feature by writing the structure yourself and using AI for specific functions

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[AI Prompts]]
- [[Portfolio]]
- [[Mayerfeld Practicum]]
- [[Python Debugging]]
