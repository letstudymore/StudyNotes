
to switch to the **Windows 11** machine

Navigate to Session Hijacking\Hetty and double-click **hetty.exe**
If an **Open File - Security Warning** window appears, click **Run**

A **Command Prompt** window appears, and Hetty initializes

Now, minimize all the windows and launch any web browser (here, **Mozilla Firefox**). Go to **http://localhost:8080** to open Hetty dashboard

In the Hetty dashboard, click **MANAGE PROJECTS** button

**Projects** page appears, type **Project name** as **Moviescope** and click **+ CREATE & OPEN PROJECT** button

You can observe that a new project name **Moviescope** has been created under **Manage projects** section with a status as **Active**

Click **Proxy logs** icon from the left-pane

A **Proxy logs** page appears, as shown in the screenshot

to switch to the **Windows 2022** machine. and login using **Administrator**
Networks screen appears, click **Yes** to allow your PC to be discoverable by other PCs and devices on the network

Open **Google Chrome** web browser, click the **Customize and control Google Chrome** icon, and select **Settings** from the context menu

On the **Settings** page, scroll-down and click **System** in the left-pane

Scroll-down to the **System** section and click **Open your computer's proxy settings** to configure a proxy.

- Under the **Use a proxy server** option, click the **Off** button to switch it **On**.
- In the **Address** field, type **10.10.1.11** (the IP address of the attacker's machine, here, **Windows 11**).
- In the **Port** field, type **8080**.
- Click **Save**

After saving, close the **Settings** and browser windows. You have now configured the proxy settings of the victim's machine

Now, in the web browser go to **http://www.moviescope.com**

to switch to the **Windows 11** machine

You can observe that the logs are captured in the **Proxy logs** page. Here, we are focusing on logs associated with moviescope.com website

to switch back to the **Windows  2022** machine

In the **MovieScope** website, login as a victim with credentials as **sam**/**test**

to switch to the **Windows 11** machine

In the **Proxy logs** page, scroll-down to check more logs on moviescope website. Check for **POST** log captured for the target website

Select the **POST request** and in the lower section of the page, select **Body** tab under **POST** section

Under the **Body** tab, you can observe the captured user credentials, as shown in the screenshot

The captured credentials can be used to log in to the target user's account and obtain further sensitive information

Now, we shall change the proxy settings back to the default settings. to switch back to the **Windows 2022** machine and perform **Steps 13-15** again




