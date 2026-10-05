# 2. System Design ka basic architecture

MERN developer ke liye initially architecture ko is tarah visualize karo:

```text
                    ┌──────────────┐
                    │    Client    │
                    │ React / Web  │
                    └──────┬───────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ Load Balancer   │
                  └────────┬────────┘
                           │
             ┌─────────────┼─────────────┐
             ▼             ▼             ▼
        ┌─────────┐   ┌─────────┐   ┌─────────┐
        │ Node #1 │   │ Node #2 │   │ Node #3 │
        │ Express │   │ Express │   │ Express │
        └────┬────┘   └────┬────┘   └────┬────┘
             │             │             │
             └─────────────┼─────────────┘
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ▼                           ▼
        ┌──────────┐                ┌──────────┐
        │  Redis   │                │ Database │
        │  Cache   │                │ MongoDB  │
        └──────────┘                └──────────┘
```

Ye **starting point** hai. Har system mein ye exact architecture nahi lagega.