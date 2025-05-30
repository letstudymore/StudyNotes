
  
In **Parrot Security** machine, open a new **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Now, run the **cd** command to jump to the root directory

In **Lab 5: Task 1**, from the Nmap results we can observe that other hosts in the subnet are running services such as RDP, SSH, and FTP. Therefore, we can perform password spraying on each service individually to check for correct credentials. In this task, we will be focusing on RDP. However, you can explore and check other services

Execute command **cme rdp 10.10.1.0/24 -u /root/ADtools/users.txt -p "cupcake"** to perform password spraying

**rdp**: Targets the Remote Desktop Protocol (RDP) service

**10.10.1.0/24**: IP address range to target, encompassing all hosts within the subnet 10.10.1.0 with a subnet mask of 255.255.255.0

**-u /root/ADtools/users.txt**: Specifies the path to the file containing user accounts for authentication

**-p "cupcake"**: Password which we cracked using AS-REP Roasting to test against the RDP service on the specified hosts

After the spray completion we find that user **Mark** is using the same password **cupcake** on host **10.10.1.40**. We will now try to connect to RDP as user **mark**

Click on **Menu** and search for **remmina** in the search filed; then, select **Remmina** from the results

In the **Remmina Remote Desktop Client** window, enter IP address **10.10.1.40** to connect (10.10.1.40 is the IP address of **Windows 11 (AD)** virtual machine ). A prompt appears asking **Accept certificate?** Tap **yes**.

In the **Enter RDP authentication credentials** window, enter **Mark** in the Username field and **cupcake** in the Password field; then, click **OK**

A **Remote Desktop** connection will be successfully established to the target system

