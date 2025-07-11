# 🐞 Bug Bounty Hunting Guide (2025 Edition)

Bug bounty hunting is a legal and ethical way to find vulnerabilities in web, mobile, and cloud applications — and get rewarded for it. This guide will help you get started and go pro.

---

## 🔰 What Is Bug Bounty Hunting?

- You find and report vulnerabilities on websites/platforms
- Companies reward you with **money**, **swag**, or **recognition**
- You work with public programs (HackerOne, Bugcrowd, etc.)

---

## 🧱 Skills You Need

### 1. Web Fundamentals
- HTTP/S, cookies, sessions
- DNS, CDN, headers, status codes

### 2. Web Application Security
- OWASP Top 10 (XSS, SQLi, SSRF, RCE, IDOR, etc.)
- Authentication bypasses, rate-limiting bypass

### 3. Recon & Automation
- Subdomain enumeration (subfinder, assetfinder)
- Wayback + param discovery (gau, waybackurls, ParamSpider)

### 4. Scripting Skills
- Bash, Python, JS for automation
- Custom payload crafting (XSS, SSRF, etc.)

---

## 🧰 Tools of the Trade

| Category              | Tools                                 |
|-----------------------|----------------------------------------|
| Recon                 | subfinder, amass, assetfinder, chaos  |
| Fuzzing               | ffuf, dirsearch, feroxbuster           |
| Vulnerability Scanning| Nuclei, Burp Suite Pro, dalfox         |
| Parameter Discovery   | ParamSpider, Arjun, gau                |
| Exploitation          | curl, httpx, sqlmap, XSStrike          |
| Reporting             | Markdown, Burp Export, Hacktivity      |

---

## 🌍 Platforms to Hunt On

- [HackerOne](https://hackerone.com)
- [Bugcrowd](https://bugcrowd.com)
- [YesWeHack](https://yeswehack.com)
- [Intigriti](https://intigriti.com)
- [Open Bug Bounty](https://www.openbugbounty.org)

---

## 🎯 Methodology (Simplified Flow)

1. **Reconnaissance**
   - Find subdomains, endpoints, parameters
2. **Vulnerability Discovery**
   - Fuzz, test, enumerate features
3. **Exploitation**
   - Proof-of-concept (POC), verify impact
4. **Reporting**
   - Provide clear, concise, reproducible report with POC

---

## 📚 Recommended Resources

- **Books**:
  - *Web Hacking 101*
  - *The Web Application Hacker's Handbook*
  - *Bug Bounty Bootcamp* by Vickie Li
- **YouTube**:
  - InsiderPhD, Stök, NahamSec, Bugcrowd University
- **Practice Platforms**:
  - [PortSwigger Labs](https://portswigger.net)
  - [HackTheBox - Web Challenges](https://hackthebox.com)
  - [TryHackMe - Web Hacking Path](https://tryhackme.com)

---

## 💰 Earning Tips

- Focus on **low-hanging fruit** (e.g., IDOR, subdomain takeovers)
- Hunt **new features** or **hidden APIs**
- Be fast when programs are newly launched
- Build your own **automation toolkit**

---

## ✅ Final Advice

- Keep practicing. Start with labs before going live.
- Always stay ethical and read the **program rules**.
- Join bug bounty communities on Discord, Twitter, Reddit.
- Use GitHub to track your tools, templates, and notes.

---

📌 *“You don’t need to hack everything — you just need to find one thing others missed.”*
