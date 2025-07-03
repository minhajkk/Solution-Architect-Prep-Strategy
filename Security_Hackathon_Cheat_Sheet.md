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
