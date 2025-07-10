# WPSCAN
- Wordpress website များ ကို security စစ်ဆေးရာမှာ အသုံးတည့်တဲ့ tool တစ်ခုဖြစ်ပါတယ်။ WPScan ကို windows မှာ သုံးခြင်ရင်တော့ အောက်မှာဖော်ပြထားတဲ့ website မှာ ကြည့်ပြီး အဆင့်ဆင့် လုပ်ဆောင်နိုင်ပါတယ်။ Kali linux မှာတော့ defult ပါပါတယ်။

## Install in Windows
ဒီ [website](https://www.seoeditors.com/expert-seo/how-to-install-wpscan-on-windows-10) မှာ wpscan သွင်းနည်း အဆင့်ဆင့် ကို ပြသထားပါတယ်။

## WPScan options

```shell

Usage: wpscan [options]
        --url URL                          The WordPress URL/domain to scan.
        --disable-accept-header           Disable the Accept HTTP header.
        --disable-referer                 Disable the Referer HTTP header.
        --wp-content-dir DIR               WPScan can detect the content directory (ie wp-content) from the homepage but if the website has a custom directory, use this option.
        --wp-plugins-dir DIR               The plugins directory (default: wp-content/plugins).
        --wp-themes-dir DIR                The themes directory (default: wp-content/themes).
        --random-user-agent               Use a random user-agent.
    -v, --verbose                          Verbose output.
        --version                          Display the WPScan version.
    -h, --help                             Display this help message.

Plugin Detection:
        --enumerate[=OPTS]                 List plugins.
                                           Options :
                                             vp  |  Only vulnerable plugins.
                                             ap  |  Only active plugins.
                                             i   |  Only an information about the plugins.
                                             vt  |  Only vulnerable plugins and their version.
                                             at  |  Only active plugins and their version.
        --exclude-content-based REGEXP     Used with the enumeration option (plugins, themes, usernames). Will exclude all entries based on the regexp.
        --detection-mode MODE              Default, Aggressive and Passive modes. Default = mixed.

Theme Detection:
        --enumerate[=OPTS]                 List themes.
                                           Options :
                                             vt  |  Only vulnerable themes.
                                             at  |  Only active themes.

User Enumeration:
        --enumerate[=OPTS]                 List users.
                                           Options :
                                             u   |  Identify the usernames of the authors (and uids) of posts and list them.
                                             m   |  Identify the username of the user connected (if any).
        --exclude-content-based REGEXP     Used with the enumeration option (plugins, themes, usernames). Will exclude all entries based on the regexp.

Password Brute Forcing:
        --wordlist WORDLIST                Path to the wordlist.
        --username USERNAME                Only brute force the supplied username.
        --usernames USERNAMES              A list of usernames to enumerate and brute force.
        --threads THREADS                  The number of threads to use when multi-threading requests.
        --throttle DELAY                    Milliseconds to wait before sending each request. This option is only available in conjunction with the --threads option.

Performance:
        --request-timeout SECONDS          Maximum time in seconds to wait for a response from the web server. The default is 30 seconds.
        --connect-timeout SECONDS          Maximum time in seconds to wait while trying to connect to the web server. The default is 30 seconds.
        --max-threads THREADS              The maximum number of threads to use when multi-threading requests. The default is 50.

Output:
        --output FILE                      Output results to a file.
        --format FORMAT                    Output results in the format specified.
                                           Available formats: cli-no-color, cli, json, xml, yml.

Miscellaneous:
        --update                           Update WPScan.
        --follow-redirection               Follow redirections.
        --batch                            Never ask for user input, use the default behaviour.
        --proxy PROXY                      Supply a proxy in the format host:port.
        --tor                              Use TOR anonymity network.
        --cache-ttl TIME                    Time to keep cached data in seconds. Default is 1800 (30 minutes).
```

### Run a basic scan
```shell
wpscan --url http://target.com
```
- Save the result
```shell
wpscan --url http://target.com > wpscan.txt
```

## Tips & Tricks
- Wpscan API key ရဖို့အတွက် [wpscan website](https://wpscan.com) မှာ account အရင်ဖွင့်ပါ။

- My Fav wpscan command
  ```shell
    wpscan --url https://target.com --random-user-agent -disable-tls-checks --api-token [your API key] --enumerate vp,vt,u
  ```
  
- User များကို manual ရှာခြင်း
        - Target Url ရဲ့ နောက်မှာ /wp-json/wp/v2/users ထည့်လိုက်တာနဲ့ user id, name, url ... စသည်ဖြင့် JSON format နဲ့ user ရှိသလောက်ပေါ်လာပါလိမ့်မယ်။
        - User name list ကို -U "user1,user2,user3" ဆိုပြီး wpscan option မှာ ထည့်လို့ရသလို username.txt ဆိုပြီးလဲ file မှာ သိမ်းပြီး scan လို့ ရပါတယ်။

- Login Bruteforce လုပ်ခြင်း
  ```shell
  wpscan --url http://target.com/ --passwrod /usr/share/wordlists/rockyou.txt --username username.txt
  ```

## Result ကို ကြည့်ပြီး ဘာတွေလုပ်မလဲ
- Vulnerable plugin ခေါင်းစဉ်တွေအလိုက် exploit တွေရှာကြည့်ပါ။ မတွေ့ဘူးဆိုရင်တော့ cve တွေဘယ်လိုရခဲ့လဲ POC တွေ လိုက်ကြည့်ပြီး manual လုပ်ကြည့်မှရမှာပါ။
- Username တွေ တွေ့ရင် Brute Force တိုက်ရမှာပဲ။ ဒါပေမဲ့ wordlist ကို guess လုပ်ပြီး ကိုယ်တိုင်ဖန်တီးတာက ပိုအဆင်ပြေနိုင်ပါတယ်။
