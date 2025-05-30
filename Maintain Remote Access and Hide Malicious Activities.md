
## User System Monitoring and Surveillance using Spyrix

**Windows Server 2022** machine, navigate to **Z:\CEHv13 Module 06 System Hacking\Spyware\General Spyware\Spyrix** and double-click **spm_setup.exe**

Follow the wizard driven steps to install Spyrix Personal Monitor
In the **Welcome to the Spyrix Personal Monitor 11.6.15 Setup Wizard**, leave the **Enter email** field as blank and click **Next**

At the end of the installation, ensure that the **Sign in your Online Monitoring account** checkbox is selected and click on **Finish**

At the end of the installation, ensure that the **Sign in your Online Monitoring account** checkbox is selected and click on **Finish**

In the **How do you want to open this?** pop-up appears, select **Firefox** from the list and click **OK**
If the **Spyrix webpage** appears in **Microsoft Edge** browser, then continue in Edge browser
In the **Spyrix Personal Monitor - Settings Wizard** click **Skip Wizard**, click **Close** in the next window, and close the **Spyrix Personal Monitor** window
  
In the **Account registration** web page, enter an email address and password and click **Sign up**

**Spyrix Personal Monitor** webpage appears, minimize the window

Now, click **Type here to search** field on the **Desktop**, search for **Remote** and click **Remote Desktop Connection** from the results

The **Remote Desktop Connection** window appears. In the **Computer** field, type the target system's IP address (here, **10.10.1.19** [**Windows Server 2019**]) and click **Show Options**
  
In the **User name** field, type **Jason** and click **Connect**

In the **Windows Security** pop-up, enter the password as **qwerty** and click **OK**
Here, we are using the target system user credentials obtained from the previous lab

A **Remote Desktop Connection** window appears; click **Yes**
Networks screen appears, click **Yes** to allow your PC to be discoverable by other PCs and devices on the network

Minimize the **Remote Desktop Connection** window

Navigate to **Z:\CEHv13 Module 06 System Hacking\Spyware\General Spyware\Spyrix** and copy **spm_setup.exe**

Switch to the **Remote Desktop Connection** window and paste the **spm_setup.exe** file on the target system's **Desktop**

Double-click the **spm_setup.exe** file

In the **Select Setup Language** pop-up, click on **OK**. In the **Welcome to the Spyrix Personal Monitor 11.6.15 Setup Wizard**, enter the email address that you have entered while registering for Spyrix in **Step#7** and click **Next**

Follow the wizard driven steps to install **Spyrix Personal Monitor**. In the final window, uncheck **Sign in your Online Monitoring account** checkbox and click **Finish**

Delete the Spyrix setup (**spm_setup.exe**) from **Desktop**

Close the **Remote Desktop Connection** by clicking on the close icon (**X**)
If a **Remote Desktop Connection** pop-up appears saying Your remote session will be disconnected, click **OK**

Now, maximize the browser window, **A new computer has been connected** window appears, close the pop-up window

to switch to the **Windows Server 2019** machine. Click [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#), click **Jason** from the left pane and log in with the password **qwerty**

Open any web browser (here, we are using **Google Chrome**) and browse any website

Once you have performed some user activities, leave the machines as it is and click on [Windows Server 2022](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to **Windows Server 2022** machine
If **Server Manager** window appears, close it
  
In the **Windows Server 2022** machine, maximize the **Firefox** browser window and reload the **Spyrix Personal Monitor** webpage

Click on **Summary** to view the events performed by **Jason** on the **Windows Server 2019** machine
  
Navigate to **Users activity** from the left-pane to view the user activities on the **Windows Server 2019** machine
If a black calendar icon appears, reload the page

Click on **Screenshots** to view the screenshots that were captured from the target machine

