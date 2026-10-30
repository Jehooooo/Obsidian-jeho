---
tags: [react, debugging, ai-prompts, state-management]
topic: React State Debugging
category: Resources / AI Prompts
---

# 🐛 Debug React State Issues

> A comprehensive reference guide, common pitfalls checklist, and reusable AI prompt template for tracking down and fixing React state bugs.

---

## ⚡ The React State Debugging Checklist

When state isn't updating, is updating unexpectedly, or triggers infinite loops, run through these 7 checks:

### 1. Direct Mutation Pitfall (Missing New Reference)
* **Problem:** React uses shallow reference equality (`Object.is`) to detect state changes. Mutating an array or object directly will not trigger a re-render.
* **Incorrect:**
  ```javascript
  // ❌ Modifying original reference
  items.push(newItem);
  setItems(items);
  ```
* **Correct:**
  ```javascript
  // ✅ Creating a new array reference
  setItems(prevItems => [...prevItems, newItem]);
  ```

### 2. Stale Closures in Hooks (`useEffect`, `useCallback`, `setInterval`)
* **Problem:** A function captures state from the render in which it was created. If omitted from dependency arrays, it reads frozen/stale values.
* **Fix:** Use the functional updater form:
  ```javascript
  // ❌ Reads stale 'count'
  setCount(count + 1);

  // ✅ Always gets latest state from React's internal queue
  setCount(prev => prev + 1);
  ```

### 3. Asynchronous Nature & React 18 Batching
* **Problem:** `setState` is asynchronous. You cannot read the updated state immediately on the next line.
* **Incorrect:**
  ```javascript
  setFilter(newFilter);
  fetchData(filter); // ❌ 'filter' is still the old value!
  ```
* **Correct:**
  ```javascript
  setFilter(newFilter);
  fetchData(newFilter); // ✅ Use the local variable directly
  ```

### 4. Infinite Re-Render Loops
* **Problem:** Calling state updates directly inside the component body or inside an effect that depends on the state it updates.
* **Checklist:**
  - Are you passing an arrow function to event handlers? (`onClick={() => handleClick()}` NOT `onClick={handleClick()}`)
  - Does your `useEffect` update a state that is also in its dependency array without an exit condition?

### 5. Derived State Anti-Pattern
* **Problem:** Storing values in state that can be easily calculated during render from props or existing state.
* **Fix:** Calculate inline or wrap with `useMemo`:
  ```javascript
  // ❌ Redundant state synchronization
  // const [fullName, setFullName] = useState('');
  
  // ✅ Derived on the fly
  const fullName = `${firstName} ${lastName}`;
  ```

### 6. Race Conditions in Data Fetching
* **Problem:** User clicks quickly or filters change; an earlier network request finishes *after* a later one, overwriting the UI with outdated data.
* **Fix:** Use an ignore flag or `AbortController`:
  ```javascript
  useEffect(() => {
    let ignore = false;
    
    async function startFetching() {
      const data = await api.getItems(category);
      if (!ignore) {
        setItems(data);
      }
    }
    
    startFetching();
    return () => {
      ignore = true;
    };
  }, [category]);
  ```

---

## 🤖 AI Prompt: Debug React State

Copy and paste this prompt to an AI assistant when debugging complex state problems:

```markdown
I have a state bug in my React component that I need help resolving.

### 1. Tech Stack & Environment
- React Version: [e.g., React 18 / Vite / Next.js]
- State Management: [e.g., useState / useReducer / Context / Zustand]
- Component Name: [e.g., AdminPostFilter.jsx]

### 2. The Expected vs. Actual Behavior
- What I expect to happen: [e.g., Clicking 'Approve' should immediately update the badge count to 1 and remove the item from Pending list]
- What actually happens: [e.g., The item stays on screen until page reload, or counter resets to 0]
- Console Warnings/Errors: [e.g., Warning: Maximum update depth exceeded OR None]

### 3. Relevant Code
```jsx
// [Paste your component code and hook definitions here]
```

### 4. What I've Already Checked
- [ ] Direct object/array mutation checked
- [ ] Dependency array verified
- [ ] Network response returns expected payload (HTTP 200)

### 5. What I Need
1. Pinpoint the exact root cause (stale closure, batching issue, mutation, or re-render cascade).
2. Provide the corrected code snippet.
3. Explain why the issue occurred and how to prevent it.
```

---

## 🔗 Related Notes
- [[React Basics]]
- [[AI Prompts]]
- [[Bayanihan Hub]]
- [[Bayanihan Hub Admin Demo Data Prompt]]