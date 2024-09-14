# Fork
Please note that this was a very useful script on its own made by @wirzka. I am merely forking it because it included odat which does not run properly on ARM devices, and I've removed that. I'll update this README with any other important changes. 

# ARMincursore
```bash
    ___    ____  __  _______                                         
   /   |  / __ \/  |/  /  _/___  _______  ________________  ________ 
  / /| | / /_/ / /|_/ // // __ \/ ___/ / / / ___/ ___/ __ \/ ___/ _ \
 / ___ |/ _, _/ /  / // // / / / /__/ /_/ / /  (__  ) /_/ / /  /  __/
/_/  |_/_/ |_/_/  /_/___/_/ /_/\___/\__,_/_/  /____/\____/_/   \___/ 
                     @wirzka     (and pop lol)                        
```
*ARMincursore* will raid the target for you.

It came out from *nmapAutomator* to be more suited for the OSCP environment.

## TOC
- [Lazy here](#tldr)
- [Features and changes](#features-and-changes)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Future features](#future-features)
- [ARMincursore in the wild](#ARMincursore-in-the-wild)
- [Disclaimer](#disclaimer)

## TL;DR
While *ARMincursore* has born from *nmapAutomator*, it is **not** *nmapAutomator*. The script from @21y4d is great, but sometimes it's too slow (due to nikto). By removing it, the time needed to complete a scan has been drastically reduced.
So, from just removing nikto I found myself tweaking it a lot, that's why I decided to rename it to ARMincursore and to publish it under a new repo and name.
Hope you'll find it useful.

*Bear in mind that I'm still working on it.*

## Features and changes
*ARMincursore* has the following features and changes:
- It immmediately runs a full TCP port scans
- It asks to the user to run with sudo in order to run a SYN Scan instead of a Connect Scan
- It automatically tries to bruteforce FTP services
- It automatically takes screenshot of HTTP homepages using *cutycapt*
- It runs *ffuf* instead of *gobuster*
- It does not run *nikto*
- It has not the remote capabilities
#### Minor changes
- It highlights target IP
- It highlights target OS type
- It highlights nmap scan type
## Requirements
*ARMincursore*'s requirements are the following:
|      tool      |      scope      | official link |
|:--------------:|:---------------:|:-------------:|
|      nmap      |   recon/enum    | https://nmap.org/              |
|  nmap vulners  |      recon      |   https://github.com/vulnersCom/nmap-vulners            |
|      ffuf      |    web enum     |  https://github.com/ffuf/ffuf             |
|    sslscan     |    web enum     |  https://github.com/rbsec/sslscan             |
|    joomscan    |    web enum     | https://github.com/OWASP/joomscan              |
|     wpscan     |    web enum     |   https://github.com/wpscanteam/wpscan            |
|   droopescan   |    web enum     | https://github.com/droope/droopescan              |
|    cutycapt    |    web enum     |http://cutycapt.sourceforge.net/               |
|     smbmap     |    smb enum     | https://github.com/ShawnDEvans/smbmap              |
|   enum4linux   |    smb enum     |   https://github.com/CiscoCXSecurity/enum4linux            |
|   snmp-check   |    snmp enum    | https://www.nothink.org/codes/snmpcheck/index.php              |
|    snmpwalk    |    snmp enum    |https://linux.die.net/man/1/snmpwalk               |
|(removed for ARM64)     odat      | oracle db recon |   https://github.com/quentinhardy/odat            |
|   ldapsearch   |    ldap enum    |   https://linux.die.net/man/1/ldapsearch            |
|    dnsrecon    |    dns enum     | https://github.com/darkoperator/dnsrecon              |
| smtp-user-enum |    smtp enum    | https://github.com/pentestmonkey/smtp-user-enum              |
|     hydra      | ftp bruteforce  | https://github.com/vanhauser-thc/thc-hydra              |


The majority of them is already present in pentesting distro like Parrot OS and Kali Linux.
To find out how many of them are missing on your machine, just launch a which command like this:
```bash
$ which nmap ffuf sslscan joomscan wpscan droopescan cutycapt smbmap enum4linux snmp-check snmpwalk ldapsearch dnsrecon smtp-user-enum hydra
```

## Installation
```bash
git clone https://github.com/wirzka/ARMincursore.git
sudo ln -s $(pwd)/ARMincursore/ARMincursore.sh /usr/local/bin/
```
## Usage
```bash
$ ARMincursore.sh -h
     ____                                        
    /  _/___ _______  ________________  ________
   / // __ \/ ___/ / / / ___/ ___/ __ \/ ___/ _ \
 _/ // / / / /__/ /_/ / /  (__  ) /_/ / /  /  __/
/___/_/ /_/\___/\__,_/_/  /____/\____/_/   \___/
                     @wirzka                      

Usage: ARMincursore.sh -H/--host <TARGET-IP> -t/--type <TYPE>
Optional: [-d/--dns <DNS SERVER>] [-o/--output <OUTPUT DIRECTORY>]

Scan Types:
        Port    : Shows all open ports
        Script  : Runs a script scan on found ports
        UDP     : Runs a UDP scan "requires sudo"
        Vulns   : Runs CVE scan and nmap Vulns scan on all found ports
        Recon   : Suggests recon commands, then prompts to automatically run them
        All     : Runs all the scans

inspired by @21y4d gently modified by @wirzka
```
## Future Features
- Generally increasing auto reconnaissance based on discovered services.

## ARMincursore in the wild
Thanks to everyone for spending some times trying, using, and enhancing ARMincursore <3:
#### Xerosec on his YouTube video
[![xerosec on his YouTube video](https://img.youtube.com/vi/4CKey4l490c/0.jpg)](https://www.youtube.com/watch?v=4CKey4l490c)

## Disclaimer
I am not responsible for any damages (tangible or intangible) resulting from the use of *ARMincursore*.
You must have the permissions to use it.

Stay safe.
