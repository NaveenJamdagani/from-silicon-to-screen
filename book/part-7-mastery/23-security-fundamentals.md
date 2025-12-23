# Chapter 23 — Security Fundamentals (Assume Breach)

Security is often treated as:
- A checklist
- A final step
- Someone else’s responsibility

That mindset causes breaches.

This chapter explains security as a **systems property** —  
something that must be designed in, not added on.

---

## 1. The First Rule of Security

The most important security assumption is:

> **Assume breach.**

Assume that:
- Someone will scan your system
- Credentials will leak
- Dependencies will have vulnerabilities
- Networks will be hostile

Security is about **limiting damage**, not preventing all attacks.

---

## 2. Security Is a Chain, Not a Feature

Security is only as strong as the weakest link.

Common weak links:
- Hardcoded secrets
- Over-permissioned roles
- Unvalidated input
- Exposed admin endpoints
- Insecure defaults

Attackers don’t break systems.
They **walk through open doors**.

---

## 3. Authentication vs Authorization (Frequently Confused)

### Authentication
> Who are you?

Examples:
- Passwords
- Tokens
- Certificates
- OAuth

### Authorization
> What are you allowed to do?

Examples:
- Roles
- Permissions
- Access policies

Most security bugs are **authorization bugs**, not authentication bugs.

---

## 4. Trust Boundaries (Where Attacks Happen)

A trust boundary exists whenever:
- Data crosses systems
- Data crosses processes
- Data crosses machines

Examples:
- Browser → Server
- Server → Database
- Service → Service

Every boundary must assume:
> Incoming data is malicious.

Never trust input. Ever.

---

## 5. Input Validation & Output Encoding

Classic attacks exploit:
- Missing input validation
- Unsafe output rendering

Examples:
- SQL injection
- XSS
- Command injection

Rules:
- Validate input at boundaries
- Encode output at sinks
- Never concatenate untrusted data

Most injection attacks are **design failures**.

---

## 6. OWASP Top Risks (Reality, Not Memorization)

The most common risks include:
- Injection
- Broken authentication
- Broken access control
- Sensitive data exposure
- Security misconfiguration

These persist because:
- They are easy to introduce
- They hide in plain sight
- They are rarely tested explicitly

Security failures are boring and repetitive.

---

## 7. Secrets Management (The Most Common Failure)

Secrets include:
- API keys
- Database passwords
- Tokens
- Certificates

Never:
- Commit secrets to Git
- Hardcode secrets in images
- Share secrets across environments

Secrets should be:
- Stored securely
- Rotatable
- Scoped minimally

Leaked secrets are how most breaches start.

---

## 8. Least Privilege (Power Is Dangerous)

Every component should have:
> The minimum access required to function.

Over-privileged systems:
- Amplify breaches
- Increase blast radius
- Hide bugs

Least privilege:
- Limits damage
- Improves understanding
- Forces discipline

---

## 9. Network Security Is Not Enough

Firewalls help.
VPCs help.
Private networks help.

But:
> Internal traffic is not trusted traffic.

Modern attacks:
- Move laterally
- Abuse internal APIs
- Exploit misconfigurations

Zero trust assumes:
> Every request must be authenticated and authorized.

---

## 10. Dependency Security (Your Supply Chain)

Your system includes:
- Open-source libraries
- Build tools
- Base images

Risks include:
- Known vulnerabilities
- Malicious packages
- Abandoned dependencies

Mitigations:
- Dependency scanning
- Regular updates
- Minimal dependencies

You inherit the risks of your dependencies.

---

## 11. Logging, Monitoring & Detection

Security is not just prevention.
It is detection.

You must know:
- Who accessed what
- When
- From where
- How often

Logs and alerts enable:
- Incident response
- Forensics
- Accountability

Silent breaches are the worst kind.

---

## 12. Secure Defaults Beat Secure Options

Systems should be:
- Secure by default
- Unsafe only with intent

If security requires:
> “Remembering to enable it”

It will be forgotten.

Design defaults that protect users.

---

## 13. Security vs Usability (The Tradeoff)

Perfect security is unusable.
Perfect usability is insecure.

Good systems:
- Balance friction and protection
- Protect users from catastrophic mistakes
- Accept small risks for usability

Security is risk management, not absolutism.

---

## 14. Incident Response (When Things Go Wrong)

Breaches will happen.

Prepared teams have:
- Clear escalation paths
- Kill switches
- Credential rotation plans
- Communication playbooks

Chaos during incidents multiplies damage.

Practice matters.

---

## 15. Interview Lens

Interviewers ask:
- How do you secure APIs?
- How do you handle secrets?
- How do you prevent common attacks?

They are testing:
> Whether you think in threat models.

---

## 16. Production Lens

Real-world security failures include:
- Publicly exposed databases
- Overly permissive IAM roles
- Forgotten debug endpoints
- Expired certificates

Most breaches are **configuration mistakes**, not hacks.

---

## 17. Common Myths (Destroyed)

❌ “Security is the security team’s job”  
✅ Security is everyone’s job

❌ “We’ll add security later”  
✅ Later is too late

❌ “No one will target us”  
✅ Automated bots don’t care who you are

---

## 18. The Mental Model (Memorize This)

> Security assumes failure,  
> limits blast radius,  
> and detects problems early.

If you design for breach,
you build resilient systems.

---

## Continue Reading

➡️ **Next:**  
[Chapter 24 — Observability](./24-observability.md)

⬅️ **Previous:**  
[Chapter 22 — CI/CD & Deployment](../part-6-devops/22-ci-cd-and-deployment.md)
