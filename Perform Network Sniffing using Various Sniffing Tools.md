
## Perform Password Sniffing using Wireshark

In this task, we will use the Windows machine as the host machine and the **Windows 11** machine as the target machine

to switch to the Windows machine and login with **Administrator**
  
Search **Wireshark** from search bar and launch it
If the **Software update** window appears, click **Remind me later**

**The Wireshark Network Analyzer** window appears, start capturing the network traffic on the primary network interface (here, **Ethernet 2**)

**Wireshark** starts capturing all packets generated while traffic is received by or sent from your machine

to switch to the **Windows 11** machine, login using **Admin**
  
Open any web browser, and go to **http://www.moviescope.com/** (here, we are using **Mozilla Firefox**)

The **MOVIESCOPE** home page appears; login using **sam**/**test**

to switch back to **Windows Server 2019** machine, and in the **Wireshark** window, click the **Stop capturing packets** icon on the toolbar

Click **File --> Save As…** from the top-left corner of the window to save the captured packets

The **Wireshark: Save Capture File As** window appears. Select any location to save the file, specify **File name** as **Password Sniffing**, and click **Save**

In the **Apply a display filter field**, type **http.request.method == POST** and click the arrow icon (**-->**) to apply the filter
Applying this syntax helps you narrow down the search for http POST traffic
  
Wireshark only filters **http POST** traffic packets, as shown in the screenshot

Now, navigate to **Edit** --> **Find Packet** from menu bar

The **Find Packet** section appears below the display filter field

Click **Display filter**, select **String** from the drop-down options, click **Narrow & Wide** and select **Narrow (UTF-8 / ASCII)** from the drop-down options and click **Packet list**, select **Packet details** from the drop-down options
  
In the field next to **String**, type **pwd** and click the **Find** button


**Wireshark** will now display the sniffed password from the captured packets

Expand the **HTML Form URL Encoded: application/x-www-form-urlencoded** node from the packet details section, and view the captured username and password, as shown in the screenshot

to switch to the **Windows 11** machine, close the web browser, and sign out from the **Admin** account

Search **Remote Desktop Connection** from search bar and launch it
  
The **Remote Desktop Connection** dialog-box appears; click **Show Options**
If some previously accessed IP address appears in the **Computer** field, delete it

The dialog-box expands; under the **General** tab, type **10.10.1.11** in the **Computer** field and **Jason** in the **User name** field; click **Connect**

The IP address and username might differ in your lab environment. The target system credentials (**Jason** and **qwerty**) we are using here are obtained in the previous labs

The **Remote Desktop Connection** pop-up appears; click **Yes**

A remote connection to the target system (**Windows 11**) appears

If a **Choose privacy settings for your device** window appears, click on **Next** in the next window click on **Next** and in the next window click on **Accept**
  
In the **Desktop** window, click windows **Search** icon and search for **Control Panel** in the search bar and launch it

The **Control Panel** window appears; navigate to **System and Security --> Windows Tools**. In the **Windows Tools** control panel, double-click **Services**

The **Services** window appears. Choose **Remote Packet Capture Protocol v.0 (experimental)**, right-click the service, and click **Start**

The **Status** of the **Remote Packet Capture Protocol v.0 (experimental)** service will change to **Running**, as shown in the screenshot.

Close all open windows on the **Windows 11** machine and close **Remote Desktop Connection**
If a **Remote Desktop Connection** pop-up appears, click **OK**
  
Now, in **Windows Server 2019**, launch **Wireshark** and click on **Capture options** icon from the toolbar

The **Wireshark**. **Capture Options** window appears; click the **Manage Interfaces…** button

The **Manage Interfaces** window appears; click the **Remote Interfaces** tab, and then the **Add a remote host and its interface** icon (**+**)

The **Remote Interface** window appears. In the **Host** text field, enter the IP address of the target machine (here, **10.10.1.11**); and in the **Port** field, enter the port number as **2002**

Under the **Authentication** section, select the **Password authentication** radio button and enter the target machine's user credentials (here, **Jason** and **qwerty**); click **OK**
The IP address and user credentials may differ when you perform this task
  
A new remote interface is added to the **Manage Interfaces** window; click **OK**
  
The newly added remote interface appears in the **Wireshark**. **Capture Options** window; click **Start**

Click [Windows 11](https://labclient.labondemand.com/Instructions/dcfb8d54-2566-4df5-b3e6-61c33a3d6dbd#) to switch to the **Windows 11** machine, and login using **Jason/qwerty**. Here, you are signing in as the victim

Acting as the target, open any web browser go to **http://www.goodshopping.com** (here, we are using **Mozilla Firefox**)
Although we are only browsing the Internet here, you could also log in to your account and sniff the credentials

Click [Windows Server 2019](https://labclient.labondemand.com/Instructions/dcfb8d54-2566-4df5-b3e6-61c33a3d6dbd#) to switch back to the **Windows Server 2019** machine. **Wireshark** starts capturing packets as soon as the user (here, you) begins browsing the Internet, the shown in the screenshot

After a while, click the **Stop capturing packet** icon on the toolbar to stop live packet capture

This way, you can use Wireshark to capture traffic on a remote interface
In real-time, when attackers gain the credentials of a victim's machine, they attempt to capture its remote interface and monitor the traffic its user browses to reveal confidential user information

