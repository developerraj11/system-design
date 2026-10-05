
# 16. Rate Limiting

Interviewer:

> "How will you protect POST /urls from abuse?"

Architecture:

```text
Client
  ↓
Load Balancer
  ↓
Rate Limiter
  ↓
Node.js
```

Redis can maintain counters.

Example:

```text
User A
100 requests/minute
```

After limit:

```text
HTTP 429 Too Many Requests
```

Interview line:

> "I would implement distributed rate limiting using Redis so that limits are shared across multiple Node.js instances."

### Example of rate limit in node and express

```js
import rateLimit from "express-rate-limit";

const rateLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 20, // limit each IP to 3 requests per windowMs
  message: {
    message:
      "Too many requests from this IP, please try again after 15 minutes.",
    success: false,
  },
  standardHeaders: true, // Return rate limit info in the `RateLimit-*` headers
  legacyHeaders: false, // Disable the `X-RateLimit-*` headers
});

export default rateLimiter;


```