# Chapter 7 — DNS, HTTPS & Trust

So far, we understand:
- Computers talk using packets
- IP addresses identify machines
- TCP makes communication reliable

But there is still a massive gap.

You don’t visit:
https://142.250.195.46


You visit:
https://google.com


And you trust it.

This chapter explains **how names become machines**  
and **how trust is established on a hostile network**.

---

## 1. The Core Problems

Two fundamental problems must be solved before the web can exist:

1. **Naming** — How do humans find machines?
2. **Trust** — How do we know we’re talking to the right machine?

The answers are:
- DNS (Domain Name System)
- HTTPS (HTTP + TLS)

---

## 2. DNS: The Internet’s Phone Book

DNS exists for one reason:

> **Humans remember names. Computers route using numbers.**

DNS translates:
google.com → 142.250.195.46


That’s it.

DNS does **not**:
- Encrypt traffic
- Verify identity
- Guarantee availability

It only answers:
> “What IP corresponds to this name?”

---

## 3. The DNS Resolution Journey (Step by Step)

When you type `google.com` in a browser:

1. Browser checks its DNS cache
2. OS checks its DNS cache
3. Router may check its cache
4. Query goes to a recursive DNS resolver
5. Resolver asks root servers
6. Root points to TLD servers (`.com`)
7. TLD points to authoritative server
8. Authoritative server returns IP
9. Result is cached at multiple layers

This entire process usually happens in **milliseconds**.

Caching is what makes DNS usable.

---

## 4. DNS Is Distributed by Design

There is:
- No central DNS server
- No single point of failure

DNS works because:
- Responsibility is delegated
- Caches reduce load
- Failures are tolerated

But DNS is also:
- A common point of outage
- A frequent attack surface

If DNS fails:
> The internet appears “down”.

---

## 5. DNS Has No Trust

Critical truth:

> **DNS does not prove identity.**

DNS answers:
- “This name maps to this IP”

DNS does NOT answer:
- “This server is legitimate”
- “This server is safe”
- “This server is who it claims to be”

That problem is solved by **TLS**.

---

## 6. HTTP Is Insecure by Default

Plain HTTP means:
- Data is readable by anyone on the path
- Data can be modified
- Identity can be spoofed

On the open internet:
> HTTP is unacceptable.

This is why HTTPS is mandatory.

---

## 7. TLS: Establishing Trust on an Untrusted Network

TLS (Transport Layer Security) solves three problems:

1. **Encryption** — Prevents eavesdropping
2. **Integrity** — Prevents tampering
3. **Authentication** — Verifies identity

TLS does this **before HTTP even starts**.

---

## 8. Certificates: Proof of Identity

A TLS certificate:
- Is issued by a trusted Certificate Authority (CA)
- Binds a domain name to a public key
- Is cryptographically signed

When your browser sees a certificate, it asks:
> “Do I trust the authority that signed this?”

If yes:
- The connection proceeds
If no:
- You see a warning
- Or the connection is blocked

Trust is delegated, not assumed.

---

## 9. The TLS Handshake (Conceptual)

During the TLS handshake:
1. Client and server agree on encryption algorithms
2. Server proves its identity using a certificate
3. Keys are exchanged securely
4. Encrypted communication begins

Only **after this** does HTTP data flow.

HTTPS is:
HTTP
inside TLS
inside TCP
inside IP


Layered trust.

---

## 10. Why HTTPS Is Not Optional

HTTPS protects against:
- Man-in-the-middle attacks
- ISP inspection
- Public Wi-Fi attacks
- Data manipulation

Modern browsers:
- Mark HTTP as “Not Secure”
- Block sensitive features
- Penalize insecure sites

HTTPS is now **table stakes**.

---

## 11. Frontend, Backend, Mobile Implications

### Frontend
- HTTPS enables modern APIs
- Mixed content is blocked
- Performance depends on TLS reuse

### Backend
- Certificates expire
- Misconfiguration causes outages
- Trust chains must be correct

### Mobile
- Certificate pinning may be used
- Clock skew breaks TLS
- Network interception is common

Security is fragile.

---

## 12. Common Myths (Destroyed)

❌ “HTTPS makes apps slow”  
✅ TLS is fast when configured correctly

❌ “DNS is just a lookup”  
✅ DNS failures break everything

❌ “Certificates are just files”  
✅ Certificates are trust contracts

---

## 13. Interview Lens

Interviewers ask:
- Why HTTPS is required
- How DNS works
- Why cert expiry breaks apps

They’re testing:
> Your understanding of trust, not syntax.

---

## 14. Production Lens

Production outages often involve:
- Expired certificates
- DNS misconfiguration
- Incorrect TLS chains
- Clock drift

Most “mysterious” outages are trust failures.

---

## 15. The Mental Model (Memorize This)

> DNS finds the machine.  
> TLS proves its identity.  
> HTTPS protects the conversation.

Without trust,
the internet is unusable.

---

## Continue Reading

➡️ **Next:**  
[Chapter 8 — Browser Internals](../part-3-clients/08-browser-internals.md)

⬅️ **Previous:**  
[Chapter 6 — TCP/IP Without Fear](./06-tcp-ip-without-fear.md)
