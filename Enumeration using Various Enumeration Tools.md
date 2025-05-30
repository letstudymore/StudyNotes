
## Enumerate Information using Global Network Inventory

Search and Type Global in the search field, the Global Network Inventory appears in the results, click Open to launch it.

The Global Network Inventory GUI appears. Click Close on the Tip of the Day pop-up.

The New Audit Wizard window appears; click Next.

Under the Audit Scan Mode section, click the Single address scan radio button, and then click Next.
	You can also scan an IP range by clicking on the IP range scan radio button, after which you will specify the target IP range.

Under the Single Address Scan section, specify the target IP address in the Name field of the Single address option (in this example, the target IP address is 10.10.1.22); Click Next.

The next section is Authentication Settings; select the Connect as radio button and enter the Windows Server 2022 machine credentials (Domain\Username: Administrator), and then click Next.

In reality, attackers do not know the credentials of the remote machine(s). In this situation, they choose the Connect as currently logged on user option and perform a scan to determine which machines are active in the network. With this option, they will not be able to extract all the information about the target system. Because this lab is just for assessment purposes, we have entered the credentials of the remote machine directly.

