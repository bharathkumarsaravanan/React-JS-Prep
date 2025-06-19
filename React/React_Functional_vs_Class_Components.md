
# ⚛️ React Component Types – Functional vs Class

---

### 🧩 What is a Component?

A **Component** in React is a **reusable building block** of UI.  
It can be **Functional** or **Class-based**.

---

## ✅ Functional Components

Introduced as stateless, but since React 16.8 they can use **state** and **lifecycle** via **hooks**.

### 🧠 Syntax:

```jsx
function Hello(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

Or with arrow function:

```jsx
const Hello = ({ name }) => <h1>Hello, {name}</h1>;
```

### ✅ Key Points:
- Simpler, cleaner
- Use **hooks** (`useState`, `useEffect`, etc.)
- Recommended for modern React
- Easier to test and read

---

## 🧱 Class Components

Older way to manage state and lifecycle methods.

### 🧠 Syntax:

```jsx
class Hello extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

### ✅ Key Points:
- Must extend `React.Component`
- Need `constructor` for state
- Use lifecycle methods: `componentDidMount`, `shouldComponentUpdate`, etc.
- More boilerplate than functional

---

## 🆚 Key Differences Table

| Feature | Functional Component | Class Component |
|--------|----------------------|------------------|
| Syntax | Function | Class |
| State | `useState()` | `this.state` |
| Side Effects | `useEffect()` | `componentDidMount()`, etc. |
| `this` keyword | ❌ No `this` | ✅ Uses `this` |
| Performance | 🟢 Slightly better | 🟡 Heavier |
| Boilerplate | Less | More |
| Recommended? | ✅ Yes | ⚠️ Legacy usage only |

---

## 🔥 Which One Should You Use?

✅ Use **functional components with hooks** in all new code.  
Class components are still supported but becoming legacy.

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|---------|----------------|
| What’s the difference between functional and class components? | Functional are functions, class components are ES6 classes with state/lifecycle methods |
| Why are functional components preferred now? | They are simpler, use hooks, easier to test and maintain |
| Can you use state in functional components? | Yes, using `useState()` |
| Can you access lifecycle in functional components? | Yes, with `useEffect()` |
| Is `this` used in functional components? | No, `this` is only in class components |
