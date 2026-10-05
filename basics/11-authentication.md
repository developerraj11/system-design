
# 15. Authentication question

Interviewer:

> "How will you authenticate users?"

Basic answer:

```text
Login
 ↓
Validate credentials
 ↓
Generate access token
 ↓
Client sends token
 ↓
Middleware validates token
```

For web applications:

> "For sensitive applications, I prefer secure, httpOnly, SameSite cookies for token/session handling to reduce exposure to client-side JavaScript."

Don't overcomplicate authentication unless interviewer asks.

---