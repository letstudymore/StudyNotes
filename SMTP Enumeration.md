
## Perform SMTP Enumeration using Nmap

In the **Parrot Security** machine, open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**).

Run **nmap -p 25 --script=smtp-enum-users [Target IP Address]** command (here, the target IP address is **10.10.1.19**).
**-p**: specifies the port, and **--script**: argument is used to run a given script (here, the script is **smtp-enum-users**).

Run **nmap -p 25 --script=smtp-open-relay [Target IP Address]** command (here, the target IP address is **10.10.1.19**).
**-p**: specifies the port, and **-script**: argument is used to run a given script (here, the script is **smtp-open-relay**).

Run **nmap -p 25 --script=smtp-commands [Target IP Address]** command (here, the target IP address is **10.10.1.19**).
 **-p**: specifies the port, and **-script**: argument is used to run a given script (here, the script is **smtp-commands**).

