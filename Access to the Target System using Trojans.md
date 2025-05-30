
## njRAT RAT Trojan


njRAT is a RAT with powerful data-stealing capabilities. In addition to logging keystrokes, it is capable of accessing a victim's camera, stealing credentials stored in browsers, uploading and downloading files, performing process and file manipulations, and viewing the victim's desktop.

This RAT can be used to control botnets (networks of computers), allowing the attacker to update, uninstall, disconnect, restart, and close the RAT, and rename its campaign ID. The attacker can further create and configure the malware to spread through USB drives with the help of the Command and Control server software.

The versions of the created client or host and appearance of the website may differ from what it is in this task. However, the actual process of creating the server and the client is the same, as shown in this task

In this task, we will use the Windows 11 (10.10.1.) machine as the attacker machine and the Windows Server (10.10.1.) machine as the victim machine

By default, Windows 11 machine selected

Navigate to Remote Access Trojans (RAT)\njRAT and double-click **njRAT v0.8d.exe**.

A **[Port Now]** pop-up appears, leave the port number to default and click on **OK**

The njRAT GUI appears; click the **[Build]** button located in the lower-left corner of the GUI to configure the exploit details.

The **Builder** dialog-box appears; enter the IP address of the **Windows 11** (attacker machine) machine in the **Host** field, check the options **Randomize Stub**, **USB Spread Nj8d, Protect Prosess** **[BSOD]**, leave the other settings to default, and click **Build**
In this task, the IP address of the **Windows 11** machine is **10.10.1.11**.

The **Save As** window appears; specify a location to store the server, rename it, and click **Save**

In this lab, the destination location chosen is **Desktop**, and the file is named **Test.exe**

Once the server is created, the **Doen Successfully!** pop-up appears; click **OK**

Now, use any technique to send this server to the intended target through email or any other source (in real-time, attackers send this server to the victim)
In this task, we copied the **Test.exe** file to the shared network location (**CEH-Tools**) to share the file.

to switch to the **Windows Server 2022** machine. to activate the machine, login with Administrator

Navigate to the shared network location (**CEH-Tools**), and then **Copy** and **Paste** the executable file (**Test.exe**) onto the **Desktop** of **Windows Server 2022**
  
Here, you are acting both as an **attacker** who logs into the **Windows 11** machine to create a malicious server, and as a **victim** who logs into the **Windows Server 2022** machine and downloads the server.

Double-click the server (**Test.exe**) to run this malicious executable
  
Click [Windows 11](https://labclient.labondemand.com/Instructions/5b5fbc6d-0ef1-49e8-b840-302f5a3d1d89#) to switch back to the **Windows 11** machine. Maximize njRAT GUI window. As soon as the victim (here, you) double-clicks the server, the executable starts running and the njRAT client (njRAT GUI) running in **Windows 11** establishes a persistent connection with the victim machine, as shown in the screenshot
  
Unless the attacker working on the **Windows 11** machine disconnects the server on their own, the victim machine remains under their control

The GUI displays the machine's basic details such as the IP address, User name, and Type of Operating system

Right-click on the detected victim name and hover the cursor over **Manager** and click **File Manager** from context menu
  
The **File Manager** window appears. Double-click any directory in the left pane (here, **ProgramData**); all its associated files and directories are displayed in the right pane. You can right-click a selected directory and manipulate it using the contextual options. Close the **File Manager** window.

Right-click on the detected victim name and click hover the cursor over **Manager** and click **Process Manager** from context menu.

You will be redirected to the Process Manager, where you can click on a selected process and perform actions such as **Suspend**, **Kill + Delete**, **Kill**, and **Refresh**.

Close the **Process Manager** window.

Right-click on the detected victim name and click hover the cursor over **Manager** and click **Registey** from context menu.

Window showing the registries folders will be opened, choose a registry directory from the left pane, and right-click on its associated registry files.
  
A few options appear for the files; you can use these to manipulate them. Close the window displaying Registry folders.

Right-click on the detected victim name and hover the cursor over **Manager** and click **Remote Shell** from context menu.

This launches a remote command prompt for the victim machine (**Windows Server 2022**)

In the text field present in the lower section of the window, type the command **ipconfig/all** and press **Enter**.

Similarly, you can issue all other commands that can be executed in the command prompt of the victim machine. Close the **Remote Shell** window.
  
Right-click on the victim name, and then select **Remote Desktop**.

This launches a remote desktop connection without the victim's awareness.
It might take a while for the screen to appear. If the screen is blank then switch to **Windows Server 2022** machine and unlock the machine.

Now, you will be able to remotely spy the activities performed on the victim machine.

On completing the task, close the **Remote Desktop** window.
If a Hacked pop-up appears, click Continue to close it.

In the same way, right-click on the victim name, and select **Remote Cam** to spy on them and track voice conversations.

to switch to the **Windows Server 2022** machine. Assume that you are a legitimate user and perform a few activities such as logging into any website or typing some text in text documents.

The Keylogger window appears; wait for the window to load.

The window displays all the keystrokes performed by the victim on the **Windows Server 2022** machine, as shown in the screenshot.

A **Chat** pop-up appears; enter a nickname (here, **Hacker**) and click **OK**.

A chat box appears; type a message, and then click **Send**.

Seeing this, the victim becomes alert and attempts to close the chatbox. Irrespective of what the victim does, the chat box remains for open as long as the attacker uses it.

Surprised by the behavior, the victim (you) attempts to break the connection by restarting the machine. As soon as this happens, njRAT loses its connection with **Windows Server 2022**, as the machine is shut down in the process of restarting.

However, as soon as the victim logs in to their machine, the njRAT client automatically establishes a connection with the victim.
  
On completion of this lab, click [Windows Server 2022](https://labclient.labondemand.com/Instructions/5b5fbc6d-0ef1-49e8-b840-302f5a3d1d89#) to switch to the **Windows Server 2022** machine, launch **Task Manager**, click on **More details** and look for the **Explorer.exe (32 bit)** process, and click **End task**.

