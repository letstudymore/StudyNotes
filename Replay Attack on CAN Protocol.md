
1. In the **Attacker** machine, open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**).
    
2. Run **sudo apt-get install can-utils** to install CAN utility
    
3. Now, to setup a virtual CAN interface issue following commands:
    
    - **sudo modprobe can**
    - **sudo modprobe vcan**
    - **sudo ip link add dev vcan0 type vcan**
    - **sudo ip link set up vcan0**
    
4. To check whether Virtual CAN interface is setup successfully, run **ifconfig**. Here, **vcan0** interface is present which confirms that our Virtual CAN interface is setup successfully.
    
5. Run **chmod -R 777 ICSim** to give permissions to the ICSim folder.
    
6. Now, run **cd ICSim** to navigate to ICSim directory and execute **make** command to create two executable files for IC Simulator and CANBus Control Panel.
    
7. Run **./icsim vcan0** to start the ICSim simulator. You will see the IC Simulator interface as shown in the screenshot.
    
8. Open a new terminal tab and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**). Navigate to ICSim directory to do so run **cd ICSim/**.
    
9. Execute **./controls vcan0** to start the CANBus Control Panel. You will see the CANBus Control Panel interface as shown in the screenshot.
    
10. Now, we will start sniffer to capture the traffic sent to the ICSim Simulator by CANBus control panel simulator. To do so, open a new terminal tab and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**). Navigate to ICSim directory to do so run **cd ICSim/**.
    
11. Execute **cansniffer -c vcan0** to start sniffing on the vcan0 interface. Leave this sniffer on.
    
12. Open a new terminal and execute **sudo su** to run the programs as a root user (When prompted, enter the password toor). Navigate to ICSim directory to do so run **cd ICSim/**. To capture the logs run **candump -l vcan0**.
    
13. After starting to capture the logs, open ICSim and Controller simulator and perform functions such as acceleration, turning left/right, opening and locking doors so that logs are generated. Once you are done, terminate the ongoing process by pressing **Ctrl + C**.
    
14. Now verify if you have obtained the log file by executing **ls** command. The **.log** file has been generated as shown in the screenshot.
    
15. Now, to perform replay attack, run **canplayer -I candump-2024-05-07_063502.log** and press enter.