
# 12. Horizontal scaling

Suppose:

```text
1 Node server
      ↓
1000 req/sec
```

Traffic becomes:

```text
10,000 req/sec
```

Don't make one server bigger forever.

Instead:

```text
             Load Balancer
          /       |       \
         /        |        \
      Node1     Node2     Node3
```

This is:

> **Horizontal Scaling**

Memory trick:

```text
Vertical = Bigger machine
Horizontal = More machines
```