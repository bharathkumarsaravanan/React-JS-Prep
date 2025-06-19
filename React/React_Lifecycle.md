# ⚛️ React Lifecycle – Class vs Functional

---

## 🏛️ Class Component Lifecycle

| Phase | Lifecycle Methods | Purpose |
|-------|-------------------|---------|
| 🐣 Mounting | `constructor`<br>`componentDidMount` | Setup state, fetch data |
| 🔄 Updating | `shouldComponentUpdate`<br>`componentDidUpdate` | Control & respond to prop/state changes |
| ⚰️ Unmounting | `componentWillUnmount` | Cleanup timers, listeners, etc. |
| 🐛 Error Handling | `componentDidCatch`<br>`getDerivedStateFromError` | Catch/render errors |

---

### ✅ Example – Class Component

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  componentDidMount() {
    console.log("Mounted");
  }

  componentDidUpdate() {
    console.log("Updated");
  }

  componentWillUnmount() {
    console.log("Will Unmount");
  }

  render() {
    return <p>{this.state.count}</p>;
  }
}
```

---

## ⚛️ Functional Component Lifecycle (with Hooks)

Hooks let you mimic the lifecycle behavior **without classes**.

| Class Lifecycle | Functional Equivalent |
|------------------|------------------------|
| `componentDidMount` | `useEffect(() => {}, [])` |
| `componentDidUpdate` | `useEffect(() => {...}, [dep])` |
| `componentWillUnmount` | `useEffect(() => { return () => {...} }, [])` |

---

### ✅ Example – Functional Version

```jsx
function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Mounted");

    return () => {
      console.log("Will Unmount");
    };
  }, []);

  useEffect(() => {
    console.log("Updated", count);
  }, [count]);

  return <p>{count}</p>;
}
```

---

## 🧠 Key Differences

| Concept | Class Component | Functional Component |
|--------|------------------|----------------------|
| Syntax | Verbose | Concise |
| State | `this.state` | `useState()` |
| Lifecycle | Lifecycle methods | `useEffect()` |
| `this` keyword | Needed | ❌ Not used |
| Code Reuse | Harder | Easier with custom hooks |

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| Can functional components have lifecycle? | ✅ Yes, using `useEffect` |
| How do you mimic `componentDidMount`? | `useEffect(() => {}, [])` |
| What does `componentWillUnmount` become? | Return function inside `useEffect` |
| When should you prefer functional components? | Almost always, unless using legacy code |
| Why are functional components better? | Simpler syntax, no `this`, better reuse via hooks |
