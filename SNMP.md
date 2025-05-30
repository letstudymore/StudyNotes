
**Default Port:** 161

**Tools to use:**

Nmap
Snmp-check
metaspolit

Default UDP ports used by SNMP
Processes running on the target machine with nmap scripts
Community strings of the server using Nmap scripts
Community strings of the server using snmp_login Metasploit module
List all the interfaces of the machine using appropriate Nmap Scritps


**NMAP**

nmap -sP IP/CIDR
**Example:** nmap -sP 192.168.0/24

nmap -sU IP/CIDR
**Example:** nmap -sU 192.168.0.1

**nmap SNMP available scripts** - https://nmap.org/nsedoc/scripts/

snmp-brute
snmp-hh3c-logins
snmp-info
snmp-interfaces - nmap -sU -p 161 --script=snmp-interfaces IP TARGET
snmp-ios-config
snmp-netstat
snmp-processes - nmap -sU -p 161 --script=snmp-processes IP TARGET
snmp-sysdescr
snmp-win32-services
snmp-win32-shares
snmp-win32-software
snmp-win32-users

**SNMP CHECK**

**Example:** snmp-check 192.168.0.1


**VALID STRING WITH METASPLOIT (msfconsole)**

search snmp
use auxiliary/scanner/snmp/snmp_login
show options
ip a
set RHOSTS IP
show options
run or exploit

####################################################################

Community strings with NMAP
nmap -p 161 -sU --script snmp-brute --script-args snmp-brute.communitiesdb=./SecLists/Discovery/SNMP/common-snmp-community-strings.txt 192.168.6.2

Community string with Metasploit
msfconsole -q -x 'use auxiliary/scanner/snmp/snmp_login;set RHOSTS 192.168.9.20;set RPORT 161;exploit'
