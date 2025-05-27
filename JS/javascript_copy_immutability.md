
# JavaScript: Deep Copy vs Shallow Copy & Immutability

A focused guide for React Developer Interviews on understanding memory, copying techniques, and writing immutable code.

---

## 🔄 1. Shallow Copy vs Deep Copy

| Aspect           | Shallow Copy                          | Deep Copy                          |
|------------------|----------------------------------------|-------------------------------------|
| What it copies   | Top-level references only              | Recursively copies all nested data |
| Shared reference | Yes (nested objects/arrays)            | No (completely independent copy)   |
| Example Tools    | `=`, `...spread`, `Object.assign()`     | `structuredClone()`, `_.cloneDeep()` or custom recursions |

---

### 🧪 Shallow Copy Example

```js
const obj1 = { a: 1, b: { c: 2 } };
const shallow = { ...obj1 };

shallow.b.c = 100;
console.log(obj1.b.c); // 100 — ❌ mutated original!
```

---

### ✅ Deep Copy Example (with structuredClone)

```js
const obj1 = { a: 1, b: { c: 2 } };
const deep = structuredClone(obj1);

deep.b.c = 100;
console.log(obj1.b.c); // 2 — ✅ original is safe
```

---

## 🔧 2. Custom Deep Clone Function (Without JSON)

```js
function deepClone(obj) {
  if (obj === null || typeof obj !== 'object') return obj;

  if (Array.isArray(obj)) {
    return obj.map(deepClone);
  }

  const cloned = {};
  for (const key in obj) {
    cloned[key] = deepClone(obj[key]);
  }
  return cloned;
}
```

---

## ⚠️ Why Not JSON Way?

```js
const obj = {
  a: 1,
  b: undefined,
  c: () => {},
};

console.log(JSON.parse(JSON.stringify(obj))); 
// { a: 1 } — b and c lost!
```

- ❌ Loses functions, `undefined`, and circular references cause errors.

---

## 📘 3. Immutability in Practice (React)

### ❌ Bad (Mutates State)
```js
const state = { todos: [{ text: "hi" }] };
state.todos[0].text = "bye";
```

### ✅ Good (Immutable Update)
```js
const newState = {
  ...state,
  todos: state.todos.map(todo => ({ ...todo, text: "bye" })),
};
```

---

## 🧠 Memory & References

- Objects/arrays are **reference types**
- `const a = b` → both point to the same memory
- Deep copy creates **new memory allocation**

---

## 🧪 Common Interview Questions & Answers

### 1. **What’s the difference between shallow and deep copy?**

> A shallow copy only copies top-level properties and retains shared references for nested objects. A deep copy recursively clones all levels, ensuring no shared references.

---

### 2. **Write a custom deep clone function.**

> See section above for full implementation:
```js
function deepClone(obj) { ... }
```

---

### 3. **Why is immutability important in React?**

> React relies on detecting object reference changes to know when to re-render. If you mutate state directly, React may not re-render components as expected.

---

### 4. **Update nested object in React state immutably.**

```js
const updated = {
  ...state,
  user: {
    ...state.user,
    profile: {
      ...state.user.profile,
      name: "New Name"
    }
  }
};
```

---

### 5. **Explain memory difference between reference and primitive.**

> Primitives (like numbers, strings) are copied by value and stored directly in memory. Objects/arrays are reference types; assignments copy references, not data, causing shared mutation.

---

## ✅ Tips
- Prefer immutable updates (spread/rest)
- Use deep clone when necessary
- Avoid JSON clone for serious work
- Consider libraries like `lodash.clonedeep`, `immer`

---
