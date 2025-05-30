
## Clear Windows Machine Logs using Various Utilities

**Windows 11** machine, navigate to **E:\CEH-Tools\CEHv13 Module 06 System Hacking\Covering Tracks Tools\Clear_Event_Viewer_Logs.bat**. Right-click **Clear_Event_Viewer_Logs.bat** and click **Run as administrator**

The **User Account Control** pop-up appears; click **Yes**

A **Command Prompt** window appears, and the utility starts clearing the event logs, as shown in the screenshot. The command prompt will automatically close when finished

Clear_Event_Viewer_Logs.bat is a utility that can be used to wipe out the logs of the target system. This utility can be run through command prompt or PowerShell, and it uses a BAT file to delete security, system, and application logs on the target system. You can use this utility to wipe out logs as one method of covering your tracks on the target system.

In the Windows search type **cmd** the **Command Prompt** appears in the results, click **Run as administrator** to launch it

The **User Account Control** pop-up appears; click **Yes**

A **Command Prompt** window with **Administrator** privileges appears. Run **wevtutil el** command to display a list of event logs

**el | enum-logs** lists event log names

Now, run **wevtutil cl [log_name]** command (here, we are clearing **system** logs) to clear a specific event log
**cl | clear-log**: clears a log, **log_name** is the name of the log to clear, and ex: is the system, application, and security

Similarly, you can also clear application and security logs by issuing the same command with different log names (**application, security**)

**wevtutil** is a command-line utility used to retrieve information about event logs and publishers. You can also use this command to install and uninstall event manifests, run queries, and export, archive, and clear logs
  
In **Command Prompt**, run **cipher /w:[Drive or Folder or File Location]** command to overwrite deleted files in a specific drive, folder, or fil
Here, we are encrypting the deleted files on the **C:** drive. You can run this utility on the drive, folder, or file of your choice

The Cipher.exe utility starts overwriting the deleted files, first, with all zeroes (0x00); second, with all 255s (0xFF); and finally, with random numbers, as shown in the screenshot
Cipher.exe is an in-built Windows command-line tool that can be used to securely delete a chunk of data by overwriting it to prevent its possible recovery. This command also assists in encrypting and decrypting data in NTFS partitions

When an attacker creates a malicious text file and encrypts it, at the time of the encryption process, a backup file is created. Therefore, in cases where the encryption process is interrupted, the backup file can be used to recover the data. After the completion of the encryption process, the backup file is deleted, but this deleted file can be recovered using data recovery software and can further be used by security personnel for investigation. To avoid data recovery and to cover their tracks, attackers use the Cipher.exe tool to overwrite the deleted files

Press **ctrl+c** in the command prompt to stop the encryption

The time taken to overwrite the deleted file, folder or drive depends upon its size



## Clear Linux Machine Logs using the BASH Shell


to switch to the **Parrot Security** machine.

Open a Terminal window and run **export HISTSIZE=0** command to disable the BASH shell from saving the history.
**HISTSIZE**: determines the number of commands to be saved, which will be set to 0.

In the **Terminal** window, run **history -c** command to clear the stored history
This command is an effective alternative to the disabling history command; with **history -c**, you have the convenience of rewriting or reviewing the earlier used commands.

Similarly, you can also use the **history -w** command to delete the history of the current shell, leaving the command history of other shells unaffected

Run **shred ~/.bash_history** command to shred the history file, making its content unreadable
This command is useful in cases where an investigator locates the file; because of this command, they would be unable to read any content in the history file

Now, run **more ~/.bash_history** command to view the shredded history content, as shown in the screenshot

Type **ctrl+z** to stop viewing the shredded history content
The time taken for shredding history file depends on the size of the file

You can use all the above-mentioned commands in a single command by issuing **shred ~/.bash_history && cat /dev/null > .bash_history && history -c && exit**

This command first shreds the history file, then deletes it, and finally clears the evidence of using this command. After this command, you will exit from the terminal window



