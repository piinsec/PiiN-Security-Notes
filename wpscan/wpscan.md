# WPSCAN
## Table of Content
- [Install WPScan](#install-wpscan)
- [WPScan options](#wpscan-options)
- [Run a basic scan](#run-a-basic-scan)

## Install WPScan

WPScan can be installed on Linux and macOS systems using the command line. You can download the latest version of WPScan from the official GitHub repository:

```shell
git clone https://github.com/wpscanteam/wpscan.git
```

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
- Save the result : \> wpscan.txt

### Run a basic scan
Scanning the target DVWP on http://localhost:8080
To run a basic scan with WPScan, use the following command:

```shell
wpscan --url http://example.com
```

```shell

wpscan --url http://example.com --enumerate vp --plugins-detection mixed --plugins-version-detection mixed
```
This will perform a more detailed scan of the target WordPress site, including enumerating the installed plugins (--enumerate vp), using mixed detection modes for plugin detection and version detection (--plugins-detection mixed --plugins-version-detection mixed), and display a summary of the scan results.








