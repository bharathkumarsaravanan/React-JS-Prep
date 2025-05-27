
# JavaScript: Event Delegation & DOM Manipulation

Master this key frontend concept for scalable, performant UIs — crucial for both Vanilla JS and React developers.

---

## 🧠 What is Event Delegation?

**Event Delegation** is a technique where a parent element handles events from its children using event bubbling.

### ✅ Why Use It?
- Minimizes number of event listeners
- Handles dynamic elements gracefully
- Centralizes logic

---

## 🌊 Event Flow: Bubbling vs Capturing

**Event Flow** phases:
1. Capturing Phase
2. Target Phase
3. Bubbling Phase

By default, JS events bubble up from the target to the root.

### Example:

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>
```

```js
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked");
});

document.getElementById("child").addEventListener("click", () => {
  console.log("Child clicked");
});
```

**Output:**
```
Child clicked
Parent clicked
```

---

## ✅ Event Delegation in Action

### HTML:
```html
<ul id="list">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```

### JavaScript:
```js
document.getElementById("list").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("Clicked:", e.target.textContent);
  }
});
```

---

## 🛠️ Creating Elements Dynamically

```js
const li = document.createElement("li");
li.textContent = "New Item";
document.getElementById("list").appendChild(li);
```

Add attributes/classes:

```js
li.classList.add("item");
li.setAttribute("data-id", "10");
```

---

## 🧪 Real Interview Task

> Create 5 buttons using JS. Log button index on click using delegation.

### HTML:
```html
<div id="buttons"></div>
```

### JS:
```js
const container = document.getElementById("buttons");

for (let i = 1; i <= 5; i++) {
  const btn = document.createElement("button");
  btn.textContent = `Button ${i}`;
  btn.dataset.index = i;
  container.appendChild(btn);
}

container.addEventListener("click", (e) => {
  if (e.target.tagName === "BUTTON") {
    console.log("Clicked:", e.target.dataset.index);
  }
});
```

---

## 🧩 Summary Table

| Concept             | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| Event Delegation    | Handling child events at parent level using bubbling                        |
| Bubbling            | Event moves from target → ancestors                                         |
| Capturing           | Event moves top → target (use `{ capture: true }`)                          |
| createElement       | Creates new DOM nodes in JS                                                 |
| appendChild/append  | Appends DOM nodes                                                           |
| stopPropagation     | Stops bubbling                                                              |

---

## 📘 Interview Questions with Answers

### 1. **What’s the difference between bubbling and capturing?**
> Bubbling: Event moves bottom-up (target → root).  
> Capturing: Event moves top-down (root → target).  
> Bubbling is default in JS.

---

### 2. **Why use event delegation?**
> Improves performance, reduces memory usage, and supports dynamically added elements.

---

### 3. **How do you attach click handlers to elements not yet in DOM?**
> Attach a single listener to a static parent and handle events via `event.target`.

---

### 4. **Write JS to create dynamic list items and handle clicks.**
```js
const ul = document.createElement("ul");
document.body.appendChild(ul);

for (let i = 1; i <= 3; i++) {
  const li = document.createElement("li");
  li.textContent = `Item ${i}`;
  ul.appendChild(li);
}

ul.addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    alert(e.target.textContent);
  }
});
```

---

### 5. **Can you prevent bubbling?**
```js
element.addEventListener("click", (e) => {
  e.stopPropagation();
});
```

> `stopPropagation()` halts event bubbling.

---

## 🧠 Final Tips

- Avoid attaching listeners to each child — use delegation.
- Always check `e.target` before reacting.
- Use `stopPropagation()` sparingly and wisely.

---
