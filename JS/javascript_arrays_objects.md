
# JavaScript: Arrays and Objects – Deep Dive

A focused guide for React Developer Interviews on mastering Array methods and object traversal.

---

## 🧩 1. Array Methods: `map`, `filter`, `reduce`

These are must-know functional tools for any React dev.

---

### 🔹 `map()` – *Transform an array*
```js
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6]
```
- **Use case:** Transform data before rendering (e.g. `.map()` in JSX).
- **Doesn’t mutate original array**

---

### 🔹 `filter()` – *Select items based on a condition*
```js
const numbers = [1, 2, 3, 4];
const even = numbers.filter(num => num % 2 === 0);
console.log(even); // [2, 4]
```
- **Use case:** Filtering out nulls, or items by status, etc.

---

### 🔹 `reduce()` – *Summarize an array into a single value*
```js
const nums = [1, 2, 3, 4];
const total = nums.reduce((acc, curr) => acc + curr, 0);
console.log(total); // 10
```
- **Use case:** Totals, averages, flattening arrays, etc.

---

## 🧪 Practice Task:
Write a `.reduce()` that returns the longest word in an array.
```js
const words = ['apple', 'banana', 'kiwi'];
const longest = words.reduce((a, b) => a.length > b.length ? a : b);
console.log(longest); // banana
```

---

## 🔁 2. Object Traversal (Looping through objects)

### `for...in` – Loop through keys
```js
const obj = { a: 1, b: 2 };
for (let key in obj) {
  console.log(key, obj[key]);
}
```

### `Object.keys() / Object.values() / Object.entries()`
```js
const obj = { a: 1, b: 2 };

Object.entries(obj).forEach(([key, value]) => {
  console.log(key, value);
});
```

---

## 🔧 3. Custom Implementations

### ✅ Write your own `.map()`
```js
Array.prototype.myMap = function(callback) {
  let result = [];
  for (let i = 0; i < this.length; i++) {
    result.push(callback(this[i], i, this));
  }
  return result;
};

console.log([1, 2, 3].myMap(x => x * 2)); // [2, 4, 6]
```

---

### ✅ Write your own `.reduce()`
```js
Array.prototype.myReduce = function(callback, initialValue) {
  let acc = initialValue;
  for (let i = 0; i < this.length; i++) {
    acc = callback(acc, this[i], i, this);
  }
  return acc;
};

console.log([1, 2, 3].myReduce((acc, val) => acc + val, 0)); // 6
```

---

### ✅ Flatten a nested array (`[1, [2, [3]]] → [1, 2, 3]`)
```js
function flatten(arr) {
  return arr.reduce((flat, item) =>
    flat.concat(Array.isArray(item) ? flatten(item) : item), []);
}

console.log(flatten([1, [2, [3, 4]]])); // [1, 2, 3, 4]
```

---

## ✅ Interview Tips:
- Be ready to **rewrite `map`, `reduce`, `flatten`**.
- Know when to use `forEach` vs `map` (hint: `map` returns a value).
- Show that you understand **immutability** – don’t mutate inputs.

---
