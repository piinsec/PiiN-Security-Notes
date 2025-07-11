# 🎯 Red Team Guide (2025 Edition)

Red Teaming involves simulating real-world adversaries to test the effectiveness of security defenses. Unlike traditional pentesting, red teaming emphasizes stealth, persistence, and real-world tactics, techniques, and procedures (TTPs).

---

## 🔰 What Is Red Teaming?

- Realistic, full-scope offensive operations against an organization
- Focused on **emulating advanced threat actors (APT)**
- Tests not just technology, but also people and processes (e.g., social engineering)
- Often used to improve **Blue Team (defensive)** capabilities

---

## 🧱 Skills You Need

### 1. Networking & Systems
- Deep knowledge of **TCP/IP**, DNS, HTTP, VPNs
- Understand **firewalls**, **IDS/IPS**, and endpoint defenses
- Familiarity with **Active Directory** architecture

### 2. Operating Systems
- Proficient with **Linux CLI**
- Deep understanding of **Windows internals**

### 3. Programming/Scripting
- **PowerShell** (for Windows post-exploitation)
- **Python**, **Bash**, and optionally C/C++

### 4. Security Concepts
- MITRE ATT&CK framework
- TTPs (Tactics, Techniques, Procedures) used by real threat actors

---

## 🛠️ Essential Tools for Red Teaming

| Category              | Tools                                      |
|-----------------------|---------------------------------------------|
| Reconnaissance        | Nmap, Amass, subfinder, FOCA                |
| Enumeration           | enum4linux, CrackMapExec, ldapdomaindump    |
| Exploitation          | Metasploit, custom scripts, Cobalt Strike   |
| Credential Access     | Mimikatz, LaZagne, Rubeus                   |
| Lateral Movement      | PsExec, WMIexec, SMBexec                    |
| Post-Exploitation     | PowerView, PowerUp, BloodHound, SharpHound |
| C2 Frameworks         | Covenant, Sliver, Mythic, Havoc             |

---

## 🧪 Practice Labs

- Create a local AD lab using:
  - **Kali Linux**, **Windows 10**, **Windows Server 2019**
- Use platforms like:
  - [Hack The Box - Pro Labs](https://www.hackthebox.com)
  - [TryHackMe - Red Team Paths](https://tryhackme.com)
  - [RangeForce, CyberDefenders, VulnHub]

---

## 📚 Recommended Learning Resources

- 🎥 YouTube: The Cyber Mentor, Hackersploit, John Hammond
- 📘 Books:
  - *Red Team Field Manual*
  - *Advanced Penetration Testing* by Wil Allsopp
  - *The Hacker Playbook 2/3*
- 🎓 Certifications:
  - eCPPT, CRTP, CRTO, OSCP (Offensive Security), Red Team Ops II

---

## 🧠 Bonus Tips

- Stay stealthy — learn **OPSEC**, **AV/EDR evasion**, **living off the land**
- Document everything like a professional report
- Emulate real-world APTs using MITRE ATT&CK mapping
- Use GitHub to track toolsets and custom scripts

---

📌 *“Red Teaming is not just about breaking things — it’s about showing how things break, why they break, and how to fix them better.”*
