
Reverse proxies handle:
- TLS termination
- Load balancing
- Request routing
- Rate limiting
- Static assets

Examples:
- Nginx
- Envoy
- HAProxy

Your server is usually **behind** something.

---

## 10. Stateless vs Stateful Servers

### Stateless
- No memory of previous requests
- Easy to scale
- Failures are cheap

### Stateful
- Session memory
- In-memory caches
- Harder to scale
- Failures are expensive

Modern backend design favors **stateless servers**  
and moves state elsewhere.

---

## 11. Servers Are Disposable (By Design)

In modern systems:
- Servers crash
- Servers restart
- Servers are replaced

Good systems assume:
> Any server can disappear at any time.

If your server must stay alive to work,
your system is fragile.

---

## 12. The “Cloud Server” Illusion

Cloud servers are:
- Still computers
- Still running OSes
- Still finite

The cloud adds:
- Automation
- APIs
- Elasticity

It does **not** remove:
- Latency
- Failures
- Resource limits

Cloud makes servers easier to manage,
not magical.

---

## 13. Frontend–Backend Boundary

From the frontend’s perspective:
- A server is a URL
- That returns data
- With latency and failure

From the backend’s perspective:
- Clients are unreliable
- Requests spike
- Timeouts happen

Design lives at this boundary.

---

## 14. Common Myths (Destroyed)

❌ “Servers are always running”  
✅ Servers are frequently restarted

❌ “One server handles everything”  
✅ Servers specialize

❌ “Cloud servers don’t crash”  
✅ They crash faster, automatically

---

## 15. Interview Lens

Interviewers ask:
- What is a server?
- How does it scale?
- What happens under load?
- What happens when it crashes?

They want to see:
> Whether you think in systems, not endpoints.

---

## 16. Production Lens

Real-world server issues include:
- Thread exhaustion
- Connection limits
- Memory leaks
- Slow I/O cascading failures

These are **resource management failures**.

---

## 17. The Mental Model (Memorize This)

> A server is a program that listens,  
> executes under constraints,  
> and must survive failure.

Everything else is infrastructure.

---

## Continue Reading

➡️ **Next:**  
[Chapter 16 — Node.js Internals](./16-nodejs-internals.md)

⬅️ **Previous:**  
[Chapter 14 — Frontend Performance](../part-4-frontend/14-frontend-performance.md)
