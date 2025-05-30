
 
On the victim machine, navigate to ProcessMonitor and double-click **Procmon.exe** to launch the Process Monitor tool

The **Process Monitor License Agreement** window appears; click **Agree**.

The **Process Monitor** main window appears, as shown in the screenshot, with the processes running on the machine.

Scroll down to look for the **Trojan.exe** process that was executed in the previous task. If you killed the process at the end of the task, then navigate to njRAT** and double-click **Trojan.exe** to re-execute the malicious program.
 
Observe that the **Trojan.exe** process is running on the machine. Process Monitor shows the running process details such as the PID, Operation, Path, Result, and Details.
  
To view the properties of a running process, select the process (here, **Trojan.exe**), right-click on the process and select **Properties** from the context menu.

The **Event Properties** window appears with the details of the chosen process.

In the **Event** tab, you can see the complete details of the running process such as Date, Thread, Class, Operation, Result, Path, and Duration.

Once the analysis is complete, click the **Process** tab.

The **Process** tab shows the complete details of the process running, as shown in the screenshot
 
Click the **Stack** tab to view the supported DLLs of the selected process. Once the analysis is done, click **Close**

Use other process monitoring tools such as **Process Explorer** (https://docs.microsoft.com), **OpManager** (https://www.manageengine.com), **Monit** (https://mmonit.com), **ESET SysInspector** (https://www.eset.com), or **System Explorer** (https://systemexplorer.net) to perform process monitoring


