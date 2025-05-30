

1. In the **Parrot ** machine, open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**).
    
2. Enumerate the directories used by web servers and web applications, in the terminal window. Run **nmap -sV --script=http-enum [target website]**.
    
3. In this scan, we are enumerating the **www.goodshopping.com** website.
    
4. This script enumerates and provides you with the output details.
    
5. The next step is to discover the hostnames that resolve the targeted domain.
    
6. In the terminal window, run **nmap --script hostmap-bfk -script-args hostmap-bfk.prefix=hostmap- www.goodshopping.com**.
    
7. Perform an HTTP trace on the targeted domain. In the terminal window, run **nmap --script http-trace -d www.goodshopping.com**.
    
8. This script will detect a vulnerable server that uses the TRACE method by sending an HTTP TRACE request that shows if the method is enabled or not.
    
9. Now, check whether Web Application Firewall is configured on the target host or domain. In the terminal window, run **nmap -p80 --script http-waf-detect www.goodshopping.com**.
    
10. This command will scan the host and attempt to determine whether a web server is being monitored by an IPS, IDS, or WAF.
    
11. This command will probe the target host with malicious payloads and detect the changes in the response code.
    
12. This concludes the demonstration of how to enumerate web server information using the Nmap Scripting Engine (NSE).