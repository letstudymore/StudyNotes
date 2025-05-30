
**Default Port:** 445

NMAP Scripts

smb-brute
smb-double-pulsar-backdoor
smb-enum-domains - nmap --script smb-enum-domains.nse -p445  **TARGET IP**
smb-enum-groups - nmap --script smb-enum-groups.nse -p445 **TARGET IP**
smb-enum-processes
smb-enum-services - nmap --script smb-enum-services.nse -p445  **TARGET IP**
smb-enum-sessions
smb-enum-shares - nmap --script smb-enum-shares.nse -p445 **TARGET IP**
smb-enum-users - nmap --script smb-enum-users.nse -p445 **TARGET IP**
smb-flood
smb-ls
smb-mbenum
smb-os-discovery
smb-print-text
smb-protocols
smb-psexec
smb-security-mode
smb-server-stats
smb-system-info
smb-vuln-conficker
smb-vuln-cve-2017-7494
smb-vuln-cve2009-3103
smb-vuln-ms06-025
smb-vuln-ms07-029
smb-vuln-ms08-067
smb-vuln-ms10-054
smb-vuln-ms10-061
smb-vuln-ms17-010
smb-vuln-regsvc-dos
smb-vuln-webexec
smb-webexec-exploit
smb2-capabilities
smb2-security-mode
smb2-time
smb2-vuln-uptime


ENUMERATE SHARES
nmap --script smb-enum-shares.nse -p 445 TARGET IP
Pay attention to the Current and Anonymous user access: READ, READ/WRITE

CONNECT TO SHARE USING GUI 
Network > Windows Network > smb://IP-ADDRESS and authentication credencials

ENUMERATE USERS
nmap --script smb-enum-users.nse -p445 TARGET IP
nmap --script smb-enum-users.nse --script-args smbusername=XXX,smbpassword=XXX -p445 TARGET IP**

ENUMERATE GROUPS
nmap --script smb-enum-groups.nse -p445 TARGET IP
nmap --script smb-enum-groups.nse -p445 --script-args smbusername=XXX,smbpassword=XXX -p445 TARGET IP

ENUMERATE DOMAINS
nmap --script smb-enum-domains.nse -p445 TARGET IP
nmap --script smb-enum-domains.nse -p445 --script-args smbusername=XXX,smbpassword=XXX -p445 TARGET IP

ENUMERATE SERVICES
nmap --script smb-enum-services.nse -p445  TARGET IP
nmap --script smb-enum-services.nse -p445 --script-args smbusername=XXX,smbpassword=XXX -p445 TARGET IP

ENUMERATE SECURITY LEVEL
nmap -sC -sV -A -T4 -p445 TARGET IP

#########################################################################

SMBCLIENT

smbclient //IP/share
smbclient -L IP
type password and ls
