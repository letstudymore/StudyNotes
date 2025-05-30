
Port scanning techniques are categorized according to the type of protocol used for communication within the network.

TCP Scanning
	Open TCP scanning methods (TCP connect/full open scan)
	Stealth TCP scanning methods (Half-open Scan, Inverse TCP Flag Scan, ACK flag probe scan, third party and spoofed TCP scanning methods)

UDP Scanning
SCTP Scanning
	SCTP INIT Scanning
	SCTP COOKIE/ECHO Scanning
SSDP and List Scanning
IPv6 Scanning

**nmap -sL -n [Target IP Address]**
he list scan is a degenerate form of host discovery that simply lists each host of the network(s) specified, without sending any packets to the target hosts.

**nmap -sT -v [Target IP Address]**
**-sT**: performs the TCP connect/full open scan and **-v**: enables the verbose output (include all hosts and ports in the output).

**nmap -sS -v [Target IP Address]**
**-sS**: performs the stealth scan/TCP half-open scan and **-v**: enables the verbose output (include all hosts and ports in the output).

**nmap -sX -v [Target IP Address]**
**-sX**: performs the Xmas scan and **-v**: enables the verbose output (include all hosts and ports in the output)

**nmap -sM -v [Target IP Address]**
**-sM**: performs the TCP Maimon scan and **-v**: enables the verbose output (include all hosts and ports in the output).

**nmap -sA -v [Target IP Address]**
**-sA**: performs the ACK flag probe scan and **-v**: enables the verbose output (include all hosts and ports in the output).

**nmap -sU -v [Target IP Address]**
**-sU**: performs the UDP scan and **-v**: enables the verbose output (include all hosts and ports in the output). This scan could take approximately 15-20 minutes.

Apart from the aforementioned port scanning and service discovery techniques, you can also use the following scanning techniques to perform a port and service discovery on a target network using Nmap.

IDLE/IPID Header Scan: A TCP port scan method that can be used to send a spoofed source address to a computer to discover what services are available.

**nmap -sI -v [target IP address]**
**IDLE/IPID Header Scan**: A TCP port scan method that can be used to send a spoofed source address to a computer to discover what services are available.

**nmap -sY -v [target IP address]**
**SCTP INIT Scan**: An INIT chunk is sent to the target host; an INIT+ACK chunk response implies that the port is open, and an ABORT Chunk response means that the port is closed.

**nmap -sZ -v [target IP address]**
**SCTP COOKIE ECHO Scan**: A COOKIE ECHO chunk is sent to the target host; no response implies that the port is open and ABORT Chunk response means that the port is closed.

**nmap -sV [Target IP Address]**
**-sV**: detects service versions.
Service version detection helps you to obtain information about the running services and their versions on a target system. Obtaining an accurate service version number allows you to determine which exploits the target system is vulnerable to.

**nmap -A [Target Subnet]**
**-A**: enables aggressive scan. The aggressive scan option supports OS detection (-O), version scanning (-sV), script scanning (-sC), and traceroute (--traceroute). You should not use -A against target networks without permission.

**nmap -f [Target Subnet]**
-f: Used to scan tiny fragment packets.

