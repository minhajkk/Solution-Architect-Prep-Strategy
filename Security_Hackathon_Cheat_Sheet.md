# 🛡️ Security Hackathon Cheat Sheet (For Solution Architects)

---

## 🔍 1. Reconnaissance (Information Gathering)

**Goal:** Enumerate domains, subdomains, IPs, services, technologies.

### 🔧 Web-Based Recon Tools

| Task              | Tool/Portal                                                                 |
|-------------------|------------------------------------------------------------------------------|
| DNS Enumeration   | [HackerTarget DNS Lookup](https://hackertarget.com/dns-lookup/)             |
| Subdomain Finder  | [crt.sh](https://crt.sh), [Pentest-Tools](https://pentest-tools.com)        |
| WHOIS Lookup      | [HackerTarget WHOIS](https://hackertarget.com/whois-lookup/)                |
| IP Info           | [SecurityTrails](https://securitytrails.com), [IPinfo](https://ipinfo.io)   |
| Port Scanning     | [HackerTarget Nmap](https://hackertarget.com/nmap-online-port-scanner/)     |
| Tech Stack        | [Wappalyzer](https://wappalyzer.com), [BuiltWith](https://builtwith.com)    |
| SSL/TLS Check     | [SSL Labs](https://www.ssllabs.com/ssltest), [DigiCert Tools](https://ssltools.digicert.com) |
| Header Analysis   | [SecurityHeaders.com](https://securityheaders.com)                          |
| WAF Detection     | [Pentest-Tools](https://pentest-tools.com)                                  |

---

## 🕵️‍♂️ 2. OWASP Top 10 Testing Summary

Test for vulnerabilities across the most common OWASP categories.

### Example Focus Areas

- **A1: Broken Access Control** – ID tampering, role abuse
- **A2: Cryptographic Failures** – Weak TLS, exposed cookies
- **A3: Injection** – SQLi, XSS, Command Injection
- **A5: Security Misconfiguration** – Default creds, open dirs
- **A6: Vulnerable Components** – Outdated libraries
- **A7: Identification & Authentication Failures** – Weak login/session logic
- **A10: SSRF** – Internal network access via user input

---

### **1. Broken Access Control**

**What It Means:** Unauthorized users can access restricted resources or perform actions beyond their role.

**🔍 Example:**
- URL: `https://app.com/admin/view?user=123`
- Try changing `user=123` to another user ID.
- Try accessing `/admin/` as a normal user.

**🔧 Tools:** Browser + DevTools, Hoppscotch

**✅ Fix:** Enforce access control server-side (RBAC/ABAC).

---

### **2. Cryptographic Failures**

**What It Means:** Insecure data in transit or at rest due to weak/missing encryption.

**🔍 Example:**
- App using HTTP instead of HTTPS.
- Cookies missing `Secure` or `HttpOnly` flags.
- Weak TLS configuration.

**🔧 Tools:** [SSL Labs](https://ssllabs.com/ssltest), [SecurityHeaders](https://securityheaders.com)

**✅ Fix:** Use strong TLS, secure cookies, encrypt sensitive data.

---

### **3. Injection (SQLi, XSS, etc.)**

**What It Means:** Attacker injects malicious input into queries or scripts.

**🔍 Example:**
- Input field: `username` → try `admin'--`
- Search box: `<script>alert('xss')</script>`

**🔧 Tools:** [ReqBin](https://reqbin.com), [Hoppscotch](https://hoppscotch.io)

**✅ Fix:** Parameterized queries, input sanitization, content encoding.

---

### **4. Insecure Design**

**What It Means:** Architectural flaws due to lack of threat modeling or secure patterns.

**🔍 Example:**
- Password reset links don’t expire.
- Sensitive operations (delete, wire transfer) don’t require re-authentication.

**✅ Fix:** Apply threat modeling early, enforce secure design patterns.

---

### **5. Security Misconfiguration**

**What It Means:** Default settings, unnecessary features, or improper error handling.

**🔍 Example:**
- Stack trace shown on error.
- Exposed `.git/` folder or `/admin/` panel.
- X-Powered-By header leaks tech stack.

**🔧 Tools:** [SecurityHeaders](https://securityheaders.com), [Wappalyzer](https://wappalyzer.com)

**✅ Fix:** Harden configurations, disable debug/error output, minimal exposure.

---

### **6. Vulnerable and Outdated Components**

**What It Means:** Using old libraries/frameworks with known CVEs.

**🔍 Example:**
- Detect jQuery 1.x or Log4j in frontend/backend.
- Use CVE search engines or SCA tools.

**🔧 Tools:** [BuiltWith](https://builtwith.com), [Wappalyzer](https://wappalyzer.com)

**✅ Fix:** Regular dependency scanning and patching (e.g. `npm audit`, `snyk`).

---

### **7. Identification and Authentication Failures**

**What It Means:** Login and session handling is insecure.

**🔍 Example:**
- Try brute-force login (`admin/admin`, `admin/password123`)
- Session stays alive after logout or inactive.

**🔧 Tools:** Hoppscotch, Burp Suite (if installed)

**✅ Fix:** Enforce MFA, rate limit logins, use secure tokens.

---

### **8. Software and Data Integrity Failures**

**What It Means:** Code or data can be tampered with due to missing integrity checks.

**🔍 Example:**
- Application loads unsigned JavaScript from a CDN.
- No integrity checks (`Subresource Integrity` missing).

**✅ Fix:** Use signed packages, implement integrity verification, CI/CD trust validation.

---

### **9. Security Logging and Monitoring Failures**

**What It Means:** Attacks go unnoticed due to missing logs or no alerting.

**🔍 Example:**
- Failed login attempts are not logged.
- Suspicious activity isn't flagged or monitored.

**✅ Fix:** Log critical events, centralize monitoring, enable alerting (SIEM integration).

---

### **10. Server-Side Request Forgery (SSRF)**

**What It Means:** Attacker makes the server issue internal requests.

**🔍 Example:**
- Input: `http://127.0.0.1:8080/admin`
- API or image loader fetches internal URLs on behalf of attacker.

**🔧 Tools:** [Hoppscotch](https://hoppscotch.io), Local test payloads

**✅ Fix:** Whitelist domains, validate URLs, block localhost/private IP ranges.

---

## 📘 Bonus Tips

- Use **[Hoppscotch](https://hoppscotch.io)** to test APIs and HTTP headers.
- Use **[JWT.io](https://jwt.io)** to inspect and validate tokens.
- Use **[SecurityHeaders.com](https://securityheaders.com)** to check headers quickly.
- For subdomain enum, check **[crt.sh](https://crt.sh)** and **[Pentest-Tools](https://pentest-tools.com)**.

---

## 🌐 3. API Security Checklist

Use tools like [Hoppscotch.io](https://hoppscotch.io), [ReqBin](https://reqbin.com), and [JWT.io](https://jwt.io) for API testing.

### Key Areas to Test

- [ ] Broken Authentication
- [ ] Excessive Data Exposure
- [ ] Lack of Rate Limiting
- [ ] Mass Assignment
- [ ] Injection via JSON
- [ ] HTTP Method Abuse (GET, POST, PUT, DELETE)

---

## 🧰 4. Web-Based Tool Quick Reference

| Task              | Tool/Link                                                   | Web-Based |
|-------------------|-------------------------------------------------------------|-----------|
| Port Scan         | [HackerTarget Nmap](https://hackertarget.com/nmap-online-port-scanner/) | ✅        |
| Subdomain Enum    | [crt.sh](https://crt.sh), [Pentest-Tools](https://pentest-tools.com) | ✅        |
| Dir Discovery     | [SecurityTrails](https://securitytrails.com/tools/path-finder) | ✅        |
| Tech Detection    | [Wappalyzer](https://wappalyzer.com), [BuiltWith](https://builtwith.com) | ✅        |
| SSL Check         | [SSL Labs](https://www.ssllabs.com/ssltest/), [DigiCert](https://ssltools.digicert.com) | ✅ |
| Header Security   | [SecurityHeaders](https://securityheaders.com)             | ✅        |
| HTTP Requests     | [Hoppscotch.io](https://hoppscotch.io), [ReqBin](https://reqbin.com) | ✅        |
| JWT Decoder       | [JWT.io](https://jwt.io)                                   | ✅        |
| WAF Detection     | [Pentest-Tools](https://pentest-tools.com)                 | ✅        |
| **Burp Suite / ZAP / SQLMap / Hydra** | *Not available online (local only)*   | ❌        |

---

## ✅ 5. Challenge Strategy Example:  
**“List all information of `abc.domain.com`”**

### Checklist:
- [x] Subdomains → [crt.sh](https://crt.sh), [Pentest-Tools](https://pentest-tools.com)
- [x] Open Ports → [HackerTarget Nmap](https://hackertarget.com/nmap-online-port-scanner/)
- [x] Headers & TLS → [SecurityHeaders](https://securityheaders.com), [SSL Labs](https://www.ssllabs.com/ssltest/)
- [x] Tech Stack → [Wappalyzer](https://wappalyzer.com)
- [x] Directory Paths → [SecurityTrails](https://securitytrails.com)
- [x] API Behavior → [Hoppscotch](https://hoppscotch.io), [JWT.io](https://jwt.io)
- [x] Document Findings → Screenshots, text notes, summaries

---

**Tip:** Use screenshots, short notes, and tool outputs to document your findings effectively for submission.
