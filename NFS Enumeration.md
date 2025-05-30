
## Perform NFS Enumeration using RPCScan and SuperEnum

RPCScan communicates with RPC (remote procedure call) services and checks misconfigurations on NFS shares. It lists RPC services, mountpoints,and directories accessible via NFS. It can also recursively list NFS shares. SuperEnum includes a script that performs a basic enumeration of any open port, including the NFS port (2049).


Having enabled the NFS service, it is necessary to check if it is running on the target system (**Windows  2019**). In order to do this, we will use **Parrot Security** machine.

**nmap -p 2049 [Target IP Address]**

**SUPERENUM**

Run **cd SuperEnum** command to navigate to the **SuperEnum** folder.

Run **echo "10.10.1.19" >> Target.txt** command to create a file having a target machine's IP address (**10.10.1.19**).

Execute **./superenum** command. Under **Enter IP List filename with path**, type **Target.txt**, and press **Enter**.

If you get an error running the ./superenum script, execute **chmod +x superenum** command, then repeat **Step#13**.


**RPCSCAN**

Now, we will perform NFS enumeration using RPCScan. To do so, run **cd RPCScan** command.

Execute **python3 rpc-scan.py [Target IP address] --rpc** command (here, the target IP address is **10.10.1.19**, the **Windows  2019** machine).
**--rpc**: lists the RPC (portmapper).


