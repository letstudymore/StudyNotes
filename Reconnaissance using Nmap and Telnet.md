
Perform a Whois lookup to gather information about the IP address of the web server and the complete information about the domain such as its registration details, name servers, IP address, and location.

Use tools such as Netcraft (https://www.netcraft.com), SmartWhois (https://www.tamos.com), WHOIS Lookup (https://whois.domaintools.com), and Batch IP Converter (http://www.sabsoft.com) to perform the Whois lookup.

Perform DNS Interrogation to gather information about the DNS servers, DNS records, and types of servers used by the target organization. DNS zone data include DNS domain names, computer names, IP addresses, domain mail servers, service records, etc.

Use tools such as, DNSRecon (https://github.com), and Domain Dossier (https://centralops.net) to perform DNS interrogation.

Now, we will perform port scanning to gather information about the open ports and services running on the machine hosting the target website.

Click [Parrot Security](https://labclient.labondemand.com/Instructions/e68926b9-e037-4274-8217-faedd3dd3075#) to switch to the Parrot Security machine. Open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).
In this task, the target website (www.moviescope.com) is hosted by the victim machine (Windows Server 2019). Here, the host machine is the Parrot Security machine.

Now, type cd and press Enter to jump to the root directory.

In the Parrot Terminal window, run nmap -T4 -A -v [Target Web Application] command (here, the target web application is www.moviescope.com) to perform a port and service discovery scan.

The result appears, displaying the open ports and services running on the machine hosting the target website.

Scroll down to see the complete results. You can observe that the target machine name, NetBIOS name, DNS name, MAC address, OS, and other information is displayed, as shown in the screenshot.

Now, perform banner grabbing to identify the make, model, and version of the target web server software.

In the terminal window, run command telnet www.moviescope.com 80 to establish a telnet connection with the target machine.Port 80 is the port number assigned to the commonly used Internet communication protocol, Hypertext Transfer Protocol (HTTP).

The Trying 10.10.1.19… message appears; type GET / HTTP/1.0 and press Enter two times.

The result appears, displaying information related to the server name and its version, technology used.

the server is identified as Microsoft-IIS and the technology used is ASP.NET.
