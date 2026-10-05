
# 4. Scenario #1 — URL Shortener

Ye humara first complete system design hoga because isme almost saare fundamentals aa jaate hain.

### Interviewer:

> "Design a URL shortening service like Bitly."

---

## Step 1 — Requirements

Aap bolo:

> "Before designing, I would clarify the requirements."

### Functional

```text
POST /urls
GET /:shortCode
```

Example:

```text
https://myapp.com/abc123
             ↓
https://google.com/some/very/long/url
```

### Non-functional

```text
High read traffic
Low latency
High availability
Scalable
Unique short URLs
```

---

# 5. Step 2 — Traffic estimation

Interviewer agar numbers na de to reasonable assumption karo.

Example:

```text
10 million URLs/day
Read : Write = 100 : 1
```

Therefore:

```text
Writes = 10M/day

Reads ≈ 1B/day
```

Approximate:

```text
1B / 86,400
≈ 11,574 requests/sec
```

Interview mein exact calculation se zyada important hai:

> "This is a read-heavy system, so caching will be important."

🔥 **This sentence interviewer ko signal deta hai ki aap architecture ko traffic pattern ke according design kar rahe ho.**

---

# 6. Step 3 — High Level Design

```text
                    Client
                       │
                       ▼
                ┌─────────────┐
                │Load Balancer│
                └──────┬──────┘
                       │
            ┌──────────┼──────────┐
            ▼          ▼          ▼
         Node-1     Node-2     Node-3
            │          │          │
            └──────────┼──────────┘
                       │
                ┌──────▼──────┐
                │    Redis    │
                │    Cache    │
                └──────┬──────┘
                       │ Cache Miss
                       ▼
                ┌─────────────┐
                │   MongoDB   │
                └─────────────┘
```

---

# 7. Request flow

### URL create

```text
Client
  ↓
POST /urls
  ↓
Load Balancer
  ↓
Node.js
  ↓
Generate shortCode
  ↓
MongoDB
  ↓
Return short URL
```

### URL redirect

```text
Client
  ↓
GET /abc123
  ↓
Node.js
  ↓
Redis?
 ┌───────┴───────┐
 HIT             MISS
 ↓                ↓
URL             MongoDB
 ↓                ↓
Redirect         Redis
                  ↓
                Redirect
```

### Interview-ready explanation

> "For redirects, I would first check Redis because URL resolution is read-heavy. If the short code exists in cache, we can avoid a database call and directly redirect the user. On cache miss, we query MongoDB and populate Redis."

---

# 8. MongoDB schema

```javascript
{
  _id: ObjectId,
  shortCode: "abc123",
  originalUrl: "https://example.com/very-long-url",
  createdAt: Date,
  expiresAt: Date
}
```

Index:

```javascript
{
  shortCode: 1
}
```

And it should be:

```text
UNIQUE
```

### Interview line

> "Since shortCode is used for lookup, I would create a unique index on shortCode."

---

# 9. Why Redis?

Interviewer:

> "Why Redis?"

Answer:

> "Because URL redirection is highly read-heavy. Redis provides low-latency in-memory access and reduces repeated database queries."

Memory trick:

> **Redis = FAST READ + REDUCE DB LOAD**

---