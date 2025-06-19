# ⚛️ Lifting State Up & Prop Drilling – Simplified Guide

---

## 🧠 What is Lifting State Up?

“**Lifting state up**” means moving shared state to the **closest common parent** component so multiple children can access or modify it.

---

## ✅ Why Do We Lift State?

- Two or more components need to **share** the same state.
- Helps keep the **source of truth** in a single place.
- Promotes **controlled components** (React manages all state).

---

## 📦 Example

```jsx
// Parent.js
function Parent() {
  const [name, setName] = useState("");

  return (
    <>
      <ChildInput name={name} setName={setName} />
      <ChildDisplay name={name} />
    </>
  );
}

function ChildInput({ name, setName }) {
  return <input value={name} onChange={(e) => setName(e.target.value)} />;
}

function ChildDisplay({ name }) {
  return <p>Hello, {name}!</p>;
}
```

✅ Both children share the `name` state lifted to the parent.

---

## 🧪 Interview Q&A – Lifting State

| Question | Simple Answer |
|---------|----------------|
| What is lifting state up? | Moving state to a common ancestor to share between components |
| Why do we lift state? | To make components share the same data source |
| When should state be lifted? | When multiple components need to read/write the same value |

---

## 🪜 What is Prop Drilling?

Prop drilling is passing data **through multiple levels of components** even if intermediate components don’t use it — just to reach a deeply nested one.

---

## 📦 Example

```jsx
function App() {
  return <Grandparent user="Alice" />;
}

function Grandparent({ user }) {
  return <Parent user={user} />;
}

function Parent({ user }) {
  return <Child user={user} />;
}

function Child({ user }) {
  return <p>Hello, {user}</p>;
}
```

❌ `Grandparent → Parent → Child` all pass the `user` prop down even though only `Child` uses it.

---

## ✅ How to Fix Prop Drilling

- **React Context API**
- **State management tools** (Redux, Zustand, etc.)
- **Colocate deeply-used state near consumers**

---

## 🧪 Interview Q&A – Prop Drilling

| Question | Simple Answer |
|---------|----------------|
| What is prop drilling? | Passing props through components that don’t need them just to reach a nested one |
| Why is it bad? | Makes code messy, harder to maintain |
| How can you avoid it? | Use Context API or state management tools |
