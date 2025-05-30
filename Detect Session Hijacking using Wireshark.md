
Wireshark allows you to capture and interactively browse the traffic running on a network. The tool uses WinPcap to capture packets, and so is only able to capture packets on networks that are supported by WinPcap. It captures live network traffic from Ethernet, IEEE 802.11, PPP/HDLC, ATM, Bluetooth, USB, Token Ring, Frame Relay, and FDDI networks. Security professionals can use Wireshark to monitor and detect session hijacking attempts.

Here, we will use the Wireshark tool to detect session hijacking attacks manually on the target system

We will use the **Parrot ** (**10.10.1.**) machine to carry out a session hijacking attack on the **Windows** (**10.10.1.11**) machine

to switch to the **Windows** machine

Click the windows **Search** icon on the **Desktop**, search for **Wireshark** in the search bar and launch it

**The Wireshark Network Analyzer** window appears, start capturing the network traffic on the primary network interface (here, **Ethernet**)

Now, we shall launch a session hijacking attack on the target machine (**Windows**) using **betterca**
To do so, you may either follow Steps **8-11** below, or refer to Task 2 (Intercept HTTP Traffic using bettercap) in Lab 1

to switch to the **Parrot Security** machine

Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**). Run **cd** to jump to the root directory

Run **bettercap -iface eth0** to set the network interface
**-iface**: specifies the interface to bind to (here, **eth0**)

Type **net.probe on** and press **Enter**. This module will send different types of probe packets to each IP in the current subnet for the **net.recon** module to detect them

Type **net.recon on** and press **Enter**. This module is responsible for periodically reading the system ARP table to detect new hosts on the network.
The net.recon module displays the detected active IP addresses in the network. In real-time, this module will start sniffing network packets

Type **net.sniff on** and press **Enter**. This module is responsible for performing sniffing on the network

You can observe that bettercap starts sniffing network traffic on different machines in the network, as shown in the screenshot
to switch back to the **Windows 11** machine and observe the huge number of **ARP packets** captured by the **Wireshark**, as shown in the screenshot
bettercap sends several ARP broadcast requests to the hosts (or potentially active hosts). A high number of ARP requests indicates that the system at **10.10.1.13** (the attacker's system in this task) is acting as a client for all the IP addresses in the subnet, which means that all the packets from the victim node (in this case, **10.10.1.11**) will first go to the host system (**10.10.1.13**), and then the gateway. Similarly, any packet destined for the victim node is first forwarded from the gateway to the host system, and then from the host system to the victim node.



