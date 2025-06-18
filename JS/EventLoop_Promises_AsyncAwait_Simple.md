
# 🔄 Event Loop, Promises & Async/Await – Simple Guide

---

## 🧠 1. What is the Event Loop?

JavaScript runs **one thing at a time** (single-threaded). But it can still handle tasks like API calls, thanks to the **Event Loop**.

### 🔁 Think of it like:
- **JS engine** = chef 🧑‍🍳 (handles one dish at a time)
- **Web APIs** = helpers 👨‍🔧 (do long tasks like timers or fetch)
- **Callback/Microtask Queues** = dishes waiting to be served
- **Event Loop** = moves finished dishes back to chef to serve

### Example:

```js
console.log("Start");

setTimeout(() => console.log("Timer"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("End");
```

### Output:

```
Start
End
Promise
Timer
```

---

## 🪄 2. What is a Promise?

A **Promise** is like ordering food. You get the result **later**.

```js
const pizza = new Promise((resolve, reject) => {
  setTimeout(() => resolve("🍕 Ready!"), 1000);
});

pizza.then(msg => console.log(msg));
```

---

## 🤖 3. What is Async/Await?

Just a **cleaner way to write Promises**.

### Instead of:

```js
fetchData().then(res => res.json()).then(data => console.log(data));
```

### Use:

```js
async function load() {
  const res = await fetchData();
  const data = await res.json();
  console.log(data);
}
```

---

## 💥 4. Interview Questions (Simple)

| Question | Answer |
|----------|--------|
| What is a Promise? | A task that finishes later (success or error) |
| What is async/await? | A better way to use Promises |
| What is Event Loop? | JS’s way to handle async without blocking |
| Promise vs setTimeout? | Promises (microtasks) run before timers (callback queue) |
| Can you await anything? | Yes, it will be wrapped into a Promise |

---

## 🧪 5. Predict Output

```js
console.log("1");

setTimeout(() => console.log("2"), 0);

Promise.resolve().then(() => console.log("3"));

console.log("4");
```

### Output:
```
1
4
3
2
```

---

## 🛠 6. React Use Case

React often uses async functions:

```js
useEffect(() => {
  async function fetchData() {
    const res = await fetch('/api/data');
    const data = await res.json();
    setData(data);
  }
  fetchData();
}, []);
```

---

## ✅ Recap

- JS is single-threaded
- Uses Event Loop to handle async
- Promises go to microtask queue
- `await` pauses till Promise resolves
- `async/await` is just clean syntax
