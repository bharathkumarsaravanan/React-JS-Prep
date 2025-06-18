
# 🚦 Lighthouse & 🔧 Chrome DevTools – Frontend Interview Crash Guide

---

## 🚦 1. Lighthouse – Automated Website Auditing Tool

### 🔹 What is Lighthouse?
Lighthouse is a built-in Chrome tool that **audits** your web page’s:
- Performance
- Accessibility
- Best Practices
- SEO
- PWA readiness

### 🔍 How to Use:
- Open Chrome DevTools → Go to **“Lighthouse”** tab → Click **“Analyze”**
- Choose device type (Mobile/Desktop) and categories
- Click **"Generate report"**

### 📊 Key Audit Categories:

| Category | Description |
|----------|-------------|
| ⚡ Performance | Page load speed (TTI, FCP, LCP, TBT) |
| ♿ Accessibility | Color contrast, ARIA labels, keyboard navigation |
| ✅ Best Practices | HTTPS, image optimization, secure APIs |
| 🔍 SEO | Meta tags, headings, crawlability |
| 📱 PWA | Progressive Web App checks (manifest, service worker) |

### 🧠 Interview Questions:
- What’s TBT, LCP, FCP in Lighthouse?
- How do you improve a low performance score?
- How does Lighthouse differ from DevTools?

---

## 🔧 2. Chrome DevTools – Manual Debugging Power

### 🔍 Important Panels:

| Panel | Purpose |
|-------|---------|
| **Elements** | Inspect/edit HTML & CSS, check styles live |
| **Console** | View logs, run JS, debug errors |
| **Network** | See HTTP requests (XHR, headers, status codes) |
| **Performance** | Record and analyze load/rendering timelines |
| **Sources** | Debug JS with breakpoints |
| **Memory** | Detect memory leaks |
| **Application** | View LocalStorage, cookies, cache |
| **Lighthouse** | Runs audits directly |

### 🛠️ DevTools Use Cases:
- Fix CSS bugs live
- Profile React rendering
- View slow API calls
- Set breakpoints to debug JS
- Diagnose memory leaks

---

## 🎯 DevTools + Lighthouse in Interviews

| Question | What they look for |
|----------|--------------------|
| How do you debug a slow page? | Use Lighthouse → DevTools Performance tab |
| How to find a memory leak? | Use Memory panel + heap snapshot |
| Why is TTI high? | JS blocking scripts, unused code |
| How do you test accessibility? | Lighthouse + Elements Accessibility tab |
| What is CLS? | Cumulative Layout Shift (visual stability) |

---

## 🧪 Practice Task

1. Visit: https://web.dev/measure/
2. Analyze your site with Lighthouse
3. Open Chrome DevTools:
   - Go to Performance → Click “Record” → Reload
   - Check for **long tasks**, **scripting issues**, or **layout shifts**

---

## 🧠 Key Terms for Interviews

| Term | Meaning |
|------|---------|
| **TTI** | Time to Interactive |
| **FCP** | First Contentful Paint |
| **LCP** | Largest Contentful Paint |
| **CLS** | Cumulative Layout Shift |
| **TBT** | Total Blocking Time |
| **JS Heap** | Memory used by JS |
| **Event loop** | JS concurrency model |
| **Debounce/throttle** | Limit function calls |

---

✅ Use Lighthouse for scoring, DevTools for fixing.
