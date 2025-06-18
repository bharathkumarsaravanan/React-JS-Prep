
# 🛡️ CORS, Preflight, Cookies, LocalStorage, JWT – Frontend Dev Interview Crash Guide

---

## ✅ 1. What is CORS?

**CORS (Cross-Origin Resource Sharing)** is a browser security mechanism that restricts JS from making requests to a **different origin** unless the server explicitly allows it.

### 📌 Example:
```js
// App running on http://localhost:3000
fetch("https://api.example.com/user"); // blocked if CORS not enabled
```

### 💬 Real-world analogy:
Your browser is like a passport officer. It blocks a request to another country (domain) unless that country’s API explicitly says: “You’re allowed to enter.”

---

## ✅ 2. What is Preflight?

A **preflight request** is an **OPTIONS** request sent **automatically** by the browser before actual API calls, when:

- Method is not GET/POST
- Custom headers are added
- Content-Type is anything other than allowed simple types

### 🔁 Flow:
```
1. Browser ➝ OPTIONS ➝ Server
2. Server ➝ 200 OK with CORS headers
3. Browser ➝ Real request (e.g. POST /data)
```

### ✅ Example CORS Headers in Backend:
```http
Access-Control-Allow-Origin: https://your-app.com
Access-Control-Allow-Methods: GET, POST, PUT, DELETE
Access-Control-Allow-Headers: Content-Type, Authorization
```

---

## ✅ 3. Cookie vs LocalStorage vs SessionStorage

| Feature         | Cookies                | LocalStorage        | SessionStorage       |
|-----------------|------------------------|---------------------|----------------------|
| Size Limit      | ~4KB                   | ~5MB                | ~5MB                 |
| Auto Sent w/ Req| ✅ Yes (if not HttpOnly)| ❌ No               | ❌ No                |
| Expiry          | Set manually           | Persisted until deleted | Clears on tab close |
| Access by JS    | ✅ (unless HttpOnly)    | ✅ Yes              | ✅ Yes               |
| Use case        | Auth (HttpOnly = secure)| Non-sensitive info | Temporary values     |

---

## ✅ 4. What is JWT?

**JWT (JSON Web Token)** is a compact, URL-safe token used to verify identity between frontend and backend.

### 📦 Structure:
```
Header.Payload.Signature
```

- Header: `{ alg: "HS256", typ: "JWT" }`
- Payload: `{ userId: 123, role: "admin" }`
- Signature: Ensures integrity (can't be tampered)

### 🛠 How JWT is used in frontend:

1. Backend returns a JWT after login
2. Store it (preferably in `HttpOnly Cookie`)
3. Send it in `Authorization` header with every request:

```js
Authorization: Bearer <token>
```

---

## ✅ 5. Why not always use LocalStorage for JWT?

| Risk | Explanation |
|------|-------------|
| ❌ XSS Attack | JS-accessible tokens in localStorage can be stolen if site is vulnerable |
| ✅ HttpOnly Cookie | Safer – JS can’t access; auto-sent with every request |

⚠️ **Interview Pro Tip**: Use HttpOnly cookies + CSRF protection for secure apps.

---

## ✅ 6. Cookie Flags: `SameSite`, `Secure`, and `HttpOnly`

| Flag       | Purpose                                  |
|------------|------------------------------------------|
| `HttpOnly` | JS can’t access the cookie               |
| `Secure`   | Cookie sent only on HTTPS                |
| `SameSite=Strict` | Prevents CSRF (no cross-site reqs)  |

---

## ✅ 7. Real-world Auth Flow (JWT + Cookies)

Client logs in ➝ Server sets JWT as cookie ➝ Client sends cookie automatically in future requests ➝ Server validates

---

## ✅ 8. Frontend Code Example

```js
// Login and store JWT in localStorage (not recommended for sensitive apps)
const login = async () => {
  const res = await fetch('/login', {
    method: 'POST',
    body: JSON.stringify({ email, password }),
  });
  const data = await res.json();
  localStorage.setItem('token', data.token);
};

// Send token in header
axios.get('/profile', {
  headers: {
    Authorization: `Bearer ${localStorage.getItem('token')}`
  }
});
```

---

## ✅ 9. Interview Questions to Practice

| Question | Ideal Answer |
|----------|--------------|
| What is CORS? | A browser protection to prevent cross-origin requests |
| Why does preflight happen? | For non-simple requests; browser checks if it’s allowed |
| How do you store tokens in frontend? | Prefer HttpOnly cookies for security |
| What's the difference between cookie and localStorage? | Cookies auto-send with requests; localStorage doesn't |
| Can JS access HttpOnly cookie? | No – that's what makes it secure |
| What’s the structure of JWT? | Header, Payload, Signature |
| How do you protect against XSS in auth? | Don’t store sensitive tokens in JS-accessible places |

---

## ✅ 10. Rapid Fire Recap

- **CORS**: Browser security against cross-origin
- **Preflight**: OPTIONS check for unsafe requests
- **Cookies**: Good for secure storage (esp. with HttpOnly)
- **LocalStorage**: Use for non-sensitive data only
- **JWT**: Compact token used in most modern auth
