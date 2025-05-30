
switch to the Parrot Security machine. use a sample password file (passwords.txt) containing a list of passwords to crack the FTP credentials on the target machine

Assume that you are an attacker, and you have observed that the FTP service is running on the Windows 11 machine.

Perform an Nmap scan on the target machine (Windows 11) to check if the FTP port is open.

In the Parrot Security machine, open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

In the terminal window, run nmap -p 21 IP Address .

Observe that port 21 is open in Windows .

Check if an FTP server is hosted on the Windows 11 machine.

Run ftp IP Address . You will be prompted to enter user credentials. The need for credentials implies that an FTP server is hosted on the machine.

Try entering random usernames and passwords in an attempt to gain FTP access.

As shown in the screenshot, you will not be able to log in to the FTP server. Close the terminal window.

Now, to attempt to gain access to the FTP server, perform a dictionary attack using the THC Hydra tool.

Click Places from the top-section of the Desktop and click Desktop from the drop-down options.

Copy Wordlists folder.

Paste the copied folder (Wordlists) on the Desktop. Close the window

In the Parrot  machine, open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

In the terminal window, run hydra -L Wordlists/Usernames.txt -P /Wordlists/Passwords.txt ftp://IP.

Hydra tries various combinations of usernames and passwords (present in the Usernames.txt and Passwords.txt files) on the FTP server and outputs cracked usernames and passwords.

On completion of the password cracking, the cracked credentials appear, as shown in the screenshot.

Try to log in to the FTP server using one of the cracked username and password combinations. In this lab, use Martin's credentials to gain access to the server.

In the terminal window, run ftp [IP Address of Windows 11].

Enter Martin's user credentials (Martin and apple) to check whether you can successfully log in to the server.

On entering the credentials, you will successfully be able to log in to the server. An ftp terminal appears, as shown in the screenshot.

Now, you can remotely access the FTP server hosted on the Windows 11 machine.

Run mkdir Hacked to remotely create a directory named Hacked on the Windows 11 machine through the ftp terminal.

to switch to the Windows 11 machine and navigate to C:\FTP.

View the directory named Hacked, as shown in the screenshot:

You have successfully gained remote access to the FTP server by obtaining the appropriate credentials.

to switch back to the Parrot machine.

Enter help to view all other commands that you can use through the FTP terminal.

On completing the task, enter quit to exit the ftp terminal.