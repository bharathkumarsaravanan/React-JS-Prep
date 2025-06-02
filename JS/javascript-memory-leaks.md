
# JavaScript Memory Leaks, Garbage Collection & Performance

## 🚀 Goal
Understand how memory management works in JavaScript, what causes memory leaks (especially in the context of React), how the Garbage Collector (GC) works, and how to analyze leaks using Chrome DevTools.

---

## 1. What is Memory Management?
- JS automatically allocates and deallocates memory using **Garbage Collection (GC)**.
- You create objects, arrays, functions → JS stores them in memory.
- Once objects are no longer **reachable**, GC frees them.

---

## 2. Garbage Collection in JS
- JavaScript uses **Mark-and-Sweep** algorithm:
  1. GC starts from **roots** (e.g., `window`, call stack).
  2. Marks everything **reachable**.
  3. Sweeps away the unmarked (unreachable) memory.

> ✅ If nothing references a value, it is garbage collected.

### Example:
```js
let obj = { name: "test" }; // allocated
obj = null; // now eligible for GC
```

---

## 3. Common Causes of Memory Leaks

### 🔁 1. Closures Holding References
```js
function leaky() {
  let hugeData = new Array(1000000).fill('💥');
  return function inner() {
    console.log(hugeData[0]); // still references hugeData
  };
}
```
**Fix:** Nullify unused variables or avoid unnecessary closures.

### 🗃️ 2. Forgotten Timers or Intervals
```js
setInterval(() => console.log('hi'), 1000); // runs forever
```
**Fix:** Clear intervals/timeouts during cleanup (e.g., `useEffect` cleanup).

### 💾 3. Detached DOM Elements
```js
let node = document.getElementById("element");
document.body.removeChild(node); // node still referenced in JS
```
**Fix:** Manually nullify DOM references after removal if needed.

### 🧠 4. Global Variables
```js
window.leak = new Array(1000000).fill('🚨');
```
**Fix:** Avoid polluting global scope.

### 🔁 5. Event Listeners Not Removed
```js
div.addEventListener("click", handleClick); // not removed
```
**Fix:** Always remove listeners when elements are destroyed.

---

## 4. How to Detect Memory Leaks

### 🛠 Chrome DevTools → Memory Tab

#### Steps:
1. Open DevTools → `Memory` tab
2. Take **Heap Snapshot** before interaction
3. Trigger UI actions (e.g., open/close modal repeatedly)
4. Take another Heap Snapshot
5. Compare retained objects, growth, and detached DOM trees

> 🔍 Look for objects that should be gone but remain in memory

---

## 5. Real-World Leak in React

### Bad Code:
```js
useEffect(() => {
  const interval = setInterval(() => console.log("leak"), 1000);
}, []); // missing cleanup
```

### Fix:
```js
useEffect(() => {
  const interval = setInterval(() => console.log("safe"), 1000);
  return () => clearInterval(interval); // ✅ cleanup
}, []);
```

---

## 6. Performance Profiling

### Use DevTools → Performance Tab:
- Record interactions (like typing, clicking)
- Look for long tasks, frame drops
- Check for JS memory spikes or unnecessary re-renders

### In React:
- Use **React DevTools Profiler** to:
  - Find re-renders
  - Measure component render durations
  - Optimize memoization and avoid unnecessary updates

---

## 7. Interview Questions & Answers

### Q1: What is a memory leak in JS?
**A:** When memory that’s no longer needed is not released, causing a steady increase in usage.

### Q2: How do closures cause memory leaks?
**A:** They retain references to variables even after outer functions finish execution, keeping them alive.

### Q3: How does the Garbage Collector work?
**A:** It finds all reachable objects from root references and frees anything else (mark-and-sweep).

### Q4: Tools to find memory leaks?
**A:** Chrome DevTools → Memory tab (Heap Snapshots, Allocation Timeline)

### Q5: How to prevent memory leaks in React?
**A:** Cleanup side effects using return in `useEffect`, avoid stale closures, unsubscribe listeners, and remove intervals.

### Q6: What are signs that a memory leak is present in an app?
**A:** App becomes slower over time, memory usage increases continuously, and you see retained DOM nodes in memory profiles.

### Q7: Can you detect memory leaks with performance profiling tools?
**A:** Yes. DevTools’ Memory tab helps take heap snapshots and compare memory usage over time.

### Q8: What is the difference between `repaint` and `reflow`?
**A:** `Reflow` recalculates layout (expensive), while `repaint` redraws elements without layout changes (less expensive).

### Q9: How do detached DOM nodes cause memory leaks?
**A:** If JavaScript still holds references to DOM elements removed from the document, they can't be garbage collected.

### Q10: How does using `React.memo` or `useMemo` help performance?
**A:** It prevents unnecessary re-renders and re-computations, reducing memory churn and CPU usage.

---

## 8. Study Strategy for Fast Learning

| Day | Focus Topic                     | Task |
|-----|----------------------------------|------|
| Day 1 | Understand Garbage Collection     | Write simple examples, watch animation videos |
| Day 2 | Learn Closure & Timer Leaks      | Code examples with and without fixes |
| Day 3 | React + Memory Leaks             | Fix broken useEffect examples |
| Day 4 | DevTools Practice + Mock Interview | Use Memory tab and record findings |

---

## ✅ Summary
Memory leaks slow down apps and eat resources. JavaScript devs—especially React developers—must master GC, identify leak patterns, and use DevTools efficiently. Good memory management leads to performant, scalable apps.
