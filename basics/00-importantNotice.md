
# 18. VERY IMPORTANT: How YOU should answer

A common mistake is:

❌

> "We use Redis, Kafka, MongoDB, Kubernetes, API Gateway, Load Balancer, Elasticsearch..."

This sounds like **technology name-dropping**.

Instead:

### Problem

```text
Read traffic is high
```

### Reasoning

```text
Repeated DB queries are expensive
```

### Solution

```text
Redis cache
```

### Trade-off

```text
Cache can become stale
```

That's system design thinking.

---

# 19. Your interview answer structure

Whenever interviewer gives you a new problem, start:

> **"Sure. I'll start by clarifying the requirements, then I'll define the scale and traffic assumptions. After that I'll design the high-level architecture, discuss database and caching strategy, and finally cover scalability, reliability, security and failure scenarios."**

This one sentence gives you a **structured starting point**.