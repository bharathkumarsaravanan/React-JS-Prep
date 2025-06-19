# 📦 Box Model, Z-Index, Specificity – Simplified Guide

---

## 📦 1. Box Model – Layout Anatomy

Every HTML element is a box. The **box model** defines how space is consumed.

### ✅ Layers of the box:

```
| Margin  |
| Border  |
| Padding |
| Content |
```

### ✅ Explanation:

| Part | Description |
|------|-------------|
| **Content** | The actual text/image inside the element |
| **Padding** | Space between content and border |
| **Border** | Edge of the box |
| **Margin** | Space between this element and others |

---

### ✅ Example

```css
.card {
  margin: 10px;
  padding: 15px;
  border: 1px solid black;
}
```

✅ This creates spacing *outside* (`margin`) and *inside* (`padding`) the `.card`.

---

### ✅ `box-sizing`

```css
* {
  box-sizing: border-box;
}
```

✅ Makes padding and border stay **inside the declared width/height**, avoiding layout bugs.

---

## 🧱 2. Z-Index – Stack Order

Controls which element **appears above or below** others.

### ✅ Rule of thumb:

- Higher `z-index` = closer to user (on top)
- Only works on **positioned** elements (`relative`, `absolute`, `fixed`, `sticky`)

---

### ✅ Example:

```css
.box1 {
  position: absolute;
  z-index: 1;
}

.box2 {
  position: absolute;
  z-index: 2;
}
```

✅ `box2` will appear **above** `box1`.

---

## 🧠 3. CSS Specificity – Which Rule Wins?

When multiple CSS rules apply to the same element, **specificity** decides which one wins.

### ✅ Specificity Ranking:

| Selector Type | Score |
|---------------|-------|
| Inline styles (`style=""`) | 1000 |
| ID selector (`#id`) | 100 |
| Class/Attr/Pseudo (`.class`, `[type]`, `:hover`) | 10 |
| Element tag (`div`, `h1`, etc) | 1 |
| `!important` | Overrides all (use with caution) |

---

### ✅ Example:

```css
/* Score: 10 */
.button {
  color: blue;
}

/* Score: 100 */
#button {
  color: red;
}
```

✅ `#button` wins because ID (100) > class (10)

---

### ✅ Pro Tip:

Avoid using `!important` unless you're debugging or overriding external styles.

---

## 🧪 Interview Q&A Summary

| Question | Simple Answer |
|---------|----------------|
| What is Box Model? | How elements are spaced with padding, border, margin |
| What does `box-sizing: border-box` do? | Keeps total width/height including padding & border |
| What is Z-Index? | Controls which item appears above others |
| When does z-index work? | Only on positioned elements |
| What is specificity? | Determines which CSS rule takes priority |
| How to increase specificity? | Use more specific selectors like `#id` or `.class.class2` |
