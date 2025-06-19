# ⚛️ React Context API vs Redux – Simplified Guide

---

## 🧠 What Is Context API?

> Built-in way in React to **pass global data** (like theme, user, auth) **without prop drilling**.

---

## ✅ Context API Use Case

- Small to medium apps  
- Light global data (user, theme, language)  
- When **prop drilling** becomes annoying

---

## 📦 Example

```jsx
// Create Context
const ThemeContext = React.createContext();

// Provide
<ThemeContext.Provider value="dark">
  <Child />
</ThemeContext.Provider>

// Consume
const theme = useContext(ThemeContext);
```

---

## 🧠 What Is Redux?

> A **state management library** for handling **complex, large-scale state** outside the React tree.

---

## ✅ Redux Use Case

- Large apps with **many components** sharing/updating state  
- Complex state logic (undo/redo, caching, etc.)  
- Want **dev tools**, **middlewares**, **predictable updates**

---

## 🆚 Key Differences

| Feature                  | Context API   | Redux                  |
|--------------------------|----------------|-------------------------|
| Built-in?                | ✅ Yes         | ❌ No (external lib)    |
| State type               | Simple global state | Complex app-wide state |
| Performance              | Slower on frequent updates | Optimized with middlewares |
| DevTools                | ❌ None        | ✅ Yes (Redux DevTools) |
| Middleware (logging, async) | ❌ No     | ✅ Yes (Redux Thunk, Saga) |
| Boilerplate              | 🔸 Low         | 🔺 High (Redux Toolkit helps) |
| Async handling           | ❌ Manual      | ✅ Built-in with middleware |

---

## 🧪 When to Use What?

| Situation                              | Use       |
|----------------------------------------|-----------|
| Simple theme or user state             | ✅ Context |
| App-wide complex state (cart, auth)    | ✅ Redux   |
| Need dev tools or advanced workflows   | ✅ Redux   |
| No async or minimal global state       | ✅ Context |

---

## 🧪 Interview Q&A

| Question                        | Simple Answer                                                  |
|---------------------------------|----------------------------------------------------------------|
| What is Context API?           | A way to share data globally in React without prop drilling    |
| When to use Context?           | For small global states like theme, language                   |
| What is Redux?                 | A library to manage complex app-wide state                     |
| When to use Redux?             | Large apps, async needs, or advanced state workflows           |
| Can Context replace Redux?     | Yes, for small apps — but Redux is better for complex logic    |
