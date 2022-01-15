# OSCP-cheatsheet

### Valuable links and sources
```
Great tool to automate the scans:
https://github.com/Tib3rius/AutoRecon

Lists of Directories, Passwords and more:
https://github.com/danielmiessler/SecLists 
https://github.com/swisskyrepo/PayloadsAllTheThings

A lot of hacking techniques stored in one place:
https://book.hacktricks.xyz/

Find Ippsec Video related to your searchterm:
https://ippsec.rocks/?#

```
### Port Scanning
```
Find open ports quickly:
masscan -p1-65535,U:1-65535 10.10.10.x --rate=1000 -e tun0

Scan Ports found with masscan with nmap:
nmap -sV -A -o nmap.txt 10.10.10.x -p XX,XX,XX
```

### Basic Website Recon
```
nikto -u http://10.10.10.10/
```

### Content Discovery
```
ffuf -c -w ./directory-list-2.3-big.txt -u https://10.10.10.10/FUZZ -e txt,php,jsp,old,bak
gobuster vhost -u http://10.10.10.10/ -w /usr/share/wordlists/dirb/common.txt
```

### Wordlists: 
```
https://github.com/danielmiessler/SecLists
cewl -w wordlists.txt -d 10 -m 1 http://10.10.10.x/
```
### SMB
```
Anonymous login:
smbclient -N -L \\\\10.10.10.10\\

smbmap
smbmap -H 10.10.10.10 -p anonymous -u anonymous

nmap smb vuln script
nmap --script smb-vuln* -p 137,139,445 10.10.10.10

Metasploit scanner for SMB Version:
use auxiliary/scanner/smb/smb_version

```
### LDAP
```
ldapsearch -x -h 10.10.10.x -p 389 -s base namingcontexts
ldapsearch -x -h 10.10.10.x -p 389 -b "DC=svcorp-BANK,DC=com"
nmap -p 389 --script ldap-search 10.10.10.x
```

### Shell upgrade to terminal
```
python -c 'import pty;pty.spawn("/bin/bash")'
Ctrl+Z  
stty raw -echo
fg 
export TERM=xterm-256color
```
   
### Compiling exploits for Windows
```
i686-w64-mingw32-gcc exploit.c -o exploit
gcc exploit.c -o exploit 

For 32bit
i686-w64-mingw32-gcc 40564.c -o 40564 -lws2_32
gcc 9542.c -m32  -Wl,--hash-style=both -o exploit (static exploit)
```
