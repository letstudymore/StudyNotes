## Perform SNMP Enumeration using SnmpWalk

Parrot

Run **snmpwalk -v1 -c public [target IP]** command (here, the target IP address is **10.10.1.22**).
**-v**: specifies the SNMP version number (1 or 2c or 3) and **-c**: sets a community string.

Run **snmpwalk -v2c -c public [Target IP Address]** command to perform SNMPv2 enumeration on the target machine (here, the target IP address is **10.10.1.22**)
**-v**: specifies the SNMP version (here, 2c is selected) and **-c**: sets a community string.


