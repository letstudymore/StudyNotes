
## Detect and Protect Against DDoS Attacks using Anti DDoS Guardian

In this task, we will use the **Windows Server 2019** and **Windows Server 2022** machines to perform a DDoS attack on the target system, **Windows 11**

On the **Windows 11** machine, navigate to DoS and Anti DDoS Guardian and double-click **Anti_DDoS_Guardian_setup.exe**

The **Setup - Anti DDoS Guardian** window appears; click **Next**. Follow the wizard-driven installation steps to install the application

In the **Stop Windows Remote Desktop Brute Force** wizard, uncheck the **install Stop RDP Brute Force** option, and click **Next**.

The **Select Additional Tasks** wizard appears; check the **Create a desktop shortcut** option, and click **Next**

The **Ready to Install** wizard appears; click **Install**

The **Completing the Anti DDoS Guardian Setup Wizard** window appears; ensure that **Launch Anti DDoS Guardian** option is selected and click **Finish**

The **Anti-DDoS Wizard** window appears; click **Continue** in all the wizard steps, leaving all the default settings. In the last window, click **Finish**

The **Anti DDoS Guardian** window appears, displaying information about incoming and outgoing traffic, as shown in the screenshot

to switch to the **Windows**. Login using **Administrator**

Navigate to Low Orbit Ion Cannon (LOIC) and double-click **LOIC.exe**

The **Low Orbit Ion Cannon** main window appears

Perform the following settings:

- Under the **Select your target** section, type the target IP address under the **IP** field (here, **10.10.1.), and then click the **Lock on** button to add the target devices.
- Under the **Attack options** section, select **UDP** from the drop-down list in **Method**. Set the thread's value to **5** under the **Threads** field. Slide the power bar to the middle.

Now, switch to the **Windows  2022** machine and follow **Steps#10-12** to launch LOIC and configure it

Once **LOIC** is configured on all machines, switch to each machine (**Windows Server 2019**, and **Windows 2022**) and click the **IMMA CHARGIN MAH LAZER** button under the **Ready?** section to initiate the DDoS attack on the target **Windows 11** machine

to switch back to the **Windows 11** machine and observe the packets captured by **Anti DDoS Guardian**

Observe the huge number of packets coming from the host machines (**10.10.1.19 [Windows Server 2019**] and **10.10.1.22 [Windows Server 2022]**)

Double-click any of the sessions **10.10.1. or **10.10.1.**

The **Anti DDoS Guardian Traffic Detail Viewer** window appears, displaying the content of the selected session in the form of raw data. You can observe the high number of incoming bytes from **Remote IP address 10.10.1.

You can use various options from the left-hand pane such as **Clear**, **Stop Listing**, **Block IP**, and **Allow IP**. Using the **Block IP (B)** option blocks the IP address sending the huge number of packets

In the **Traffic Detail Viewer** window, click **Block IP** option from the left pane

On completion of the task, click **Stop flooding**, and then close the LOIC window on all the attacker machines. (**Windows Server 2019** and **Windows Server 2022**)

Other DoS and DDoS protection tools such as, **DOSarrest's DDoS protection service** (https://www.dosarrest.com), **DDoS-GUARD** (https://ddos-guard.net), **Radware DefensePro X** (https://www.radware.com), **F5 DDoS Attack Protection** (https://www.f5.com) to protect organization's systems and networks from DoS and DDoS attacks