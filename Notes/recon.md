# Reconnaissance 

## Search Engine for bug Bounty Hunters
[Search Engine](https://nitinyadav00.github.io/Bug-Bounty-Search-Engine/)

## Status code check
[httpstatus.io](https://httpstatus.io)

## Subdomain finder online
[subdomainfinder.c99.nl](https://subdomainfinder.c99.nl)

## Magicrecon
[Magicrecon](https://github.com/robotshell/magicRecon)
```shell
./magicrecon.sh -l domainlist.txt -p
```
## DORKing
```shell
go-dork -e google -q “Powered by Real Easy Store ( joudiSoft ltd. )” -p 50
site:.mm(inurl:url= | inrul:return= | inurl:next= | inurl:redirect= | inurl:redir= | inrul:ret=) 
```
## Subdomain Find
### Amass
```shell
amass enum -passive -d target.com -o subdomain.txt
```
## Assetfinder
```shell
assetfinder --sub-only target.com >> subdomain.txt
```
## Subfinder
- ရှိသမျှ domain တွေကို စစ်ပြီး domain.txt file မှာ သိမ်းသည်။
```shell
sudo subfinder -d target.com -all > domain.txt
```
## Assetfinder
- subdomain အားလုံးကို ရှာပြီး domain1.txt မှာ သိမ်းသည်။
```shell
sudo assetfinder -subs-only target.com > domain1.txt
```
## Bruteforce subdomain
- ffuf ဖြင့် subdomain များကို bruteforce လုပ်ခြင်းဖြစ်သည်။
```shell
ffuf -u https://FUZZ.target.com -w /usr/share/wordlist/Subdomain.txt -o domain2.txt
```
## Modify the result
```shell
└─$ wc -l domain.txt                                                                                                                         
123 domain.txt
└─$ wc -l domain1.txt 
195 domain1.txt
└─$ sort -u domain.txt domain1.txt > sdomain.txt
└─$ wc -l sdomain.txt 
128 sdomain.txt
```
## Live domain tessting
  - httpx
```shell
cat sdomain.txt | sudo httpx > alive.txt
```
## Tahkeover testing
  - subzy
```shell
subzy run --targets sdomain.txt
```
  - nuclei
```shell
cat alive.txt | nuclei -t ~/.local/nuclei-templates/http/takeovers.yml
```
  - For critical vulns only
```shell
cat alive.txt | nuclei -severity critical,high -o nuclei_results.txt
```
## Finding URLs
```shell
katana -u http://target.com -o urls.txt
```
## Port Scanning
### Nmap 
```shell
nmap -p --open -sV -sC -T4 -oN nmap_result.txt target.com
```
## Directoroy Brute Forcing
### FFUF
```shell
ffuf -u https://target.com/FUZZ -w /usr/share/wordlist/dirbuster/directory-list-2.3-medium.txt -o dir.txt
```
### Gobuster
```shell
gobuster dir -u https://target.com -w /usr/share/wordlist/dirbuster/directory-list-2.3-medium.txt -o dir.txt
```
## Link Finder
[linkfinder.py](https://github.com/GerbenJavado/LinkFinder)
```shell
python3 linkfinder.py -i https://target.com/script.js -o result.txt
```
### GF
```shell
cat js_file.txt | gf apikeys > secrets.txt
```
## Parameter Discovery
[paramspider.py](https://github.com/devanshbatham/ParamSpider)
```shell
python3 paramspider.py -d target.com --level high -o params.txt
```
### Arjun
[Arjun](https://github.com/s0md3v/Arjun)
```shell
arjun -u https://target.com/api -m GET -o params.json
```
## XSS Detection
[Dalfox](https://github.com/hahwul/dalfox)
```shell
cat params.txt | dalfox pipe -o xss_result.txt
```
### XSS Strike
[xss strike](https://github.com/s0md3v/XSStrike)
```shell
python3 xssstrike.py -u “https://target.com/index.php?search=query”
```
## SQLi
```shell
sqlmap -u “https://target.com/i.php?id=1” —dbs —batch —random-agent
```
## SSRF Discovery
### Gopherus
[Gopherus](https://github.com/tarunkant/Gopherus )
```shell
python3 gopherus.py interactsh-client -v
```
## LFI/RFI
### lfisute
```shell
python3 lfisuite.py -u “https://target.com/i.php?file=../../../etc/passwd”
```
### fimap
```shell
fimap -u “https://t.com/i.php?file=test”
```
## OPEN REDIRECT
### oralyzer
```shell
python3 oralyzer.py -l url.txt -p payload.txt
```
```shell
ffuf -w redirect_params.txt:PARAM -w payload.txt:PAYLOAD -u “https://site.com/re.php?PARAM=PAYLOAD” -mc 301,302,303,307,308 -H “User-agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0: -x http://localip:8080 -t 10 -mr “Location: http://google.com” 
```
## API RECON
```shell
kiterunner -u https://target.com -w wordlist/apis.txt
```
## Content discovery
```shell
gau [target.com](http://target.com) | tee url.txt
waybackurls [target.com](http://target.com) > wayback.txt
```
## CMS ENUM
```shell
python3 cmseed.py -u target.com
```
## Katana
```shell
katana -u example.com  -jc | grep “.js$”
katana -list subfinal.txt -jc | grep “.js$”
katana -list subfinal.txt -jc | grep “.js$” | uniq | sort
katana -u subalive.txt -d 5 -ps -pss waybackarchive, commoncrawl, alienvault -hf -jc -fx -ef woof, css, png, svg, jpg, woff2, jpeg, gif, svg -o allurls.txt
cat allurls.txt | grep -E “\.txt|\.log|\.cache|\.secret|\.db|\.backup|\.yml|\.json|\.gz|\.rar|\.zip|\.config”
cat allurls.txt | grep -E “\.js$” >> js.txt
cat js.txt | nuclei -t /home/kali/.local/nuclei-templates/Nuclei-template/ -serverity ‘critical,high,medium’
cat allurls.txt | gf lfi | nuclei -tags lfi
```
