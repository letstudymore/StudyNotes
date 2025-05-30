
**Default Ports:** 
137 (UDP and TCP for name resolution)
138 (UDP for datagram service)
139 (TCP for session service)
**Sometimes administrators could set up NetBIOS on port 445**

**NMAP**

sudo nmap -sU --script nbstat.nse -p137 **TARGET IP**
sudo nmap -sU --script nbstat.nse -p138 **TARGET IP**
sudo nmap -sV --script nbstat.nse -p137 **TARGET IP**
sudo nmap -sV --script nbstat.nse -p139 **TARGET IP**

nmap -sV --script=nbstat.nse **TARGET IP**

