
MQTT is a lightweight messaging protocol that uses a publish/subscribe communication pattern. 

1. To install the **MQTT Broker** on the **Windows  2019**, 
    
2. Navigate to Bevywise IoT Simulator folder and double-click on the **Bevywise_MQTTRoute_4.exe** file.
    
3. If **Open File - Security Warning** popup appears, click **Run**.
    
4. The **Setup - MQTTRoute 4.0** window opens. Select **I accept the agreement** and click on **Next**. Follow the wizard driven steps to install the tool.
    
5. After the installation completes, click on **Finish**. Ensure that **Launch MQTTRoute** is checked.
    
6. The MQTTRoute will execute and the command prompt will appear. You can see the **TCP** port using **1883**.
    
7. We have installed MQTT Broker successfully and leave the Bevywise MQTT **running**.
    
8. To create IoT devices, we must install the **IoT simulator** on the client machine.
    
9. switch to **Windows  2022** machine. 
    
10. Navigate to Bevywise IoT Simulator folder and double-click on the **Bevywise_IoTSimulator_3.exe** file.
    
11. If **Open File - Security Warning** popup appears, click **Run**..
    
12. The **Setup-IoTSimulator_3 3.0** setup wizard opens. Select **I accept the agreement** and follow the wizard driven steps.
    
13. To complete the installation, select **Yes, restart the computer now** and click on **Finish** to complete the installation.
    
14. After restarting, Bevywise IoT Simulator is installed successfully. To launch the **IoT simulator**, navigate to the **C:\Bevywise\IotSimulator\bin** directory and double-click on the **runsimulator.bat** file.
    
15. Upon double-clicking the **runsimulator.bat** file opens in the command prompt. If **How do you want to open this?** pop-up appears, select **Microsoft Edge** browser and click **OK** to open the URL **http://127.0.0.1:9000/setnetwork?network=HEALTH_CARE**.
    
16. The web interface of the IoT Simulator opens in Edge browser. In the IoT Simulator, you can view the default network named **HEALTH_CARE** and several devices.
    
17. Next, we will create a **virtual IoT network** and **virtual IoT devices**. Click on the **menu** icon and select the **+New Network** option.
    
18. The **Create New Network** popup appears. Type any name (here, **CEH_FINANCE_NETWORK**) and description. Click on **Create**.
    
19. In the next screen, we will setup the **Simulator Settings**. Set the **Broker IP Address** as **10.10.1.19** (the IP address of the **Windows Server 2019** ). Since we have installed the Broker on the web server, the created network will interact with the server using MQTT Broker. Do not change default settings and click on **Save**.
    
20. To proceed with the network creation, click on **Yes**.
    
21. To add IoT devices to the created network, click on the **Add blank Device** button.
    
22. The **Create New Device** popup opens. Type the device name (here, we use **Temperature_Sensor**), enter Device Id (here, we use **TS1**), provide a **Description** and click on **Save**.
    
23. The device will be added to the **CEH_FINANCE_NETWORK**.
    
24. To connect the Network and the added devices to the server or Broker, click on the **Start Network** red color circular icon in right corner.
    
25. When a connection is established between the network and the added devices and the web server or the MQTT Broker, the red button turns into **green**.
    
26. Next, switch to the [Windows Server 2019](https://labclient.labondemand.com/Instructions/a7ad206c-dbb0-4409-9308-112bc753c2ac#) machine. Open a web browser, and go to **http://localhost:8080** and login using **admin/admin** (here, we are using **Firefox** Browser).
    
27. Since the Broker was **left running**, you can see a connection request from machine **10.10.1.22** for the device **TS1** under **Recent Connections** section.
    
28. Switch back to Windows Machine
    
29. Next, we will create the **Subscribe command** for the device Temperature_Sensor.
    
30. Click on the **Plus** icon in **the top right corner** and select the **Subscribe to Command** option.
    
31. The **Subscribe for command - TS1** popup opens. Select **On start** under the **Subscribe on** tab, type **High_Tempe** under the **Topic tab**, and select **1 Atleast once** below the **Qos** option. Click on **Save**.
    
32. Scroll down the page, you can see the **Topic** added under the **Subscribe to Commands** section.
    
33. Next, we will capture the traffic between the **virtual IoT network and the MQTT Broker** to monitor the secure communication.
    
34. Minimise the Edge browser. Click **Type here to search** field on the **Desktop**, search for **wireshark** in the search bar and select **Wireshark** from the results.
    
35. The Wireshark Application window appears, select the **Ethernet** as interface.
    
36. Click on the **Start Wireshark** icon to start the capturing packets, leave the Wireshark running.
    
37. Leave the IoT simulator running and switch to the [Windows Server 2019](https://labclient.labondemand.com/Instructions/a7ad206c-dbb0-4409-9308-112bc753c2ac#) machine.
    
38. Navigate to **Devices** menu and click on connected device i.e.**TS1**.
    
39. Now, we will send the command to **TS1** using the **High_Tempe** topic.
    
40. In **Send Command** section, select **Topic** as **High_Tempe**, type **Alert for High Temperature** in **Message** field and click on the **Submit** button.
    
41. **Message sent to TS1** appears under **Message** box which indicates that the message was successfully sent to TS1.
    
42. The message has been sent to the device using this topic.
    
43. Next, switch to Windows machine
    
44. We have left the IoT simulator running in the web browser. To see the alert message, maximise the Edge browser and expand the arrow under the connected **Temperature_Sensor**, **Device Log** section.
    
45. You can see the alert message "**Alert for High Temperature**"

    
46. To verify the communication, we have executed **Wireshark** application, switch to the Wireshark traffic capturing window.
    
47. Type **mqtt** under the **filter** field and press **Enter**. To display only the MQTT protocol packets.
    
48. Select any **Publish Message** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
    
49. Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len**, **Topic Length**, **Topic**, and **Message**.
    
50. Publish Message can be used to obtain the message sent by the MQTT client to the broker.
    
51. Select any **Publish Release** packet from the **Packet List** pane. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
    
52. Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len**, **Message Type**, **Message Identifier**.

53. Now, scroll down, look for the **Publish Complete** packet from the **Packet List** pane, and click on it. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
    
54. Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Msg Len** and **Message Identifier**.
    
55. Now, scroll down, look for the **Publish Received** packet from the **Packet List** pane, and click on it. In the **Packet Details** pane at the middle of the window, expand the **Transmission Control Protocol**, **MQ Telemetry Transport Protocol**, and **Header Flags** nodes.
    
56. Under the **MQ Telemetry Transport Protocol** nodes, you can observe details such as **Message Type**, **Msg Len** and **Message Identifier**.
    
57. Similarly you can select **Ping Request**, **Ping Response** and **Publish Ack** packets and observe the details.