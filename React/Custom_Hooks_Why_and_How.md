# ⚛️ Custom Hooks – Why and How

---

## 🧠 What is a Custom Hook?

A **Custom Hook** is just a **function that starts with `use`** and uses one or more built-in hooks (`useState`, `useEffect`, etc.).

> ✅ Purpose: **Reuse stateful logic** across components.

---

## ✅ Why Use Custom Hooks?

| Benefit | Explanation |
|--------|-------------|
| 🧼 Clean code | Separate logic from UI |
| ♻️ Reusable | Share logic between components |
| 🚫 Avoid duplication | No repeated `useState`, `useEffect` logic |
| 📦 Composable | You can use other hooks inside custom hooks |

---

## 🧪 Syntax: How to Write a Custom Hook

```jsx
// useWindowWidth.js
import { useState, useEffect } from "react";

function useWindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    const handleResize = () => setWidth(window.innerWidth);
    window.addEventListener("resize", handleResize);

    return () => window.removeEventListener("resize", handleResize);
  }, []);

  return width;
}
export default useWindowWidth;
```

### ✅ Usage:

```jsx
import useWindowWidth from "./useWindowWidth";

function MyComponent() {
  const width = useWindowWidth();
  return <p>Window width: {width}</p>;
}
```

---

## 🧪 Another Example: useFetch

```jsx
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(data => {
        setData(data);
        setLoading(false);
      });
  }, [url]);

  return { data, loading };
}
```

---

## ⚠️ Rules for Custom Hooks

- ✅ Must start with `use`
- ✅ Can use other hooks inside
- ❌ Never call them inside loops or conditions
- ✅ Should return state, functions, or values

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| What is a custom hook? | A reusable function that uses React hooks |
| Why use custom hooks? | To reuse logic, clean up code, separate concerns |
| Can custom hooks call other hooks? | ✅ Yes |
| Where should custom hooks be called? | Inside functional components or other hooks |
| Do custom hooks render UI? | ❌ No, only return logic or data |
