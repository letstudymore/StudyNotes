
**PCAP (Packet Capture) File Structure**

**FILTERING PACKETS**

**BY IP**
ip.addr == x.x.x.x
ip.addr == x.x.x.x && ip.addr == x.x.x.x
(or ip.src == xxxx && ip.dst == xxxx - for a destination)

**FLAGS:**
tcp.flags.syn == 1  - Displays packets with the SYN flag set, indicating a connection request
tcp.flags.ack == 1 - Displays packets with the ACK flag set, indicating acknowledgment
tcp.flags.rst == 1 - Displays packets with the RST flag set, indicating a connection reset
tcp.flags.fin == 1 - Displays packets with the FIN flag set, indicating the end of a connection
tcp.flags.push == 1 - Displays packets with the PSH flag set, indicating the receiving application should process data
tcp.flags.urg == 1 - Displays packets with the URG flag set, indicating urgent data

**PROTOCOLS**
http or dns

**TCP PORTS**
tcp.port == xxx

**STRINGS (REGEX ETC)**
Crtl + F > Choose: String (Example "Password")

**FOLLOW THE PACKET**
Choose the packet > Right click > Follow > TCP Stream
Choose the packet > Right click > Follow > HTTP Streams

**EXPORTING TEXT FILES**
File > Export Objects > HTTP > Apply filters using column headers > Save



