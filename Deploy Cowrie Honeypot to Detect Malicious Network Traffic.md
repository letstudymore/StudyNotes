
Cowrie serves as an SSH and Telnet honeypot, capable of capturing brute-force attacks and the actions taken by attackers within the shell. When operating in medium interaction mode, it replicates UNIX behavior using Python. In high interaction mode, acting as a proxy, it allows observation of attacker actions on another system via SSH and Telnet.

to switch to the **Ubuntu** machine and login with **Ubuntu**/**toor**

1. Click [Ubuntu](https://labclient.labondemand.com/Instructions/694ed99e-95e9-490a-beb4-8989eb3d4e43#) to switch to the **Ubuntu** machine and login with **Ubuntu**/**toor**.
    
2. In the **Ubuntu** machine, we will deploy **Cowrie** honeypot.
    
3. Open a **Terminal** window and execute **sudo adduser --disabled-password cowrie** to create a new user named **cowrie** without password (When prompted, enter the password **toor**, The password that you type will not be visible). Close the terminal.
    
    > Leave Full Name, Room Number, Work Phone, Home Phone, Other blank and type **Y** when prompted **Is the information correct? [Y/n]**.
        
4. Click on **Files** icon and navigate to **ceh tools on 10.10.1.11/Honeypots/Honeypot Tools** and copy **cowrie** folder and paste it into **/home/ubuntu**.
    
    > If **ceh-tools on 10.10.1.11** option is not present then follow the below steps to access **CEH-Tools** folder:
    > 
    > - Open **Files** and navigate to the **+ Other Locations** from the left pane
    > - In the **Connect to Server** field, type **smb://10.10.1.11** and press **Enter** to access **Windows 11** shared folders.
    > - The security pop-up appears; enter the **Windows 11** machine credentials (**Admin**) and click **Connect**.
    > - The **Windows shares on 10.10.1.11** window appears; double-click the **CEH-Tools** folder.
       
    
5. Open a new terminal and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**). Now, jump into Cowrie directory using **cd cowrie** command.
    
    > The password that you type will not be visible.
    
6. Run **pip install --upgrade -r requirements.txt** to install all the required dependencies.
        
    
7. Run **cd ..** command to jump back to **/home/ubuntu** and run **chmod -R 777 cowrie** to modify the file permissions of cowrie folder.
    
8. Run **iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-port 2222** to redirect the traffic coming on port 22 to port 2222. This redirection channels incoming traffic to a Cowrie honeypot, ensuring the protection of the primary system by segregating potential risks.
    
    > Here,
    > 
    > - **-t nat** specifies the table in which the rule should be added. Here, it is the network address translation (NAT) table.
    > - **-A PREROUTING** specifies that the rule should be appended to the PREROUTING chain. The PREROUTING chain is traversed by packets as soon as they come in, before any routing decisions are made.
    > - **-p tcp** specifies the protocol to which the rule should apply. Here, it is TCP.
    > - **--dport 22** specifies the destination port. Here, it is port 22, which is commonly used for SSH (Secure Shell) connections.
    > - **-j REDIRECT** specifies the target of the rule. It instructs iptables to redirect the packet to another destination instead of its original destination. Here, the destination will be redirected.
    > - **--to-port 2222** specifies the port to which the packet should be redirected. Here, it is port 2222. So, any incoming TCP packets to port 22 will be redirected to port 2222.

    
9. To facilitate enhanced security measures, run the following commands to configure authbind, enabling the Cowrie honeypot to operate on port 22 without requiring root privileges:
    
    - Run **touch /etc/authbind/byport/22** to create an authbind configuration file for port 22, essential for granting permission to the Cowrie honeypot to listen on that specific port.
    - Run **chown cowrie:cowrie /etc/authbind/byport/22** to change the ownership of the authbind configuration file for port 22 to the user and group "cowrie," ensuring proper access permissions for the Cowrie honeypot to operate on that port.
    - Run **chmod 770 /etc/authbind/byport/22** to set appropriate permissions on the authbind configuration file for port 22, ensuring that the Cowrie honeypot has the necessary access to operate on the port without requiring root privileges.
    
    
10. Run **virtualenv --python=python3 cowrie-env** to create a virtual environment. Run **source cowrie-env/local/bin/activate** to activate the environment.
        
    
11. Exit the root privileged terminal using **exit** command. Navigate to cowrie directory using **cd cowrie** command. Here, run **bin/cowrie start** to initiate the Cowrie honeypot and begin monitoring and logging incoming traffic for security analysis and threat detection purposes.
    
    
12. In the terminal, acquire root privileges using **sudo su** command and execute **cd var/log/cowrie/** to navigate to **var/log/cowrie**. Now, run **tail cowrie.log** to view the log file.
    
    > Here, **Ready to accept SSH connections** confirms that the honeypot is successfully setup.
    
    
13. Now, we will use **Parrot Security** machine as an attacker to attack the honeypot running SSH service. To do so, firstly we will scan the target machine for open SSH port.
    
14. Click [Parrot Security](https://labclient.labondemand.com/Instructions/694ed99e-95e9-490a-beb4-8989eb3d4e43#) to switch to **Parrot Security** machine and use **toor** as password. Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**).
    
15. In the terminal, run **nmap -p- -sV 10.10.1.9** command to discover open ports and services.
    
16. You can observe that the port 22 is open and is the default port used for SSH connection. Since the port is open we will try to connect to the machine using SSH.
    
    > Here, you can also observe the SSH service running on port 2222 that is a honeypot that we have deployed. Attackers will target the SSH service running on default SSH port (22).
        
    
17. To establish a connection to the target machine via SSH, we will use PuTTY. Initiate the PuTTY interface by executing **putty** command.
    
    
    
18. The **PuTTY Configuration (as superuser)** window appears. Enter the IP address of the target machine (here, **10.10.1.9**) in the **Host Name (or IP address)** field, and proceed by clicking on **Open** button.
    
    > PuTTY Security Alert (as superuser) window appears, click **Accept**.
    
    
    
19. In **10.10.1.9 - PuTTY (as superuser)** window, type **ubuntu** in **login as** field and password as **toor**, it responds with **Access denied**. Try a random set of passwords to bruteforce into the target machine.
    
    
    
20. Click [Ubuntu](https://labclient.labondemand.com/Instructions/694ed99e-95e9-490a-beb4-8989eb3d4e43#) to switch back to **Ubuntu** machine, and run **tail cowrie.log**. Here, observe the logs generated when the attacker tried to connect to the SSH service on the **Ubuntu** machine using PuTTY. These log entries serves as evidence of the attacker's unauthorized access attempts.
    
    
21. Click [Parrot Security](https://labclient.labondemand.com/Instructions/694ed99e-95e9-490a-beb4-8989eb3d4e43#) to switch back to **Parrot Security** machine. In the terminal window, open the PuTTY interface by executing **putty** command.
    
22. In the **PuTTY Configuration (as superuser)** window, type the IP address of the target machine (here, **10.10.1.9**) under **Host Name (or IP address)** section and click on **Open**.
    
    > If **PuTTY Security Alert (as superuser)** window appears, click **Accept**.
    
23. In **10.10.1.9 - PuTTY (as superuser)** window, type login as **root** and type a random password of your choice.
    
    
24. You are now in the honeypot, execute various commands to gather intelligence and explore the system.
    
    - Run **id** command to retrieve information about the current user and group.
    - To identify the username associated with the active session, execute **whoami** command.
    - Run **pwd** to determine the present working directory within the system.
    - Run **cd ..** to navigate to the root directory.
    - Run **ls** to list the files available in the directory.
    - Continue the reconnaissance, run **ls -la** command to list detailed information about files and directories in the current location.
    
    > The Cowrie honeypot has default credentials set to **root** / ***** (with root as username and taking any character or word as a correct password). After obtaining access to the SSH service, attacker runs the above commands giving him a sense of compromising the target system successfully. However, all these interactions are captured by the virtual environment which was created while setting up Cowrie honeypot, without affecting actual SSH service running on the target system.
    
    
25. Click [Ubuntu](https://labclient.labondemand.com/Instructions/694ed99e-95e9-490a-beb4-8989eb3d4e43#) to switch back to the **Ubuntu** machine and execute **tail cowrie.log** command to view the logs. These logs will capture the activities performed by the attacker within the Cowrie honeypot environment, including the execution of commands.
    
    
    > This will notify you of the intrusion, allowing you to implement specific security measures to sever communication with the attacker's machine.