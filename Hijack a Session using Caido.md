Caido assists security professionals and enthusiasts in efficiently auditing web applications. It offers exploration tools, including sitemap, history, and intercept features, which aid in identifying vulnerabilities and analyzing requests in real-time. Users can modify incoming requests using Forward and Tamper tools, enhancing testing customization and system security comprehension. Automation is facilitated through the Automate tool, allowing for faster vulnerability discovery by testing requests against large wordlists. Caido's intuitive UI simplifies security testing for both novices and experts with clear navigation and user-friendly controls.

to switch to the **Windows 11** machine. Login using **Admin**

Click windows **Search** icon on the **Desktop**, search for **cmd** and launch **Command Prompt** from search bar

Run **ipconfig/flushdns** command to reset dns cache and close the Command Prompt

Click windows **Search** icon on the **Desktop**, search for **Caido** and launch **Caido** from search bar

**Caido** application window appears, click on **menu** besides Start button and select **Edit**

In **Edit Instance** window, click on the radio button besides **All interfaces (0.0.0.0)** to listen on all the available network interfaces and click on **Save**

Click on **Start** button to start the local instance

**Welcome to Caido** pop-up appears, click on **Login** if you have an account already. If not, select **Don't have an account?**, you will be redirected to Dashboard

Login to your mail account, you will receive a verification mail from **Team Caido** copy the code and paste it in the Caido verification window

After entering the code, your account will be activated as shown in the screenshot

Navigate back to Caido application, in **Welcome to Caido** pop-up click on **Login**

**Welcome to Caido** page will appear, enter your credentials and click **Login**

Once logged in, **Register your Caido Instance** pop-up will appear. Type **Session Hijacking** and click **Register**

**Sign in with Caido** window appears, click **Allow** to allow the access. **Authorization Complete!** pop-up appears, close the web browser and return to the application

The **Caido** main window appears
If a Caido pop-up appears, click **Next** or **Ok** in all the pop-ups

Click on **+ Create a project** button to create a new project. **Create a project** pop-up appears, name it as **Session Hijacking** and click **Create**.

Click on **Intercept** option on the left pane, as shown in the screenshot below

Click the **Forwarding** icon and wait until it changes to **Queuing**. This button will trap and display the next response or request from the victim's machine in the **Intercept** tab
The **Forwarding** icon turns automatically from green to red

to switch to the **Windows Server 2019** machine. Click [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/5718c668-1e29-4e5d-97c6-1139515763ed#) to activate the machine and login using **Administrator**
Networks screen appears, click **Yes** to allow your PC to be discoverable by other PCs and devices on the network

Open **Firefox** web browser and navigate to **http://10.10.1.11:8080/ca.crt**. CA certificate will be downloaded automatically as shown in the screenshot

In **Firefox** web browser, select **Settings** from the context menu

On the **Settings** page, search for **Certificates** and open **View Certificates**

Navigate to **Authorities** tab and click on **Import…**

In **Select File containing CA certificate(s) to import** window, select the recently downloaded **ca.crt** file and click **Open**

When prompted, click the **Trust this CA to identify websites** checkbox and click on **OK**. Click **OK** in the **Certificate Manager** window

On the **Settings** page, search for **proxy** and open it

**Connection Settings** page appears and click **Manual proxy configuration** to configure a proxy

Set HTTP Proxy to **10.10.1.11** and port to **8080**, check the **Also use this proxy for HTTPS** box and click **OK**

After saving, close the **Settings** and browser windows. You have now configured the proxy settings of the victim's machine

Open a new tab in **Firefox** web browser and place your mouse cursor in the address bar, type **www.moviescope.com** and press **Enter**

If a message appears, stating that **Your connection is not private**. Click the **Advanced** button

On the next page, click **Proceed to www.moviescope.com (unsafe)** to open the website

to switch back to the attacker machine (**Windows 11**) and observe that **Caido** has begun to capture the requests of the victim's machine

On the **Requests** tab, for all www.moviescope.com requests, modify **www.moviescope.com** to **www.goodshopping.com** in all the captured GET **requests** and **Forward** all the requests

In a similar way, modify every **GET** request captured by **Caido** until you see the **www.goodshopping.com** page in the victim's machine. You will need to switch back and forth from the victim's machine to see the browser status while you do this
If you do not receive any request or you see a blank Requests tab then switch to **Windows Server 2019** machine and refresh the browser to capture the request again

The victim has navigated to **www.moviescope.com**, but now sees **www.goodshopping.com**; while the address bar displays **www. moviescope.com**, the window displays **www.goodshopping.com**

Now, we shall change the proxy settings back to the default settings. To do so, in the **Firefox** browser, select **Settings** from the context menu. On the **Settings** page, search for **proxy** and open it. **Connection Settings** page appears, check **No Proxy** radio button and click **OK**