
## NetBIOS Enumeration using Windows Command-Line Utilities

Open a Command Prompt window and run nbtstat -a [IP address of the remote machine] command (here, the target IP address is 10.10.1.11)

In this command, -a displays the NetBIOS name table of a remote computer.

Now, run net use command. The output displays information about the target such as connection status

Name the shared folder/drive available on the Windows Server 2019 machine.
\\windows11\CEH-Tools

