
# 13. Why Node.js works well here?

Since you're a Node developer, interviewer may ask.

Answer:

> "Node.js is suitable for I/O-heavy systems because its event-driven, non-blocking architecture allows a server to handle many concurrent requests efficiently. For CPU-heavy operations, I would offload work to workers or separate services."

🔥 Important distinction:

```text
I/O heavy → Node.js good

CPU heavy → Worker / separate service
```