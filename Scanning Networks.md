
The following are examples of host discovery techniques:

- ARP ping scan
- UDP ping scan
- ICMP ping scan (ICMP ECHO ping, ICMP timestamp, ping ICMP, and address mask ping)
- TCP ping scan (TCP SYN ping and TCP ACK ping)
- IP protocol ping scan

**Host Discovery using Nmap**

Here, we will use Nmap to discover a list of live hosts in the target network. We can use Nmap to scan the active hosts in the target network using various host discovery techniques such as ARP ping scan, UDP ping scan, ICMP ECHO ping scan, ICMP ECHO ping sweep, etc.

nmap -sn -PR [Target IP Address]
-sn: disables port scan and -PR: performs ARP ping scan.

nmap -sn -PU [Target IP Address]
-PU: performs the UDP ping scan.

The UDP ping scan sends UDP packets to the target host; a UDP response means that the host is active. If the target host is offline or unreachable, various error messages such as “host/network unreachable” or “TTL exceeded” could be returned.

nmap -sn -PE [Target IP Address]
-PE: performs the ICMP ECHO ping scan.

nmap -sn -PE [Target Range of IP Addresses]
The ICMP ECHO ping sweep is used to determine the live hosts from a range of IP addresses by sending ICMP ECHO requests to multiple hosts. If a host is alive, it will return an ICMP ECHO reply.

nmap -sn -PP [Target IP Address]
-PP: performs the ICMP timestamp ping scan.

Apart from the aforementioned network scanning techniques, you can also use the following scanning techniques to perform a host discovery on a target network.

- **ICMP Address Mask Ping Scan**: This technique is an alternative for the traditional ICMP ECHO ping scan, which are used to determine whether the target host is live specifically when administrators block the ICMP ECHO pings.

    **# nmap -sn -PM [target IP address]**
    TCP SYN Ping Scan**: This technique sends empty TCP SYN packets to the target host, ACK response means that the host is active.

    **# nmap -sn -PS [target IP address]**
    **TCP ACK Ping Scan**: This technique sends empty TCP ACK packets to the target host; an RST response means that the host is active.

    **# nmap -sn -PA [target IP address]**
    **IP Protocol Ping Scan**: This technique sends different probe packets of different IP protocols to the target host, any response from any probe indicates that a host is active.

**# nmap -sn -PO [target IP address]**

**MSFCONSOLE**

**nmap -Pn -sS -A -oX Test 10.10.1.0/24**
Here, we are scanning the whole subnet 10.10.1.0/24 for active hosts.

**search portscan** > use **auxiliary/scanner/portscan/syn**

- **set INTERFACE eth0**
- **set PORTS 80**
- **set RHOSTS 10.10.1.5-23**
- **set THREADS 50**

**PORTS**: specifies the ports to scan (e.g., 22-25, 80, 110-900), **RHOSTS**: specifies the target address range or CIDR identifier, and THREADS: specifies the number of concurrent threads (default 1).

use **auxiliary/scanner/portscan/tcp**

use **auxiliary/scanner/smb/smb_version**


