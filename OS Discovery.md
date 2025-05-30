
Banner grabbing, or OS fingerprinting, is a method used to determine the OS that is running on a remote target system.

- Active Banner Grabbing Specially crafted packets are sent to the remote OS, and the responses are noted, which are then compared with a database to determine the OS. Responses from different OSes vary, because of differences in the TCP/IP stack implementation.

- Passive Banner Grabbing This depends on the differential implementation of the stack and the various ways an OS responds to packets. Passive banner grabbing includes banner grabbing from error messages, sniffing the network traffic, and banner grabbing from page extensions.

nmap -A IP Address
-A: to perform an aggressive scan.

nmap -O IP Address
-O: performs the OS discovery.

nmap --script smb-os-discovery.nse IP Address
--script: specifies the customized script and smb-os-discovery.nse: attempts to determine the OS, computer name, domain, workgroup, and current time over the SMB protocol (ports 445 or 139).