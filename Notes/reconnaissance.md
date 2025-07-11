# Reconnaissance

This document provides a comprehensive guide to recon techniques and tools used in bug bounty hunting and penetration testing.

---

## 🌐 Search Engines for Bug Bounty Hunters

- [Bug Bounty Search Engine](https://nitinyadav00.github.io/Bug-Bounty-Search-Engine/)
- [httpstatus.io](https://httpstatus.io) — Check HTTP status codes of URLs

---

## 🕵️‍♂️ Subdomain Enumeration

### Online Tools

- [subdomainfinder.c99.nl](https://subdomainfinder.c99.nl)

### CLI Tools

#### 🔹 Amass (Passive)
```bash
amass enum -passive -d target.com -o subdomain.txt
```

#### 🔹 Subfinder
```bash
subfinder -d target.com -all > domain.txt
```

#### 🔹 Assetfinder
```bash
assetfinder --sub-only target.com > domain1.txt
```

#### 🔹 FFUF (Bruteforce)
```bash
ffuf -u https://FUZZ.target.com -w /usr/share/wordlists/Subdomain.txt -o domain2.txt
```

### 🧹 Combine and Clean Subdomains
```bash
sort -u domain.txt domain1.txt > sdomain.txt
```

---

## 🌍 Live Domain Testing

### httpx
```bash
cat sdomain.txt | httpx > alive.txt
```

---

## 🧨 Subdomain Takeover Detection

### Subzy
```bash
subzy run --targets sdomain.txt
```

### Nuclei (Takeover template)
```bash
cat alive.txt | nuclei -t ~/.local/nuclei-templates/http/takeovers/
```

### Nuclei (Critical Vulns Only)
```bash
cat alive.txt | nuclei -severity critical,high -o nuclei_results.txt
```

---

## 🔎 URL Discovery

### Katana
```bash
katana -u http://target.com -o urls.txt
```

---

## 🔌 Port Scanning

### Nmap
```bash
nmap -p- --open -sV -sC -T4 -oN nmap_result.txt target.com
```

---

## 📂 Directory and File Bruteforce

### FFUF
```bash
ffuf -u https://target.com/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o dir.txt
```

### Gobuster
```bash
gobuster dir -u https://target.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o dir.txt
```

---

## 🔗 JS and Secret Discovery

### LinkFinder
```bash
python3 linkfinder.py -i https://target.com/script.js -o result.txt
```

### GF + Regex Patterns
```bash
cat js_file.txt | gf apikeys > secrets.txt
```

---

## 🧵 Parameter Discovery

### ParamSpider
```bash
python3 paramspider.py -d target.com --level high -o params.txt
```

### Arjun
```bash
arjun -u https://target.com/api -m GET -o params.json
```

---

## ⚔️ XSS Detection

### Dalfox
```bash
cat params.txt | dalfox pipe -o xss_result.txt
```

### XSStrike
```bash
python3 xssstrike.py -u "https://target.com/index.php?search=query"
```

---

## 🐞 SQL Injection

### SQLMap
```bash
sqlmap -u "https://target.com/i.php?id=1" --dbs --batch --random-agent
```

---

## 🌐 SSRF Testing

### Gopherus
```bash
python3 gopherus.py interactsh-client -v
```

---

## 📁 LFI/RFI Testing

### LFISuite
```bash
python3 lfisuite.py -u "https://target.com/i.php?file=../../../etc/passwd"
```

### fimap
```bash
fimap -u "https://target.com/i.php?file=test"
```

---

## 🔁 Open Redirect

### Oralyzer
```bash
python3 oralyzer.py -l url.txt -p payload.txt
```

### FFUF Method
```bash
ffuf -w redirect_params.txt:PARAM -w payload.txt:PAYLOAD -u "https://site.com/re.php?PARAM=PAYLOAD" -mc 301,302,303,307,308 -H "User-agent: Mozilla/5.0" -x http://127.0.0.1:8080 -t 10 -mr "Location: http://google.com"
```

---

## 🔌 API Recon

### Kiterunner
```bash
kiterunner -u https://target.com -w wordlist/apis.txt
```

---

## 🧪 Content Discovery

```bash
gau target.com | tee url.txt
waybackurls target.com > wayback.txt
```

---

## 🛠️ CMS Enumeration

```bash
python3 cmseed.py -u target.com
```

---

## 🕸️ Advanced Katana Usage

```bash
# Discover JS files
katana -u example.com -jc | grep ".js$"

# Multiple subdomains
katana -list subfinal.txt -jc | grep ".js$" | uniq | sort

# Deep discovery with filters
katana -list subfinal.txt -jc -d 5 -ps -pss waybackarchive,commoncrawl,alienvault -hf -fx -ef woof,css,png,svg,jpg,woff2,jpeg,gif -o allurls.txt

# Sensitive files
cat allurls.txt | grep -E "\.txt|\.log|\.cache|\.secret|\.db|\.backup|\.yml|\.json|\.gz|\.rar|\.zip|\.config"

# JavaScript analysis
cat allurls.txt | grep -E "\.js$" >> js.txt
cat js.txt | nuclei -t ~/nuclei-templates/ -severity critical,high,medium

# LFI scan
cat allurls.txt | gf lfi | nuclei -tags lfi
```

---

## 🧠 Extra: Dorking with go-dork
```bash
go-dork -e google -q "Powered by Real Easy Store ( joudiSoft ltd. )" -p 50
site:.mm (inurl:url= | inurl:return= | inurl:next= | inurl:redirect= | inurl:redir= | inurl:ret=)
```

---

## 🪄 MagicRecon (Automated Recon Tool)
[Magicrecon](https://github.com/robotshell/magicRecon)
```bash
./magicrecon.sh -l domainlist.txt -p
```

---

> 🛡️ This guide is part of the [PiiN Security Notes](https://github.com/piinsec/PiiN-Security-Notes) collection.