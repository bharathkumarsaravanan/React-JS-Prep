
# ⚛️ React State Management Patterns – Frontend Interview Crash Guide

---

## 🔹 1. Local Component State

- Managed via `useState`, `useReducer`, or class component state.
- Best for **simple UI-level state** like input fields, toggles, modal visibility.

```jsx
const [isOpen, setIsOpen] = useState(false);
```

✅ Use when: State is **used only within one component**.

---

## 🔹 2. Lifting State Up

- Move shared state to the **nearest common ancestor** component.
- Common for **parent-child** communication.

```jsx
// Parent manages state
const [input, setInput] = useState("");
<InputComponent value={input} onChange={setInput} />
```

✅ Use when: Multiple child components need to share state.

---

## 🔹 3. Context API

- Native React API to **share state across deep component trees**.
- Good for **theme**, **auth**, **language**, or **user data**.
- Combine with `useReducer` or `useState`.

```jsx
const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("dark");
  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}
```

✅ Use when: You want **global** state without prop drilling.

---

## 🔹 4. useReducer + Context (Redux-like Pattern)

- A scalable, testable alternative to Redux without extra libraries.
- Best for **complex state logic** with **actions** and **reducers**.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
  }
}

const CounterContext = createContext();

function CounterProvider({ children }) {
  const [state, dispatch] = useReducer(reducer, { count: 0 });
  return (
    <CounterContext.Provider value={{ state, dispatch }}>
      {children}
    </CounterContext.Provider>
  );
}
```

✅ Use when: You need structured global state with action-based updates.

---

## 🔹 5. Redux Toolkit (RTK)

- Popular external state library.
- Centralizes app state, supports **devtools, middleware, async logic**.
- Modern Redux uses `createSlice`, `configureStore`, and avoids boilerplate.

```js
const counterSlice = createSlice({
  name: "counter",
  initialState: 0,
  reducers: {
    increment: state => state + 1,
  },
});
```

✅ Use when: App has **large-scale** state or needs **middleware**.

---

## 🔹 6. Zustand / Jotai / Recoil / Valtio (Modern Lightweight Alternatives)

| Tool | Features |
|------|----------|
| **Zustand** | Minimal, simple state with hooks. No provider needed. |
| **Jotai** | Atomic state management (recoil-like, simpler) |
| **Recoil** | Facebook's solution, supports atom-based and derived state |
| **Valtio** | Proxy-based reactive state |

✅ Use when: You want **less boilerplate**, **high performance**, and simpler alternatives to Redux.

---

## 🧠 Interview Questions to Prepare

1. What’s the difference between Context and Redux?
2. When should you avoid using Context API?
3. How do you prevent unnecessary re-renders with Context?
4. Explain `useReducer` vs `useState`.
5. When would you prefer Zustand over Redux Toolkit?
6. How do you persist state in Redux?

---

## 🎯 Optimization Tips

| Problem | Solution |
|--------|----------|
| Re-renders on context value change | Memoize `value` object: `useMemo()` |
| Prop drilling | Use Context |
| Complex async logic | Use Redux Toolkit middleware like `createAsyncThunk` |
| State duplication | Normalize with Redux or Zustand |
| Debugging state flow | Use Redux DevTools |

---

## 🧪 Practice Task

**Goal**: Build a small counter app using:
1. `useState`
2. `Context + useReducer`
3. `Zustand`

Compare re-renders and boilerplate.

---

