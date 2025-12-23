# Chapter 12 — Frontend Architecture (Systems, Not Frameworks)

Frontend architecture is often misunderstood.

People argue about:
- React vs Vue
- Redux vs Zustand
- Tailwind vs CSS

But architecture lives **above frameworks**.

This chapter explains:
- How frontend systems are structured
- Why rendering strategies exist
- How decisions affect performance, scalability, and UX

Frameworks come and go.  
Architectural tradeoffs remain.

---

## 1. What Frontend Architecture Really Means

Frontend architecture answers questions like:
- Where does data live?
- When does rendering happen?
- How is state shared?
- How do we scale teams and features?

It is **not** about components.
It is about **flows, boundaries, and constraints**.

---

## 2. The Core Problem of Frontend Systems

Frontend systems must balance:
- Performance
- Interactivity
- Maintainability
- Scalability
- SEO
- Security

These goals **conflict**.

Every architecture is a compromise.

---

## 3. Rendering Strategies (The Big Axis)

Rendering answers one question:

> **When and where do we generate HTML?**

The major strategies are:
- Client-Side Rendering (CSR)
- Server-Side Rendering (SSR)
- Static Site Generation (SSG)
- Hybrid approaches

Understanding these is foundational.

---

## 4. Client-Side Rendering (CSR)

CSR means:
- Browser loads minimal HTML
- JavaScript builds the UI
- Data is fetched after load

Pros:
- Rich interactivity
- Simple backend
- Fast transitions

Cons:
- Slower first paint
- SEO challenges
- Heavy JS payloads

CSR prioritizes **interaction over initial speed**.

---

## 5. Server-Side Rendering (SSR)

SSR means:
- Server generates HTML per request
- Browser receives ready-to-render content
- JavaScript hydrates afterward

Pros:
- Faster first content
- Better SEO
- Predictable performance

Cons:
- Server load increases
- Complexity grows
- Caching is harder

SSR trades server complexity for user experience.

---

## 6. Static Site Generation (SSG)

SSG means:
- HTML is generated at build time
- Files are served via CDN
- No server computation per request

Pros:
- Extremely fast
- Cheap to host
- Highly cacheable

Cons:
- Limited dynamic content
- Build times increase
- Personalization is harder

SSG optimizes for **speed and scale**.

---

## 7. Hydration: The Hidden Cost

Hydration is:
> Attaching JavaScript behavior to existing HTML.

Costs:
- JavaScript execution
- Event binding
- State reconstruction

Hydration explains:
- Why SSR still needs JS
- Why heavy pages feel slow
- Why partial hydration exists

HTML without JS is incomplete for apps.

---

## 8. Data Fetching Architecture

Frontend systems must decide:
- Who fetches data?
- When is data fetched?
- How is it cached?

Common patterns:
- Fetch on client
- Fetch on server
- Fetch at build time
- Edge fetching

Poor data strategy causes:
- Waterfalls
- Over-fetching
- Inconsistent state

---

## 9. State Management (Not a Library Problem)

State exists at multiple levels:
- Local component state
- Shared UI state
- Server state
- URL state

Architecture decides:
- What belongs where
- What is ephemeral
- What must persist

Most state bugs are **architectural**, not tooling issues.

---

## 10. Micro-Frontends (When Systems Get Big)

Micro-frontends split:
- Teams
- Codebases
- Deployment units

Pros:
- Team autonomy
- Independent releases
- Organizational scaling

Cons:
- Performance overhead
- Shared state complexity
- Operational burden

Micro-frontends solve **org problems**, not tech problems.

---

## 11. Frontend as a Distributed System

Modern frontends involve:
- CDNs
- Edge caches
- APIs
- Feature flags
- A/B experiments

Failures include:
- Cache inconsistency
- Partial outages
- Version mismatches

Frontend systems are **distributed systems**.

---

## 12. Performance as an Architectural Concern

Performance is shaped by:
- Rendering strategy
- Bundle boundaries
- Data fetching
- Caching layers

You cannot “optimize later” what architecture broke.

Performance must be designed in.

---

## 13. Security Implications

Frontend architecture affects:
- XSS exposure
- Data leakage
- Token storage
- Attack surface

Choices like:
- Where secrets live
- What runs on client
- What is server-only

are security decisions.

---

## 14. Common Myths (Destroyed)

❌ “Framework choice defines architecture”  
✅ Architecture defines framework usage

❌ “SSR is always better”  
✅ SSR is a tradeoff

❌ “State management is a library problem”  
✅ State management is a design problem

---

## 15. Interview Lens

Interviewers ask:
- Why CSR vs SSR?
- How do you handle SEO?
- How do you scale frontend teams?

They are testing:
> Your ability to reason about tradeoffs.

---

## 16. Production Lens

Real-world frontend failures involve:
- Over-hydration
- Cache invalidation bugs
- Data fetching waterfalls
- Unbounded bundles

These are **system failures**, not component bugs.

---

## 17. The Mental Model (Memorize This)

> Frontend architecture is about  
> **when**, **where**, and **how**  
> UI and data come together.

Once you see this,
framework debates become secondary.

---

## Continue Reading

➡️ **Next:**  
[Chapter 13 — React Explained Properly](./13-react-explained-properly.md)

⬅️ **Previous:**  
[Chapter 11 — Desktop Apps](../part-3-clients/11-desktop-apps.md)
