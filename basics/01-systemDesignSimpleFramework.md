# 1. Sabse pehle — System Design ka simple framework

Har question mein ye **10-step framework** yaad rakho:

### 🧠 R-E-A-C-T-S-C-A-L-E

| Step  | Kya karna hai | Interview mein bolo |
|-------|---------------|---------------------|
| **R** | Requirements  | "First, let me clarify functional and non-functional requirements." |
| **E** | Estimation    | "Let's assume around X users/requests per second." |
| **A** | APIs          | "I would expose APIs like..." |
| **C** | Components    | "At high level, the architecture will have..." |
| **T** | Technology    | "For this use case, I would choose..." |
| **S** | Storage       | "For persistent data, I would use..." |
| **C** | Cache         | "Since this is read-heavy, I would introduce Redis..." |
| **A** | Availability  | "We need redundancy and horizontal scaling..." |
| **L** | Load/Latency  | "Load balancer distributes traffic..." |
| **E** | Edge cases    | "Now let's discuss failures, consistency and security." |

**Interview trick:** Agar nervous ho jao, bas **REACT-SCALE** follow karo. Architecture automatically develop hone lagega.