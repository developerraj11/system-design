# 10. But what if Redis goes down?

🔥 Very important follow-up.

Don't say:

> "System will fail."

Say:

> "Redis should be treated as a cache, not the source of truth. If Redis is unavailable, the application can fall back to MongoDB. We may see higher latency and database load, but the system should continue serving requests."

Architecture:

```text
             Node
              │
         ┌────▼────┐
         │  Redis  │
         └────┬────┘
              │
          Cache Miss
              │
              ▼
          MongoDB
```

This is a **very important Senior-level answer**.
