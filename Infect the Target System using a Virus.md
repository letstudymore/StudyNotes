
## JPS Virus Maker Tool and Infect the Target System

After performing this task, we will revert the machine to its initial state, as the **Windows Server 2019** machine will be infected by the virus. To do this, click on the Power and Display button and select the **Revert Machine**. If the Revert Machine option is not working, end the lab and re-launch it to reset the machines. To do this, click the Exit Lab option and select End lab from the drop-down menu.

In the **Windows 11** machine, navigate to JPS Virus Maker and double-click **JPS.exe**.

If an **Open File - Security** Warning pop-up appears, click **Run**.

The **JPS (Virus Maker 4.0)** window appears; tick the **Auto Startup** checkbox.

The window displays various features and options that can be chosen while creating a virus file.

From the **Virus Options**, check the **options** that you want to embed in a new virus file.
  
In this task, the options embedded in the virus file are **Disable TaskManager**, **Disable Windows Update**, **Disable Control Panel**, **Disable Drives**, **Hide Desktop Icons**, **Enable Remote Desktop**, **Remove Bluetooth**, **Turn Off Windows Firewall**, **Turn Off Windows Defender**, and **Auto Startup**.

Ensure that the **None** radio button is selected to specify the trigger event when the virus should start attacking the system after its creation.

Now, click the right arrow icon from the right-hand pane of the window to configure the virus options.

A **Virus Options** window appears.

Check the **Change Windows Password** option, and enter a password (here, **qwerty**) in the text field. Check the **Change Computer Name** option, and type **Test** in the text field.

You can even configure the virus to convert to a worm. To do this, check the **Enable Convert to Worm** checkbox, and provide a **Worm Name** (here, **fedevi**). For the worm to self-replicate after a particular time, specify the time in seconds (here, **1 second**) in the **Copy After** field.

Ensure that the **JPG Icon** radio button is selected under the **Change Icon** section. Ensure that the **None** radio button is selected in the lower part of the window.

After completing your selection of options, click the drop-down icon next to the **Create Virus!** button and select **x64(64Bit)**; click **Create Virus!**

The newly created virus (server) is placed automatically in the **folder** where jps.exe is located, but with the name **Server.exe**. Navigate to 07 Malware Threats\Virus Maker\JPS Virus Maker and observe that the newly created virus with the name **Server.exe** is available at the specified location

Now, pack this virus with a binder or virus packager and send it to the victim machine through email, chat, a mapped network drive, or other method.

In this task, we are using a mapped network drive to share the virus file to the victim machine. Assume that you are a victim and that you have received this file.

to switch to the **Windows** machine. 

Navigate to JPS Virus Maker and double-click **Server.exe** file to execute the virus.

Once you have executed the virus, close the window and you can observe that the **Desktop** screen goes blank, indicating that the virus has infected the system, as shown in the screenshot.

Surprised by the system behavior, the victim (you) attempts to fix the machine by restarting it. Once the machine has rebooted, try to log in to the machine with the provided **Username** and **Password**. You should receive the error message "the password is incorrect. Try again."

to activate the machine, login with **Administrator**

Click **OK** and login with the password that you provided at the time of virus creation (i.e., **qwerty**). You should log in to the machine with the new password

Now, try to open **Task Manager**; observe that an opening error pop-up appears, and then click **OK**

You will get a similar error for all the applications that are disabled by the virus

This is how attackers infect a system with viruses. Now before proceeding to the next task, revert the [Windows Server 2019](https://labclient.labondemand.com/Instructions/5b5fbc6d-0ef1-49e8-b840-302f5a3d1d89#) [Windows 11](https://labclient.labondemand.com/Instructions/5b5fbc6d-0ef1-49e8-b840-302f5a3d1d89#) machines to its initial state. To do this, click on the **Power and Display** button and select the **Revert Machine** option from the drop-down list as shown in the screenshot

