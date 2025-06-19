
# 🎯 CSS Flexbox / Grid / Positioning – Simplified Guide

---

## 🧱 1. Flexbox – 1D Layout (Row OR Column)

> Flexbox is used to layout items in a **row or column**, great for aligning and spacing.

### ✅ Common Properties:

| Property | What it does |
|---------|---------------|
| `display: flex` | Enables flex layout |
| `flex-direction` | `row` (default) or `column` |
| `justify-content` | Horizontal alignment |
| `align-items` | Vertical alignment |
| `gap` | Spacing between items |
| `flex-wrap` | Allows wrapping |

---

### ✅ Example: Horizontal Center

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

✅ This centers all child items **both horizontally and vertically**.

---

### ✅ Flex Shorthand

```css
.item {
  flex: 1; /* grow */
}
```

Or

```css
.item {
  flex: 1 0 200px; /* grow shrink basis */
}
```

---

## 🔲 2. Grid – 2D Layout (Rows + Columns)

> CSS Grid is used to build full layouts with **rows and columns**.

### ✅ Common Properties:

| Property | What it does |
|----------|--------------|
| `display: grid` | Enables grid |
| `grid-template-columns` | Define column structure |
| `grid-template-rows` | Define row structure |
| `gap` | Space between rows and columns |
| `grid-column` | Span columns |
| `grid-row` | Span rows |

---

### ✅ Example: 3 Equal Columns

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 20px;
}
```

✅ `fr` = "fractional unit" of space.

---

### ✅ Grid vs Flex

| Feature | Flexbox | Grid |
|--------|---------|------|
| Layout | One-direction (1D) | Two-direction (2D) |
| Use for | Small components | Full page layout |
| Responsive? | Very | Very |

---

## 📍 3. Positioning in CSS

> Controls how elements are **placed** on the page.

### ✅ Types of `position`:

| Value | Description |
|-------|-------------|
| `static` | Default – normal flow |
| `relative` | Offset from normal position |
| `absolute` | Positioned relative to nearest `relative`/`absolute` parent |
| `fixed` | Fixed to viewport |
| `sticky` | Sticks on scroll within a container |

---

### ✅ Position Example:

```css
.box {
  position: absolute;
  top: 10px;
  left: 20px;
}
```

✅ Use `relative` on parent if you want `absolute` child to stick inside it.

---

## 🔥 Interview Q&A Summary

| Question | Simple Answer |
|---------|----------------|
| Flexbox or Grid? | Flex for 1D, Grid for 2D layouts |
| How to center with Flexbox? | `justify-content: center`, `align-items: center` |
| What is `fr` in Grid? | Fraction of available space |
| Difference between `absolute` and `fixed`? | Absolute sticks inside nearest parent, fixed sticks to screen |
| When to use `sticky`? | To fix something on scroll until a limit |

---

## ✅ Real Use Case Examples

```css
/* Navbar stick on scroll */
.navbar {
  position: sticky;
  top: 0;
}
```

```css
/* Sidebar layout with Grid */
.layout {
  display: grid;
  grid-template-columns: 250px 1fr;
}
```
