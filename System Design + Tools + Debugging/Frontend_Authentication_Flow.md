# 🔐 Frontend Authentication Flow – Crash Guide (Interview Ready)

---

## ✅ 1. Types of Authentication Flows in Frontend

| Flow Type               | Use Case                          | Token Storage         |
|------------------------|-----------------------------------|------------------------|
| Email/Password login   | Classic login/signup              | LocalStorage / Cookies |
| OAuth (Google, GitHub) | Third-party login                 | Redirect flow          |
| Magic Link             | Passwordless                      | Email-based token      |
| OTP / 2FA              | Extra security layer              | Temp session + token   |
| Social SSO (SSO JWT)   | Corporate/integrated auth         | SAML + JWT             |

---

## ✅ 2. Common Token Handling Approaches

| Storage           | Pros                         | Cons                          |
|-------------------|------------------------------|-------------------------------|
| `localStorage`    | Easy to implement            | Vulnerable to XSS             |
| `sessionStorage`  | Clears on tab close          | Still XSS-vulnerable          |
| `HttpOnly Cookies`| Safe from JS access          | Needs backend cookie setup    |

> ⚠️ **Interview Tip:** Use **HttpOnly Cookies** for sensitive applications.

---

## ✅ 3. Basic JWT Flow (React + REST)

1. Client sends login credentials  
2. API responds with `{ accessToken, refreshToken }`  
3. Access token is used in headers for future requests  
4. When access token expires, refresh token is used to get a new one  

---

## ✅ 4. Frontend React Auth Flow (Simple)

1. Login Form ➝ Submit  
2. POST /login ➝ Get token(s)  
3. Save token in `localStorage` or `cookie`  
4. Set Axios headers:
```js
axios.defaults.headers.common['Authorization'] = `Bearer ${token}`;
```
5. Protect routes using:
```js
if (!token) redirectToLogin();
```
6. On logout: remove token and redirect  

---

## ✅ 5. Refreshing JWT (Access + Refresh Tokens)

- Use short-lived `accessToken` (15 mins)  
- Use long-lived `refreshToken` (7 days)  
- Store `refreshToken` in **HttpOnly Cookie**  
- Axios Interceptor:
```js
axios.interceptors.response.use(
  res => res,
  async err => {
    if (err.response.status === 401) {
      const newToken = await refreshToken();
      axios.defaults.headers['Authorization'] = `Bearer ${newToken}`;
      return axios(err.config); // retry
    }
    return Promise.reject(err);
  }
);
```

---

## ✅ 6. Route Protection Example (React Router)

```jsx
<Route
  path="/dashboard"
  element={
    token ? <Dashboard /> : <Navigate to="/login" />
  }
/>
```

---

## ✅ 7. Interview Questions to Prepare

| Question | What to Say |
|----------|-------------|
| How do you handle authentication in React? | JWT with refresh token; protect routes, use Axios interceptors |
| Where do you store tokens and why? | Prefer HttpOnly cookie; fallback is localStorage |
| How do you refresh expired tokens? | Axios interceptors + refreshToken |
| How do you protect private routes? | Use conditional rendering or route guards |
| Difference between authentication and authorization? | AuthN = Who you are; AuthZ = What you can access |
| What are security concerns in client-side auth? | XSS, CSRF, token leaks — use HttpOnly, CORS, secure headers |

---

## ✅ 8. 🧪 Mini Exercise

Implement:

- Login screen that gets `accessToken`  
- Store it in `localStorage`  
- Protect `/dashboard` route using token  
- Add Logout (clears token + redirects)  
