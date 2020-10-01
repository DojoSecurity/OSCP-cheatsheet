# OSCP-cheatsheet

### Port Scanning
```
masscan -p1-65535,U:1-65535 10.10.10.x --rate=1000 -e tun0
nmap -sV -A -p- -o nmap.txt 10.10.10.x
nikto -u http://10.10.10.x/
```

### Content Discovery
```
dirbuster
gobuster vhost -u http://10.11.1.8/ -w /usr/share/wordlists/dirb/common.txt
```

### Wordlists: 
```
https://github.com/danielmiessler/SecLists
cewl -w wordlists.txt -d 10 -m 1 http://10.10.10.x/
```
### SMB
```
Anonymous login:
smbclient -N -L \\\\10.11.1.5\\

smbmap
smbmap -H 10.11.1.5 -p anonymous -u anonymous

nmap smb vuln script
nmap --script smb-vuln* -p 137,139,445 10.11.1.5
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
