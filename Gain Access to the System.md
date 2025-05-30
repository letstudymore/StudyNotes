
## Perform Active Online Attack to Crack the System's Password using Responder

LLMNR (Link Local Multicast Name Resolution) and NBT-NS (NetBIOS Name Service) are two main elements of Windows OSes that are used to perform name resolution for hosts present on the same link. These services are enabled by default in Windows OSes and can be used to extract the password hashes from a user.

Since the awareness of this attack is low, there is a good chance of acquiring user credentials in an internal network penetration test. By listening for LLMNR/NBT-NS broadcast requests, an attacker can spoof the server and send a response claiming to be the legitimate server. After the victim system accepts the connection, it is possible to gain the victim's user-credentials by using a tool such as Responder.py.

Responder is an LLMNR, NBT-NS, and MDNS poisoner. It responds to specific NBT-NS (NetBIOS Name Service) queries based on their name suffix. By default, the tool only responds to a File Server Service request, which is for SMB.

Here, we will use the Responder tool to extract information such as the target system's OS version, client version, NTLM client IP address, and NTLM username and password hash.

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Parrot Security** machine. Click the **MATE Terminal** icon at the top of the **Desktop** window to open a **Terminal** window.

Run **sudo responder -I eth0** command in the terminal window. In the **password for attacker** field, type **toor** and press **Enter** to run Responder tool.

**-I**: specifies the interface (here, **eth0**). However, the network interface might be different in your machine, to check the interface issue ifconfig command.

Responder starts listening to the network interface for events, as shown in the screenshot.

Click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Windows 11** machine, right-click on the **Start** icon, and click **Run**.

The **Run** window appears; type **\\CEH-Tools** in the **Open** field and click **OK**

Responder starts capturing the access logs of the **Windows 11** machine. It collects the hashes of the logged-in user of the target machine, as shown in the screenshot

By default, Responder stores the logs in **/usr/share/responder/logs**.

Now, select the hash value of **Jason** and copy it as shown in the screenshot

After copying the hash value open a terminal window, run **sudo su** command and run **pluma hash.txt** command to open a hash.txt file.

In the text editor paste the copied hash value save the file and close the text editor window.

In the terminal window run **john hash.txt** command to crack the password of Jason.

John the Ripper starts cracking the password hashes and displays the password in plain text, as shown in the screenshot.

## Reverse Shell Generator


Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Parrot Security** machine. Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**).
  
In the terminal window, run **docker run -d -p 80:80 reverse_shell_generator** command to start Reverse Shell Generator.
If you receive an error run **service apache2 stop** command and perform **Step#2** again

Now, launch **Firefox** web browser and go to **http://localhost** to access Reverse Shell Generator GUI.

We will generate a payload using predefined set of commands in Reverse Shell Generator. To do so, first we need to set the IP and port numbers

In the **IP** field, type **10.10.1.13** as listener IP and in the **Port** field, type **4444** as listener port

**MSFVenom**

Now, we will create payload using msfvenom option present in the reverse shell generator tool, to do so, click **MSFVenom** tab. You can observe, msfvenom command which you can use to generate a payload (here, **reverse.exe**)

	Here, we are selecting Windows Meterpreter Staged Reverse TCP (x64) from MSFVenom section to generate payload.

Scroll down and click on **Copy** button to copy the MSFVenom code

Switch to the terminal window and paste the copied code in the terminal and press **Enter**, to create payload with IP **10.10.1.13** and port **4444**

We will start a listener using Reverse Shell Generator, to do so, switch to the browser window and select **msfconsole** as **Type** from the drop-down under **Listener**

A code will be generated with the selected IP address and port number, click **Copy** to copy the code.

As we have started the listener, we will now, transfer the payload to the victim machine, here, we are transferring the payload using the shared folder.

Click on **Places** from the **Desktop** and click on **Home Folder** to navigate to the **/home/attacker** and copy **reverse.exe** file.

Click the **Places** menu at the top of **Desktop** and click **ceh-tools on 10.10.1.11** from the drop-down options.

If ceh-tools on 10.10.1.11 option is not present then follow the below steps to access CEH-Tools folder

If ceh-tools on 10.10.1.11 option is not present then follow the below steps to access CEH-Tools folder:

Click the Places menu present at the top of the Desktop and select Network from the drop-down options
The Network window appears; press Ctrl+L. The Location field appears; type smb://10.10.1.11 and press Enter to access Windows 11 shared folders.
The security pop-up appears; enter the Windows 11 machine credentials  and click Connect.
The Windows shares on 10.10.1.11 window appears; double-click the CEH-Tools folder.

Double-click **reverse.exe** file to run it. If a **User Account Control** pop-up appears, click **Yes**

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Parrot Security** machine. Switch to the terminal window, you can see that a session has been created with the **Windows 11** machine

Type **getuid** and press **Enter**. This displays the current user ID, as shown in the screenshot


**HoaxShell**

Now, we will gain access to the remote system using PowerShell script. To do so, switch to the browser window and select **HoaxShell** tab

In the HoaxShell section, select **PowerShell IEX** from the left pane (change the port number to **444** in the payload) and click on **Copy** button at the bottom to copy the payload

We will now run a hoaxshell listener, to do so, switch to the Firefox browser and ensure the port number is **444**, select **hoaxshell** from the **Type** drop-down under **Listener** section and click on **Copy** to copy the code.

Switch to the terminal window and paste the copied code to start the listener

Click on **Places** from the **Desktop** and click on **Home Folder** to navigate to the **/home/attacker** location and copy **shell.ps1** file and paste it in **CEHv13 Module 06 System Hacking** directory of **ceh-tools on 10.10.1.11**

Click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Windows 11** machine, navigate to **E:\CEH-Tools\CEHv13 Module 06 System Hacking** and copy the **shell.ps1** file and paste it on the **Desktop**
  
To check the logged on username type **whoami** and press **Enter**. The tool displays the username of the currently logged on user



