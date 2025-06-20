
# 📝 Forms in React – Controlled vs Uncontrolled

---

## ✅ Controlled Components

> Form inputs where **React state controls the input value**.

### 🔧 Characteristics:

- Input value is **tied to component state**
- Updated via `onChange`
- React is **always in sync** with input value

### ✅ Example:

```jsx
function ControlledForm() {
  const [name, setName] = useState("");

  return (
    <input
      value={name}
      onChange={(e) => setName(e.target.value)}
    />
  );
}
```

✅ **React is the source of truth**

---

## ❌ Uncontrolled Components

> Form inputs where the **DOM itself controls the value**.

### 🔧 Characteristics:

- Use `ref` to **access the value**
- React doesn’t track changes
- Useful for quick forms or non-critical inputs

### ✅ Example:

```jsx
function UncontrolledForm() {
  const inputRef = useRef();

  const handleSubmit = () => {
    alert(inputRef.current.value);
  };

  return <input ref={inputRef} />;
}
```

✅ **DOM is the source of truth**

---

## 🆚 Controlled vs Uncontrolled – Comparison

| Feature           | Controlled          | Uncontrolled       |
|------------------|----------------------|---------------------|
| Data handled by  | React state          | DOM (`ref`)         |
| Update on change | `onChange` event     | `ref.current.value` |
| Validation       | Easy (via state)     | Manual              |
| Initial value    | `useState`           | `defaultValue`      |
| Use case         | Complex/validated forms | Simple/quick inputs |

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| What is a controlled component? | Input managed by React state |
| What is an uncontrolled component? | Input managed by the DOM (via ref) |
| Which is better? | Controlled (for most cases), Uncontrolled for simple forms |
| How do you get value from uncontrolled input? | Using `ref.current.value` |
