
## Sniff Credentials using the Social-Engineer Toolkit (SET)

to switch to the **Parrot Security** machine. Login using **attacker/too**

Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Run **setoolkit** to launch **Social-Engineer Toolkit**
If a **Do you agree to the terms of service [y/n]** question appears, enter **y** and press **Enter**

The **SET** menu appears, as shown in the screenshot. Type **1** and press **Enter** to choose **Social-Engineering Attacks**

A list of options for **Social-Engineering Attacks** appears; type **2** and press **Enter** to choose **Website Attack Vectors**.

A list of options in **Website Attack Vectors** appears; type **3** and press **Enter** to choose **Credential Harvester Attack Method**

Type **2** and press **Enter** to choose **Site Cloner** from the menu

Type the IP address of the local machine (**10.10.1.13**) in the prompt for "**IP address for the POST back in Harvester/Tabnabbing**" and press **Enter**

Now, you will be prompted for the URL to be cloned; type the desired URL in "**Enter the url to clone**" and press **Enter**. In this task, we will clone the URL **http://www.moviescope.com**
You can clone any URL of your choice

If a message appears that reads **Press {return} if you understand what we're saying here**, press **Enter**

After cloning is completed, a highlighted message appears. The credential harvester initiates, as shown in the screenshot

Having successfully cloned a website, you must now send the IP address of your **Parrot Security** machine to a victim and try to trick him/her into clicking on the link

Click **Firefox** icon from the top-section of the **Desktop** to launch a web browser window and open your email account (in this example, we are using **Mozilla Firefox** and **Outlook**, respectively). Log in, and compose an email
You can log in to any email account of your choice

After logging into your email account, click the **New Mail** button in the left pane and compose a fake but enticing email to lure a user into opening the email and clicking on a malicious link
A good way to conceal a malicious link in a message is to insert text that looks like a legitimate MovieScope URL (in this case), but that actually links to your malicious cloned MovieScope page

Position the cursor just above Regards to place the fake URL, then click the **Insert link** icon

In the **Insert link** window, first type the fake URL in the **Display as** field. Then, type the actual address of your cloned site in the **Web address (URL)** field and click **OK**. In this case, the text that will be displayed in the message is **www.moviescope.com/account-information** and the actual address of our cloned MovieScope site is **http://10.10.1.13**

The fake URL should appear in the message body

Verify that the fake URL is linked to the correct cloned site: in Outlook, hover over the link; the actual URL will be displayed. Once verified, send the email to the intended user

to switch to the **Windows 11** machine and login using **Admin**

Open any web browser (here, we are using **Mozilla Firefox**), sign in to the email account to which you sent the phishing mail as an attacker. Open the email you sent previously and click to open the malicious link

When the victim (you in this case) clicks the URL, a new tab opens up, and he/she will be presented with a replica of **www.moviescope.com**

The victim will be prompted to enter his/her username and password into the form fields, which appear as they do on the genuine website. When the victim enters the **Username** and **Password** and clicks **Login**, he/she will be redirected to the legitimate **MovieScope** login page. Note the different URLs in the browser address bar for the cloned and real sites

to switch back to the **Parrot Security** machine and switch to the **terminal** window

As soon as the victim types in his/her **Username** and **Password** and clicks **Login**, **SET** extracts the typed credentials. These can now be used by the attacker to gain unauthorized access to the victim's account

Scroll down to find **Username** and **Password** displayed in plain text, as shown in the screenshot




