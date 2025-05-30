
**Netcat**

Netcat is a networking utility that reads and writes data across network connections, using the TCP/IP protocol. It is a reliable "back-end" tool used directly or driven by other programs and scripts. It is also a network debugging and exploration tool.

**Telnet**

Telnet is a client-server network protocol. It is widely used on the Internet or LANs. It provides the login session for a user on the Internet. The single terminal attached to another computer emulates with Telnet. The primary security problems with Telnet are the following:

- It does not encrypt any data sent through the connection.
- It lacks an authentication scheme.

Telnet helps users perform banner-grabbing attacks. It probes HTTP servers to determine the Server field in the HTTP response header.

1.  switch to the **Parrot Security** machine.

2. In the **Parrot** machine, open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**).
    
3. In the terminal window, run **nc -vv www.moviescope.com 80**.
    
4. Once you hit **Enter**, the netcat will display the hosting information of the provided domain.
    
5. Now, type **GET / HTTP/1.0** and press **Enter** twice.
    
6. Netcat will perform the banner grabbing and gather information such as content type, last modified date, accept ranges, ETag, and server information.
    
7. In the terminal windows, run **clear** to clear the netcat result in the terminal window.
    
8. Now, perform banner grabbing using telnet. In the terminal window, run **telnet www.moviescope.com 80**.
    
9. Telnet will connect to the domain.
    
10. Type **GET / HTTP/1.0** and press **Enter** twice. Telnet will perform the banner grabbing and gather information such as content type, last modified date, accept ranges, ETag, and server information.
    
11. This concludes the demonstration of how to gather information about the target web server using the Netcat and Telnet utilities.