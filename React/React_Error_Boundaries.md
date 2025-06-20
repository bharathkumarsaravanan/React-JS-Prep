# 🧱 React Error Boundaries – With Functional Components

---

## ❓ What Are Error Boundaries?

> A **React component** that catches JavaScript errors in **child components**, logs them, and shows a **fallback UI** instead of crashing the app.

---

## ✅ When Are They Used?

- Rendering errors in child components  
- Lifecycle method errors  
- Errors in constructors of child components

⚠️ **Do not catch:**
- Async errors (`setTimeout`, `fetch`)  
- Event handlers  
- Server-side rendering errors

---

## ❌ Functional Components Can’t Be Error Boundaries Directly

Error Boundaries require lifecycle methods:

- `getDerivedStateFromError`  
- `componentDidCatch`

✅ These are only available in **class components**, not in hooks.

---

## 🛠️ Create a Class-Based Error Boundary

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    console.error("Error caught:", error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h2>Oops! Something broke.</h2>;
    }
    return this.props.children;
  }
}
```

---

## ✅ Wrap Functional Components with ErrorBoundary

```jsx
function BuggyComponent() {
  const [count, setCount] = React.useState(0);

  if (count === 3) {
    throw new Error("Crashed at 3!");
  }

  return <button onClick={() => setCount(c => c + 1)}>Click {count}</button>;
}

function App() {
  return (
    <ErrorBoundary>
      <BuggyComponent />
    </ErrorBoundary>
  );
}
```

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| What is an Error Boundary? | A React component that catches errors in children |
| Can functional components be Error Boundaries? | ❌ No, only class components |
| How do you catch errors in functional components? | Wrap them in a class-based ErrorBoundary |
| What methods must Error Boundaries implement? | `getDerivedStateFromError` and `componentDidCatch` |
| Does it catch async errors or event handlers? | ❌ No, only render/lifecycle/constructor errors |
| Why use them? | Prevent full app crashes, show fallback UI gracefully |
