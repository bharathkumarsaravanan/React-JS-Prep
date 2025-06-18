# 🔥 ES6+ JavaScript Essentials for Interviews

---

## 🧩 1. Destructuring
A quick way to pull values from arrays/objects into variables.

### ✅ Object Destructuring

```js
const user = { name: "Bharath", age: 25 };
const { name, age } = user;
```

### ✅ Array Destructuring

```js
const [a, b] = [1, 2];
```

---

## 🧃 2. Spread & Rest

### ✅ Spread (Unpacks values)

```js
const arr1 = [1, 2];
const arr2 = [...arr1, 3]; // [1, 2, 3]
```

### ✅ Rest (Collects values)
Rest means "collect the rest" into an array or object.

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b);
}
```

---

## 🗺 3. Map & Set

### ✅ Map
Like an object, but with any type of key, and ordered.
```js
const map = new Map();
map.set("key", "value");
map.get("key"); // "value"
```

### ✅ Set
Stores unique values only.
```js
const set = new Set([1, 2, 2]);
set.add(3); // only unique values
```

---

## ❓ 4. Optional Chaining & Nullish Coalescing
Safely access nested properties without crashing if something is undefined or null.

### ✅ Optional Chaining

```js
user?.address?.city; // undefined if any part is missing
```

### ✅ Nullish Coalescing
Return a default value only if the left side is null or undefined
(🚫 does not trigger on 0, false, "")

```js
const name = user.name ?? "Guest";
```

---

## ⚙️ 5. Debouncing & Throttling

### ✅ Debounce
Debouncing means: “Wait for the user to stop typing before doing something.”

🧠 Used when you don’t want to fire a function too often, like:

Search boxes

Input validation

Resize events

```js
function debounce(fn, delay) {
  let timeout;
  return function (...args) {
    clearTimeout(timeout);
    timeout = setTimeout(() => fn.apply(this, args), delay);
  };
}
```

### ✅ Throttle
Throttling means: “Run function only once every X ms, no matter how many times the event fires.”

🧠 Use it for:

Scroll events

Mouse move

Window resize

```js
function throttle(fn, limit) {
  let inThrottle;
  return function (...args) {
    if (!inThrottle) {
      fn.apply(this, args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}
```

---

## 🔗 6. Currying & Composition

### ✅ Currying
Currying means:
Turning a function that takes multiple arguments into a chain of functions, each with one argument.
```js
const greet = msg => name => `${msg}, ${name}`;
greet("Hello")("Bharath");
```
✅ Why use Currying?
Makes code more reusable.

Helps create custom functions easily.

### ✅ Function Composition
Function Composition means:
Combining multiple functions together so that the output of one becomes input of the next.

🧠 Like:
f(g(x))

```js
const compose = (f, g) => x => f(g(x));
```

---

## 🔁 7. Array Methods

### ✅ map

```js
[1, 2, 3].map(n => n * 2); // [2, 4, 6]
```

### ✅ filter

```js
[1, 2, 3].filter(n => n > 1); // [2, 3]
```

### ✅ find

```js
[{id:1}, {id:2}].find(u => u.id === 2); // {id:2}
```

### ✅ reduce

```js
[1, 2, 3].reduce((a, b) => a + b, 0); // 6
```

### ✅ some
Checks if at least one item passes the test.
```js
[1, 2, 3].some(n => n % 2 === 0); // true
```
✅ Use when: You want to check for existence of a condition.
### ✅ every
Checks if all items pass the test.
```js
[2, 4, 6].every(n => n % 2 === 0); // true
```
 ✅ Use when: You want to make sure everything matches a rule.
---

## ✅ Summary Table

| Feature | Purpose |
|--------|---------|
| Destructuring | Extract values from object/array |
| Spread | Unpack into new array/object |
| Rest | Collect remaining values |
| Map | Unique keys, fast lookups |
| Set | Unique values only |
| Optional Chaining | Safe nested access |
| Nullish Coalescing | Fallback for null/undefined only |
| Debounce | Wait until user stops typing |
| Throttle | Limit how often function runs |
| Currying | Break functions into smaller reusable ones |
| Composition | Combine multiple functions |
| Array Methods | map, filter, reduce, etc., for cleaner data ops |
