# 🧪 React Testing Library – Basics

---

## 🎯 What is React Testing Library?

> A testing utility that helps you **test React components the way users interact** with them — not their internals.

✅ Focus:
- Testing **behavior**, not implementation  
- Simulates **user actions**  
- Promotes **accessible queries** (`getByRole`, `getByLabelText`, etc.)

---

## 🛠️ Installation

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

---

## 🧱 Basic Test Setup

### Example Component:

```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```

### Example Test:

```jsx
import { render, screen } from '@testing-library/react';
import Greeting from './Greeting';

test('renders greeting text', () => {
  render(<Greeting name="Bharath" />);
  const heading = screen.getByText(/hello, bharath/i);
  expect(heading).toBeInTheDocument();
});
```

---

## ✍️ Common Queries

| Query              | Purpose                        |
|--------------------|--------------------------------|
| `getByText()`      | Finds element with text        |
| `getByRole()`      | Finds by accessibility role    |
| `getByLabelText()` | For form inputs                |
| `getByTestId()`    | When others don’t work (less preferred) |

---

## 🎯 User Interaction

```jsx
import { fireEvent } from '@testing-library/react';

test('button click updates count', () => {
  render(<Counter />);
  const btn = screen.getByText(/click me/i);
  fireEvent.click(btn);
  expect(screen.getByText(/count: 1/i)).toBeInTheDocument();
});
```

🧠 You can also use `userEvent` (more realistic, slower):

```bash
npm install @testing-library/user-event
```

---

## 🧪 Interview Q&A

| Question | Simple Answer |
|----------|---------------|
| What is RTL? | A library to test React components based on user behavior |
| What should you test? | What the user sees/interacts with |
| Difference between `getByText` vs `getByRole`? | Text finds content; Role ensures accessibility |
| Is testing internal state good practice? | ❌ No — test only visible output or interaction |
| What’s `jest-dom` used for? | Custom matchers like `toBeInTheDocument()` |
