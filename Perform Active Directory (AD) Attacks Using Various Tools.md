
## Perform Initial Scans to Obtain Domain Controller IP and Domain Name


to switch to the **Parrot Security** machine. Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Now, run the **cd** command to jump to the root directory

Execute the **nmap 10.10.1.0/24** command to scan the entire subnet and identify the DC IP address

Observe the nmap output carefully. Here, nmap shows that host **10.10.1.22** has **port** **88/TCP** **kerberos-sec** and **port 389/TCP LDAP** opened which confirms that our DC IP address is **10.10.1.22**

Now, we will scan **10.10.1.22** in more detail to obtain more information. Execute the **nmap -A -sC -sV 10.10.1.22** command

After scanning is complete, we get the domain name which is **CEH.com**

Now, we have DC IP and domain name, which can be used in the AS-REP Roasting attack



