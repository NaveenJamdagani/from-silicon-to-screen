# Chapter 18 — Databases (Real Understanding, No Myths)

Databases are where **systems either survive or die**.

Most developers know:
- How to write queries
- How to use an ORM
- How to add indexes

Very few understand:
> **What databases actually do and why they behave the way they do.**

This chapter builds a real mental model of databases as **systems under constraints**.

---

## 1. Why Databases Exist at All

If memory is fast, why not store everything in RAM?

Because data must:
- Survive crashes
- Survive restarts
- Survive power loss
- Be shared across machines

Databases exist to solve:

> **Durable, consistent storage under concurrent access.**

That problem is much harder than it sounds.

---

## 2. A Database Is Not Just Storage

A database is not:
- A JSON store
- A file
- A cache

A database is a system that provides:
- Persistence
- Concurrency control
- Query execution
- Indexing
- Recovery
- Integrity guarantees

Every feature has a cost.

---

## 3. Reads, Writes & the Cost Asymmetry

Databases optimize for:
- Fast reads
- Controlled writes

Why?
- Writes must be durable
- Writes must be ordered
- Writes must be recoverable

Reads can be cached.
Writes cannot be faked.

This asymmetry defines database behavior.

---

## 4. Transactions: The Foundation of Correctness

A transaction is:
> A group of operations treated as a single unit.

Transactions exist to prevent:
- Partial updates
- Inconsistent reads
- Data corruption

Without transactions:
> Concurrency destroys correctness.

---

## 5. ACID (What It Actually Means)

ACID is often memorized and forgotten.

Here’s what it really means:

- **Atomicity**  
  All operations succeed or none do.

- **Consistency**  
  Data moves from one valid state to another.

- **Isolation**  
  Concurrent transactions don’t interfere.

- **Durability**  
  Once committed, data survives crashes.

Every database makes **tradeoffs** around these guarantees.

---

## 6. Isolation Levels (Why Bugs Appear Under Load)

Isolation is not binary.

Common isolation issues:
- Dirty reads
- Non-repeatable reads
- Phantom reads

Higher isolation:
- Improves correctness
- Reduces concurrency
- Hurts performance

Lower isolation:
- Improves throughput
- Introduces anomalies

Most production bugs only appear **under concurrency**.

---

## 7. Indexes: Speed Through Structure

Indexes exist to:
> Avoid scanning all data.

Indexes:
- Trade write speed for read speed
- Consume memory and disk
- Must be maintained on every write

Too few indexes:
- Slow reads

Too many indexes:
- Slow writes

Indexes are architectural decisions.

---

## 8. Query Execution Is a Plan, Not Magic

When you run a query:
- The database parses it
- Builds a query plan
- Chooses indexes
- Executes steps

The planner may choose:
- Nested loops
- Hash joins
- Index scans
- Full scans

Understanding plans explains:
> Why the same query behaves differently over time.

---

## 9. SQL vs NoSQL (The Real Difference)

The real difference is not syntax.

### SQL Databases
- Strong consistency
- Structured schema
- Powerful queries
- Transactions

### NoSQL Databases
- Flexible schema
- Horizontal scaling
- Simpler access patterns
- Eventual consistency (often)

Neither is “better”.
They solve different constraints.

---

## 10. Normalization (1NF, 2NF, 3NF)

Normalization exists to:
> Eliminate redundancy and inconsistency.

- **1NF** — Atomic values
- **2NF** — No partial dependency
- **3NF** — No transitive dependency

Normalized data:
- Saves space
- Improves integrity

Denormalized data:
- Improves read speed
- Adds complexity

This is a **deliberate tradeoff**, not dogma.

---

## 11. Concurrency Control: Locks vs MVCC

Databases must handle many users at once.

Common strategies:
- Locks (block others)
- MVCC (multiple versions of data)

MVCC allows:
- Readers without blocking writers
- Higher concurrency
- More memory usage

This is why modern databases scale better.

---

## 12. Replication: Availability vs Consistency

Replication exists to:
- Increase availability
- Improve read scalability
- Provide redundancy

But replication introduces:
- Replication lag
- Inconsistent reads
- Complex failure modes

Distributed databases are **coordination problems**.

---

## 13. Sharding: Scaling by Partitioning

Sharding splits data across machines.

Pros:
- Horizontal scalability
- Larger datasets

Cons:
- Complex queries
- Cross-shard transactions
- Operational difficulty

Sharding is a **last resort**, not a default.

---

## 14. Backups & Recovery (Ignored Until Disaster)

Backups are:
- Slow
- Boring
- Essential

Important truths:
- Backups must be tested
- Replication is not backup
- Snapshots can be corrupted

Recovery time matters more than backup time.

---

## 15. Databases in Production Reality

Most database outages involve:
- Lock contention
- Slow queries
- Index misuse
- Disk saturation
- Replication lag

Frameworks do not save you here.
Understanding does.

---

## 16. Interview Lens

Interviewers ask:
- SQL vs NoSQL?
- How do indexes work?
- What is isolation?
- How do transactions behave?

They are testing:
> Whether you understand data as a system.

---

## 17. Common Myths (Destroyed)

❌ “Databases are slow”  
✅ Databases are careful

❌ “ORMs abstract databases”  
✅ ORMs hide costs

❌ “Scaling DBs is easy in the cloud”  
✅ Scaling coordination is hard everywhere

---

## 18. The Mental Model (Memorize This)

> Databases trade speed for correctness,  
> coordination for consistency,  
> and simplicity for guarantees.

If you respect these tradeoffs,
databases become predictable.

---

## Continue Reading

➡️ **Next:**  
[Chapter 19 — From Laptop to Production](../part-6-devops/19-from-laptop-to-production.md)

⬅️ **Previous:**  
[Chapter 17 — APIs & Communication](./17-apis-and-communication.md)
