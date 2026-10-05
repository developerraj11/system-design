
# 14. Stateless Node.js

Suppose we have:

```text
Node1
Node2
Node3
```

Any request should be able to go to any instance.

Avoid:

```text
Node1 memory = user session
```

Instead use:

```text
JWT
Redis
Database
```

Architecture:

```text
             Load Balancer
             /     |     \
           N1      N2      N3
             \     |     /
                Redis
```

Interview line:

> "I would keep application servers stateless so that requests can be routed to any instance and we can horizontally scale easily."