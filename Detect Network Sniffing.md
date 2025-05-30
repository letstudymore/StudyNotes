
## ARP Poisoning and Promiscuous Mode in a Switch-Based Network

In this task, we will use the Windows machine as the host machine to perform ARP poisoning, and will sniff traffic flowing between the **Windows 11** and **Parrot Security** machines. We will use the same machine (**Windows Server 2019**) to detect ARP poisoning and use the **Windows 11** machine to detect promiscuous mode in the network

to switch to the **Windows** machine

In the **Desktop** window, click windows **Search** icon and search for **cain** in the search bar and launch it

The **Cain & Abel** main window appears, click **Configure** from the menu bar to configure an ethernet card.

The **Configuration Dialog** window appears. The **Sniffer** tab is selected by default. Ensure that the **Adapter** associated with the **IP address** of the machine is selected and click **OK**

Click the **Start/Stop Sniffer** icon on the toolbar to begin sniffing


The **Cain** pop-up appears with a **Warning** message, click **OK**

Now, click the **Sniffer** tab

Click the plus (**+**) icon or right-click in the window and select **Scan MAC Addresses** to scan the network for hosts

The **MAC Address Scanner** window appears. Check the **All hosts in my subnet** radio button. Select the **All Tests** checkbox; then, click **OK**

Cain & Abel starts scanning for MAC addresses and lists all those found

After the completion of the scan, a list of all active IP addresses along with their corresponding MAC addresses is displayed, as shown in the screenshot

Now, click the **APR** tab at the bottom of the window


APR options appear in the left-hand pane. Click anywhere on the topmost section in the right-hand pane to activate the plus (**+**) icon

Click the plus (**+**) icon; a **New ARP Poison Routing** window appears; from which we can add IPs to listen to traffic

To monitor the traffic between two systems (here, **Windows 11** and **Parrot Security**), from the left-hand pane, click to select **10.10.1.11** (**Windows 11**) and from the right-hand pane, click **10.10.1.13** (**Parrot Security**); click **OK**. By doing so, you are setting Cain to perform ARP poisoning between the first and second targets
  
Click to select the created target IP address scan that is displayed in the **Configuration / Routed** **Packets** tab

After clicking on the **Start/Stop APR** icon, Cain & Abel starts ARP **poisoning** and the status of the scan changes to Poisoning, as shown in the screenshot

After clicking on the **Start/Stop APR** icon, Cain & Abel starts ARP **poisoning** and the status of the scan changes to Poisoning, as shown in the screenshot
  
Cain & Abel intercepts the traffic traversing between these two machines

To generate traffic between the machines, you need to ping one target machine using the other

to switch to the **Parrot Security** machine

Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**). Run **cd** command to jump to root directory
 
Run **hping3 [Target IP Address] -c 100000** command (here, target IP address is **10.10.1.11 [Windows 11]**)
**-c**: specifies the packet count.

This command will start pinging the target machine (**Windows 11**) with 100,000 packets
  
Leave the command running and immediately switch to the Windows machine

In the **Desktop** window, click windows **Search** icon and search for **wireshark** in the search bar and launch it

The **Wireshark Network Analyzer** window appears; click **Edit** in the menu bar and select **Preferences…**.

The **Wireshark . Preferences** window appears; expand the **Protocols** node

Scroll-down in the **Protocols** node and select the **ARP/RARP** option
  
From the right-hand pane, click the **Detect ARP request storms** checkbox and ensure that the **Detect duplicate IP address configuration** checkbox is checked; click **OK**

Now, double-click on the adapter associated with your network (here, **Ethernet2**) to start capturing the network packets

**Wireshark** begins to capture the traffic between the two machines, as shown in the screenshot

Switch to the **Cain & Abel** window to observe the packets flowing between the two machines

Now, switch to **Wireshark** and click the **Stop packet capturing** icon to stop the packet capturing

Click **Analyze** from the menu bar and select **Expert Information** from the drop-down options. The **Wireshark . Expert Information** window appears; click to expand the **Warning** node labeled **Duplicate IP address configured (10.10.1.11)**, running on the **ARP/RARP** protocol

Arrange the **Wireshark . Expert Information** window above the **Wireshark** window so that you can view the packet number and the **Packet details** section
  
In the **Wireshark . Expert Information** window, click any packet (here, **463**)

On selecting the packet number, **Wireshark** highlights the packet, and its associated information is displayed under the packet details section. Close the **Wireshark . Expert Information** window

The warnings highlighted in yellow indicate that duplicate IP addresses have been detected at one MAC address, as shown in the screenshot

ARP spoofing succeeds by changing the IP address of the attacker's computer to the IP address of the target computer. A forged ARP request and reply packet find a place in the target ARP cache in this process. As the ARP reply has been forged, the destination computer (target) sends frames to the attacker's computer, where the attacker can modify the frames before sending them to the source machine (User A) in an MITM attack. At this point, the attacker can launch a DoS attack by associating a non-existent MAC address with the IP address of the gateway or may passively sniff the traffic, and then forward it to the target destination.


##### Promiscuous Mode NMAP

Now, we shall perform promiscuous mode detection using Nmap
to switch to the **Ubuntu** machine and login with **Ubuntu**/**toor**

In the Ubuntu machine, open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor)

Run **apt install nmap -y** command to install nmap.

Run nmap --script=sniffer-detect [Target IP Address/ IP Address Range] (here, target IP address is 10.10.1.19 [Windows Server 2019]) to start scanning.

The scan results appear, displaying Likely in promiscuous mode under the Host script results section. This indicates that the target system is in promiscuous mode.

