# ⚛️ React Performance – Memoization & Re-renders

---

## 🔄 How React Re-renders Work

React **re-renders** a component when:
- Its **state** changes
- Its **props** change
- Its **parent** re-renders (and passes new or same props)

✅ Re-render ≠ DOM update (React may skip the actual DOM update using Virtual DOM diffing)

---

## 🚨 Problem: Unnecessary Re-renders

- Child components re-render **even if props haven’t changed**
- Causes performance drops in large apps or complex trees

---

## 🧠 What Is Memoization?

> Memoization is caching the result of a function or component to avoid re-computation.

---

## 🧩 Key Tools to Optimize Re-renders

### 1️⃣ `React.memo()`

Wraps a functional component to **prevent re-render** if props didn’t change.

```jsx
const MyComponent = React.memo(function MyComponent({ name }) {
  return <p>{name}</p>;
});
```

✅ React compares old vs new props (shallow compare). If no change → skips re-render.

---

### 2️⃣ `useMemo()`

Caches a **computed value** between renders unless dependencies change.

```jsx
const expensiveValue = useMemo(() => computeHeavyStuff(a, b), [a, b]);
```

✅ Prevents recalculating on every render

---

### 3️⃣ `useCallback()`

Memoizes a **function** so it doesn't change on every render.

```jsx
const handleClick = useCallback(() => doSomething(), []);
```

✅ Use it when passing functions as props to avoid triggering child re-renders.

---

### 4️⃣ `useRef()`

Stores **mutable values** that don’t trigger re-renders.  
Great for tracking things across renders (like timers, previous props, DOM refs).

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| Why do components re-render? | When state or props change, or parent re-renders |
| How to avoid unnecessary re-renders? | Use `React.memo`, `useMemo`, `useCallback` |
| What does `React.memo` do? | Skips re-render if props haven’t changed |
| When to use `useMemo`? | For expensive calculations |
| When to use `useCallback`? | When passing functions to children |
| Does `useRef` cause re-renders? | ❌ No, it's a mutable reference |
