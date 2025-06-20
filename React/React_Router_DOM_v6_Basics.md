
# 🚦 React Router DOM v6 – Basics

---

## 🔧 Installation

```bash
npm install react-router-dom
```

---

## 🧱 Core Concepts

| Concept | Description |
|--------|-------------|
| `BrowserRouter` | Top-level wrapper to enable routing |
| `Routes` | Wrapper for all `Route` components |
| `Route` | Defines the path and the component to render |
| `Link` | Navigation without page reload |
| `useNavigate()` | Programmatic navigation |
| `useParams()` | Access route parameters |

---

## 🗺️ Example Structure

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## 📦 Route Params

```jsx
<Route path="/user/:id" element={<User />} />
```

```jsx
function User() {
  const { id } = useParams();
  return <p>User ID: {id}</p>;
}
```

---

## 🔁 Navigate Programmatically

```jsx
import { useNavigate } from "react-router-dom";

const Login = () => {
  const navigate = useNavigate();

  const handleLogin = () => {
    // logic...
    navigate("/dashboard");
  };

  return <button onClick={handleLogin}>Login</button>;
};
```

---

## 🔄 Nested Routes

```jsx
<Routes>
  <Route path="/dashboard" element={<Dashboard />}>
    <Route path="stats" element={<Stats />} />
    <Route path="settings" element={<Settings />} />
  </Route>
</Routes>
```

📌 Inside `Dashboard`, use:

```jsx
<Outlet /> // renders nested route content
```

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| What is `BrowserRouter`? | Wrapper to enable routing in a React app |
| Difference between `Route` and `Routes`? | `Routes` wraps multiple `Route` components |
| How to link pages without reload? | Use `<Link to="/path" />` |
| How to navigate in code? | Use `useNavigate()` |
| How to access route params? | Use `useParams()` |
| How to render nested routes? | Use `<Outlet />` inside parent component |
