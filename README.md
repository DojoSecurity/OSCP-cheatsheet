# OSCP-cheatsheet

PORT SCANNING

Initial open ports check
'''masscan -p1-65535,U:1-65535 10.10.10.x --rate=1000 -e tun0'''
Nmap port scan
'''nmap -sV -A -p- -o nmap.txt 10.10.10.x'''
'''nikto -u http://10.10.10.x/''' 


Content Discovery

'''dirbuster'''
'''gobuster -e -u http://10.10.10.x/ -w /usr/share/wordlists/dirb/common.txt'''

Wordlists: 
https://github.com/danielmiessler/SecLists
cewl -w wordlists.txt -d 10 -m 1 http://10.10.10.x/  







Shell upgrade to terminal
'''python -c 'import pty;pty.spawn("/bin/bash")'
   Ctrl+Z
   
   stty raw -echo
   fg
   export TERM=xterm-256color'''
   
