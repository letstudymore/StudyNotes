

**Live Host on network (ping sweep):** nmap -sP IP/CIDR
**Examples:** 
	- nmap -sP -v 192.168.1.0/24
	- nmap -sP -v 192.168.1.*
	- nmap -sP -v 192.168.1.0-255

**Live Host on network without port scan (ARP scan):** nmap -PR -sn IP/CIDR
**Examples:** 
	- nmap -PR -sn 192.168.1.1/24
	- nmap -PR -sn 192.168.1.*
	- nmap -PR -sn 192.168.1.0-255

**Reduces TCP Wrapped Results**
nmap -sS "IP Address"
nmap -sS 192.168.10.X

**Scan ALL ports:** nmap -p- IP/CIDR
**Examples:** 
	- nmap -p- 192.168.1.1/24
	- nmap -p- 192.168.1.*
	- nmap -p- 192.168.1.0-255

**Scan specific port:** nmap -p "PORT" IP/CIDR
**Examples:** 
	- nmap -p- 192.168.1.1/24
	- nmap -p- 192.168.1.*
	- nmap -p- 192.168.1.0-255

**Agressive Scan:** nmap -A  IP/CIDR
**Examples:** 
	- nmap -A 192.168.1.1/24
	- nmap -A 192.168.1.*
	- nmap -A 192.168.1.0-255

**Power Scan Scrips + Services + Versions + OS:** nmap -sC -sV -p- -A -v -T4 IP/CIDR -oN "output_file.txt"
**Examples:** 
	- nmap -sC -sV -p- -A -v -T4 192.168.1.1/24
	- nmap -sC -sV -p- -A -v -T4 192.168.1.*
	- nmap -sC -sV -p- -A -v -T4 192.168.1.0-255

**Get OS Information**
nmap --script smb-os-discovery.nse "IP Address"
nmap --script smb-os-discovery.nse 192.168.10.X