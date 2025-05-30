
## Perform MAC Flooding using macof

MAC flooding is a technique used to compromise the security of network switches that connect network segments or network devices. Attackers use the MAC flooding technique to force a switch to act as a hub, so they can easily sniff the traffic.

macof is a Unix and Linux tool that is a part of the dsniff collection. It floods the local network with random MAC addresses and IP addresses, causing some switches to fail and open in repeating mode, thereby facilitating sniffing. This tool floods the switch's CAM tables (131,000 per minute) by sending forged MAC entries. When the MAC table fills up, the switch converts to a hub-like operation where an attacker can monitor the data being broadcast.

 to launch **Parrot Security** machine, login 

Click **Applications** in the top-left corner of **Desktop** and navigate to **Pentesting** --> **Information Gathering** --> **wireshark**

A security pop-up appears, authenticate by providing **toor** as a password

**Wireshark Network Analyzer** window appears, start capturing the network traffic on the primary network interface (here, **eth0**)
  
Leave the **Wireshark** application running

Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Now, run **cd** command to jump to the root directory

Execute **macof -i eth0 -n 10** in the root directory
**-i**: specifies the interface and **-n**: specifies the number of packets to be sent (here, **10**).

You can also target a single system by issuing the command **macof -i eth0 -d [Target IP Address]** (**-d**: Specifies the destination IP address)

Switch to the **Wireshark** window and observe the **IPv4** packets from random IP addresses

Click on any captured **IPv4** packet and expand the **Ethernet II** node in the packet details section. Information regarding the source and destination MAC addresses is displayed, as shown in the screenshot

Similarly, you can switch to a different machine to see the same packets that were captured by Wireshark in the **Parrot Security** machine

Macof sends the packets with random MAC and IP addresses to all active machines in the local network. If you are using multiple targets, you will observe the same packets on all target machines

Close the **Wireshark** window. If an **Unsaved packets**… pop-up appears, click **Stop and Quit without Saving** to close the Wireshark application



## Perform a DHCP Starvation Attack using Yersinia

In **Parrot Security** machine, launch **Wireshark** and start packet capturing on available ethernet or interface (here,**eth0**)

Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**). Run **cd** to navigate to the root directory

Run **yersinia -I** (i maiusculo) to open Yersinia in interactive mode
**-I**: Starts an interactive session.

Yersinia interactive mode appears in the terminal window

To remove the **Notification window**, press any key, and then press **h** for help

The **Available commands** option appears, as shown in the screenshot

Press **q** to exit the help options
  
Press **F2** to select DHCP mode. In DHCP mode, **STP Fields** in the lower section of the window change to **DHCP Fields**, as shown in the screenshot

Press **x** to list available attack options

The **Attack Panel** window appears; press **1** to start a DHCP starvation attack.
  
**Yersinia** starts sending DHCP packets to the network interface as shown in the screenshot

After a few seconds, press **q** to stop the attack and terminate Yersinia, as shown in the screenshot.

Now, switch to the **Wireshark** window and observe the huge number of captured **DHCP** packets, as shown in the screenshot

Click on any DHCP packet and expand the **Ethernet II** node in the packet details section. Information regarding the source and destination MAC addresses is displayed, as shown in the screenshot
  
Close the **Wireshark** window. If an **Unsaved packets…** pop-up appears, click **Stop and Quit without Saving**

