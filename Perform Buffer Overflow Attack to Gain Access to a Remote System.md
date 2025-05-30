

In this task, we use a **Parrot Security** (**10.10.1.13**) machine as the host machine and a **Windows 11** (**10.10.1.11**) machine as the target machine.

Windows

System Hacking\Buffer Overflow Tools\vulnserver**, right-click the file **vulnserver.exe**, and click the **Run as administrator** option

**Vulnserver** starts running, as shown in the screenshot

**Buffer Overflow Tools\Immunity Debugger**, right-click **ImmunityDebugger_1_85_setup.exe**, and click the **Run as administrator** option
  
**Immunity Debugger Setup** pop-up appears, click **Yes** to install Python

The **Immunity Debugger Setup: License Agreement** window appears; click the **I accept** checkbox and then click **Next**

After completion of installation, click on **Close**. **Immunity Debugger Setup** pop-up appears click **OK** to install python

After the completion of the installation, navigate to the **Desktop**, right-click the **Immunity Debugger** shortcut, and click **Run as administrator**

Now, click **File** in the menu bar, and in the drop-down menu, click **Attach**
  
The **Select process to attach** pop-up appears; click the **vulnserver** process and click **Attach**

**Immunity Debugger** showing the **vulnerserver.exe** process window appears

You can observe that the status is **Paused** in the bottom-right corner of the window
  
Click on the **Run program** icon in the toolbar to run **Immunity Debugger**.

Keep **Immunity Debugger** and **Vulnserver** running, and click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch to the **Parrot Security** machine.
  
We will now use the Netcat command to establish a connection with the target vulnerable server and identify the services or functions provided by the server

In the **Parrot Security** machine, open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Now, run **cd** command to jump to the root directory

Execute **nc -nv 10.10.1.11 9999** command
Here, **10.10.1.11** is the IP address of the target machine (**Windows 11**) and **9999** is the target port

The **Welcome to Vulnerable Server!** message appears; type **HELP** and press **Enter**

A list of **Valid Commands** is displayed, as shown in the screenshot

Type **EXIT** and press **Enter** to exit the program

Now, we will generate spike templates and perform spiking
Spike templates define the package formats used for communicating with the vulnerable server. They are useful for testing and identifying functions vulnerable to buffer overflow exploitatio

To create a spike template for spiking on the STATS function, run **pluma stats.spk** command to open a text editor

In the text editor window, type the following script:

**s_readline();**
**s_string("STATS ");**
**s_string_variable("0");**
  
Press **Ctrl+S** to save the script file and close the text editor

Now, in the terminal window, run **generic_send_tcp 10.10.1.11 9999 stats.spk 0 0** command to send the packages to the vulnerable server
Here, **10.10.1.11** is the IP address of the target machine (**Windows 11**), **9999** is the target port number, **stats.spk** is the spike_script, and **0** and **0** are the values of **SKIPVAR** and **SKIPSTR**


Now, click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the target machine (here, **Windows 11**), and in the **Immunity Debugger** window, you can observe that the process status is still **Running**, which indicates that the STATS function is not vulnerable to buffer overflow. Now, we will repeat the same process with the TRUN function

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch back to the **Parrot Security** machine

In the **Terminal** window, press **Ctrl+C** to terminate stats.spk script.

Now, run **pluma trun.spk** command to open a text editor

In the text editor window, type the following script:

s_readline();
s_string("TRUN ");
s_string_variable("0");
  
Press **Ctrl+S** to save the script file and close the text editor

Now, in the **terminal** window, run **generic_send_tcp 10.10.1.11 9999 trun.spk 0 0** command to send the packages to the vulnerable server
Here, **10.10.1.11** is the IP address of the target machine (**Windows 11**), **9999** is the target port number, **trun.spk** is the **spike_script**, and **0** and **0** are the values of **SKIPVAR** and **SKIPSTR**

Now, click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch to the target machine (here, **Windows 11**), and in the **Immunity Debugger** window, you can observe that the process status is changed to **Paused**, which indicates that the TRUN function of the vulnerable server is having buffer overflow vulnerability

Spiking the TRUN function has overwritten stack registers such as EAX, ESP, EBP, and EIP. Overwriting the EIP register can allow us to gain shell access to the target system

You can observe in the top-right window that the EAX, ESP, EBP, and EIP registers are overwritten with ASCII value "A", as shown in the screenshot

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch to the **Parrot Security** machine and press **Ctrl+Z** to terminate the script running in the terminal window

After identifying the buffer overflow vulnerability in the target server, we need to perform fuzzing. Fuzzing is performed to send a large amount of data to the target server so that it experiences buffer overflow and overwrites the EIP register
  
Click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch back to the **Windows 11** machine and close **Immunity Debugger** and the vulnerable server process

Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch back to the **Parrot Security** machine

Minimize the **Terminal** window. Click the **Places** menu present at the top of the **Desktop** and select **Network** from the drop-down options

The **Network** window appears; press **Ctrl+L**. The **Location** field appears; type **smb://10.10.1.11** and press **Enter** to access **Windows 11** shared folders

The security pop-up appears; enter the **Windows 11** machine credentials and click **Connect**

The **Windows shares on 10.10.1.11** window appears; double-click the **CEH-Tools** folder

Navigate to **CEHv13 Module 06 System Hacking\Buffer Overflow Tools** and copy the **Scripts** folder. Close the window

Paste the **Scripts** folder on the **Desktop**
  
Now, we will run a Python script to perform fuzzing. To do so, switch to the **terminal** window, run **cd /home/attacker/Desktop/Scripts/**, command to navigate to the **Scripts** folder on the **Desktop**

Execute **chmod +x fuzz.py** to change the mode to execute the Python script

Run **./fuzz.py** Python fuzzing script against the target machine
When you execute the Python script, buff multiplies for every iteration of a while loop and sends the buff data to the vulnerable server
  
Click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch to the **Windows 11** machine and maximize the **Command Prompt** window running the vulnerable server

You can observe the connection requests coming from the host machine (**10.10.1.13**)

Now, switch to the **Immunity Debugger** window and wait for the status to change from **Running** to **Paused**

In the top-right window, you can also observe that the EIP register is not overwritten by the Python script

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch to the **Parrot Security** machine. In the **Terminal** window, press **Ctrl+C** to terminate the Python script

A message appears, saying that the vulnerable server crashed after receiving approximately **10200** bytes of data, but it did not overwrite the EIP register

Click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch back to the **Windows 11** machine and close **Immunity Debugger** and the vulnerable server process

Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**

Through fuzzing, we have understood that we can overwrite the EIP register with 1 to 5100 bytes of data. Now, we will use the **pattern_create** Ruby tool to generate random bytes of data

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch back to the **Parrot Security** machine
  
In a new **Terminal** window execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)
  
Now, run **cd** command to jump to the root directory

Run **/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 10400** command
**-l**: length, **10400**: byte size (here, we take the nearest even-number value of the byte size obtained in the previous step)

It will generate a random piece of bytes; right-click on it and click **Copy** to copy the code and close the **Terminal** window

Now, switch back to the previously opened terminal window, run **pluma findoff.py** command

A Python script file appears; replace the code within inverted commas ("") in the **offset** variable with the copied code

Press **Ctrl+S** to save the script file and close it

  
Now, execute **./findoff.py** command to run the Python script to send the generated random bytes to the vulnerable server
When the above script is executed, it sends random bytes of data to the target vulnerable server, which causes a buffer overflow in the stack
  
Click [Windows 11](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) switch to the **Windows 11** machine

In the **Immunity Debugger** window, you can observe that the EIP register is overwritten with random bytes
  
Note down the random bytes in the EIP and find the offset of those bytes

Click [Parrot Security](https://labclient.labondemand.com/Instructions/b23f3920-d498-4113-9bbb-12cd16f9c53f#) to switch to the **Parrot Security** machine

In a new **Terminal** window, execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**)

Now, run **cd** command to jump to the root directory

In the **Terminal** window, run **/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -l 10400 -q 386F4337**

**-l**: length, **10400**: byte size (here, we take the nearest even-number value of the byte size obtained in the **Step#63**), **-q**: offset value (here, **77716E71** identified in the previous step).

The byte length might differ in your lab environment



