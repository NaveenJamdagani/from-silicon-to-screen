# Chapter 10 — Mobile Apps (iOS & Android Reality)

If the browser is complex,  
**mobile apps are hostile territory**.

On mobile:
- Resources are limited
- Networks are unstable
- Apps are disposable
- The OS is aggressive

This chapter explains why **mobile engineering is fundamentally different** from web and backend.

---

## 1. The Core Difference

On desktop and servers:
> Your program usually controls its lifetime.

On mobile:
> **The OS owns your app.**

You are a guest.
You can be paused, stopped, or killed at any time.

---

## 2. Mobile Is an OS-First World

Mobile operating systems (iOS, Android) are designed to:
- Protect battery
- Protect memory
- Protect user experience

They aggressively:
- Suspend background work
- Kill memory-hungry apps
- Restrict networking
- Limit CPU usage

If your app misbehaves, it dies.

---

## 3. Mobile App Lifecycle (Critical Concept)

A mobile app does **not** just “run”.

Typical lifecycle states:
- Not running
- Launching
- Foreground (active)
- Background (paused)
- Suspended
- Terminated

Transitions can happen:
- Due to user action
- Due to OS decisions
- Without warning

Assuming continuous execution is a bug.

---

## 4. Foreground vs Background

### Foreground
- UI visible
- Full CPU access (still limited)
- Network allowed
- User expects responsiveness

### Background
- Execution time is restricted
- Network may be paused
- Timers may not fire
- App may be killed anytime

Background work is **permission-based**, not guaranteed.

---

## 5. Memory: The Silent Executioner

Mobile devices have:
- Far less RAM than servers
- Strict per-app limits
- Aggressive memory reclaiming

When memory pressure increases:
- The OS kills background apps first
- Then foreground apps
- No exceptions

Your app must:
- Release memory aggressively
- Avoid large in-memory caches
- Handle restarts gracefully

Memory leaks = app death.

---

## 6. Networking on Mobile Is Hostile

Mobile networks:
- Drop connections frequently
- Change IPs constantly
- Switch between Wi-Fi and cellular
- Experience high latency and packet loss

Implications:
- Requests fail mid-flight
- TCP connections break
- Retries are mandatory
- Idempotency is critical

Assume the network will fail.
Because it will.

---

## 7. Offline-First Is Not Optional

On mobile:
> Offline is a normal state, not an edge case.

Good mobile apps:
- Cache data locally
- Queue writes
- Sync opportunistically
- Resolve conflicts

Bad mobile apps:
- Assume connectivity
- Block UI on network
- Lose user trust

Offline-first is a **design philosophy**, not a feature.

---

## 8. Push Notifications: OS-Controlled Power

Push notifications:
- Are delivered by the OS
- Not by your app
- Can wake your app briefly
- May be delayed or dropped

They are:
- Battery-sensitive
- Rate-limited
- User-controlled

Push is a privilege.
Abuse it, and users uninstall your app.

---

## 9. Battery Is the Real Currency

Every operation costs:
- CPU cycles
- Network radio usage
- Wake locks
- Screen time

Battery drain correlates with:
- Excessive background work
- Frequent network calls
- Poor lifecycle handling

Users forgive bugs.
They do not forgive battery drain.

---

## 10. JavaScript in Mobile Apps

In hybrid apps (React Native, etc.):
- JavaScript runs in a runtime
- Bridged to native code
- Subject to lifecycle constraints

Blocking JS:
- Freezes UI
- Delays gestures
- Triggers OS penalties

Same JS rules.
Stricter consequences.

---

## 11. Security on Mobile

Mobile OSes enforce:
- App sandboxing
- Permission prompts
- Secure storage APIs

But risks still exist:
- Insecure local storage
- Hardcoded secrets
- Network interception

Never trust the device.
Never trust the network.

---

## 12. Mobile vs Web vs Backend (Reality Check)

### Web
- Tabs are isolated
- Reload is normal
- Crashes are acceptable

### Backend
- Long-lived processes
- Stable networks
- Predictable resources

### Mobile
- Short-lived execution
- Unstable networks
- Aggressive OS control

Same architecture assumptions **do not transfer**.

---

## 13. Common Myths (Destroyed)

❌ “Mobile is just web with a smaller screen”  
✅ Mobile is OS-constrained computing

❌ “Background tasks always run”  
✅ Background tasks are conditional

❌ “More retries fix mobile networking”  
✅ Bad retries drain battery and worsen UX

---

## 14. Interview Lens

Interviewers ask:
- How do you handle offline?
- How do you handle app restarts?
- How do you manage background work?

They’re testing:
> Do you respect the mobile OS?

---

## 15. Production Lens

Most mobile production issues involve:
- Crashes after backgrounding
- Lost user actions
- Battery complaints
- Network edge cases

These are **lifecycle bugs**, not UI bugs.

---

## 16. The Mental Model (Memorize This)

> On mobile, your app is temporary.  
> State must be saved.  
> Work must be resumable.  
> Failure must be expected.

Once you accept this,
mobile architecture becomes clear.

---

## Continue Reading

➡️ **Next:**  
[Chapter 11 — Desktop Apps](./11-desktop-apps.md)

⬅️ **Previous:**  
[Chapter 9 — JavaScript Runtimes (Browser vs Node)](./09-javascript-runtimes.md)
