# 🧩 Code Splitting & Lazy Loading in React

---

## 🔍 What is Code Splitting?

> Breaking your large React bundle into **smaller chunks** so that only what's needed is loaded upfront.

### ✅ Why use it?

- Reduce **initial load time**  
- Improve **performance**  
- Helps with **per-route/component loading**

---

## 🚀 How to Code Split in React?

React supports **lazy loading** using:

- `React.lazy()`  
- `Suspense`

---

## 📦 `React.lazy()`

> Dynamically load a component **only when it's rendered**

### 🔧 Example:

```jsx
import React, { Suspense } from 'react';

const LazyComponent = React.lazy(() => import('./MyComponent'));

function App() {
  return (
    <Suspense fallback={<p>Loading...</p>}>
      <LazyComponent />
    </Suspense>
  );
}
```

---

## ⏳ `Suspense` for Fallback UI

> `Suspense` shows a **fallback UI** while the lazy component loads.

### 📌 Best used with:

- Page-level components  
- Routes

---

## 📁 Example with React Router

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
const About = React.lazy(() => import("./About"));

function App() {
  return (
    <BrowserRouter>
      <Suspense fallback={<p>Loading page...</p>}>
        <Routes>
          <Route path="/about" element={<About />} />
        </Routes>
      </Suspense>
    </BrowserRouter>
  );
}
```

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| What is code splitting? | Breaking app into smaller JS chunks |
| Why use lazy loading? | Improves initial page load speed |
| How do you implement lazy loading? | With `React.lazy()` and `Suspense` |
| What does `Suspense` do? | Renders a fallback while lazy component loads |
| Is code splitting automatic in React? | No, you have to implement it manually |
| Where should you lazy-load? | Routes, heavy components, rarely-used features |
