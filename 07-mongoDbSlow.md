
# 11. What if MongoDB becomes slow?

Interviewer:

> "MongoDB query is taking 2 seconds. What will you do?"

Answer in layers:

### First

```text
Check query
```

### Then

```text
Check indexes
```

### Then

```text
explain()
```

### Then

```text
Optimize schema/query
```

### Then

```text
Read replicas
```

### Then, at very large scale:

```text
Sharding
```

Interview answer:

> "I wouldn't immediately introduce sharding. First I would analyze the query using explain, verify indexes, optimize the query and schema, and then consider read replicas or sharding depending on the workload."

🔥 This is a **Lead-level mindset**: don't over-engineer.

---