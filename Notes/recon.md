# Recon 

## Search Engine for bug Bounty Hunters
[Site](https://nitinyadav00.github.io/Bug-Bounty-Search-Engine/)

## Status code check
[httpstatus.io](https://httpstatus.io)

## Subdomain finder online
[subdomainfinder.c99.nl](https://subdomainfinder.c99.nl)



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

