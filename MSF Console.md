
Check User
getuid

Check OS
sysinfo


Checking IP
ipconfig /ifconfig

Check for Privileges (whoami /all)
getprivs

Search files
search -f pagefile.sys

LIST FILES
dir
dir /a:h

Users
net user
net user /domain

NETWORK
netstat -anto

LIST SERVICES
sc queryex type=service state=all
net start/stop servicename

FIREWALLS
netsh firewall show state
netsh firewall show config
netsh advfirewall set allprofiles state off

VERSION RUNNING 
wmic /node:"" product get name,version,vendor
wmic cpu get
wmic useraccount get name,sid

FILES SEARCH
findstr /E ".txt" > txt.txt
findstr /E ".log" > log.txt
findstr /E ".doc" > doc.txt

