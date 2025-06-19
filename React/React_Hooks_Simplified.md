
# ⚛️ React Hooks – Simplified Guide

---

## 🧠 What are Hooks?

Hooks are special functions that let you “hook into” React features **without writing a class**.  
They work only in **functional components**.

---

## 1️⃣ `useState` – For State

Lets you create local state in a function component.

```jsx
const [count, setCount] = useState(0);
```

### ✅ How it works:
- `count` is the current value.
- `setCount` updates it.
- Changing state re-renders the component.

---

## 2️⃣ `useEffect` – For Side Effects

Runs code **after render**: like fetching data, timers, DOM updates.

```jsx
useEffect(() => {
  console.log("Component mounted or updated");
}, []);
```

### ✅ Variants:
| Dependency Array | When it runs |
|------------------|---------------|
| `[]` | Once (on mount) |
| `[someVar]` | When `someVar` changes |
| _No array_ | After every render |

---

## 3️⃣ `useRef` – For Persistent Values or DOM Refs

Stores a value that doesn't cause re-render. Also accesses DOM nodes.

```jsx
const inputRef = useRef(null);

useEffect(() => {
  inputRef.current.focus();
}, []);
```

### ✅ Use Cases:
- Focus inputs
- Store timers
- Keep previous state value

---

## 4️⃣ `useMemo` – For Expensive Calculations

Memorizes a **value** to avoid recalculating on every render.

```jsx
const expensiveValue = useMemo(() => computeSomething(a, b), [a, b]);
```

✅ Recomputes only when `a` or `b` change.

---

## 5️⃣ `useCallback` – For Memoizing Functions

Memorizes a **function** to avoid re-creating it unnecessarily (great for child components).

```jsx
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

✅ Same function reference between renders unless dependencies change.

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|---------|----------------|
| Why use `useState`? | To store local state in a functional component |
| When does `useEffect` run? | After render (based on dependencies) |
| What is `useRef` used for? | Storing mutable values or accessing DOM elements |
| What is `useMemo`? | Prevents expensive recalculations |
| When to use `useCallback`? | To memoize functions and prevent re-renders |
