

to the Parrot Security machine.

to run the programs as a root user (When prompted, enter the password toor).

Now, run cd PhoneSploit-Pro command to navigate to the PhoneSploit-Pro folder.

Now, execute python3 phonesploitpro.py command to run the tool.

When prompted to Do you still want to continue to PhoneSploit Pro?, type Y and press Enter.

The PhoneSploit Pro main menu options appear, as shown in the screenshot.

Type 1 and press Enter to select 1. Connect a Device option.

When prompted to Enter a phones ip address, type the target Android device's IP address (in this case, 10.) and press Enter. If you are getting Connection timed out error, then type 1 again and press Enter. If you do not get any option, then type 1 and press Enter again, until you get Enter a phones ip address option.

You will see that the target Android device (in this case, 10.) is connected through port number 5555. If you are unable to establish a connection with the target device, then press Ctrl+C and re-perform 7-9.

At the Main Menu prompt, type 6 and press Enter to choose Get Screenshot.

When prompted to Enter location to save all screenshots, Press Enter for default, type /home/attacker/Desktop as the location and press Enter. The screenshot of the target mobile device will be saved in the given location.

 When prompted Do you want to Open the file?, type Y and press Enter. This will open the screenshot as shown below.

Close the Screenshot window and switch back to the Terminal window.

At the Main Menu prompt, type 13 and press Enter to choose List Installed Apps.

Type 2 and press Enter to List all packages.

The result appears, displaying the installed apps on the target Android device, as shown in the screenshot.

Now, at the Main Menu prompt, type 10 and press Enter to choose Run an app. In this example, we will launch a calculator app on the target Android device.

Type 2 and press Enter to Enter Package Name Manually.

To launch the calculator app, type com.android.calculator2 and press Enter.

After launching the calculator app on the target Android device, click [Android](https://labclient.labondemand.com/Instructions/b36d2ee1-564f-4be0-9df6-ac825c55faf4#) to switch to the Android machine.

 You will see that the calculator app is running, as shown in the screenshot.

switch back to the Parrot Security machine.

Now, at the Main Menu prompt, type 14 and press Enter to choose Access Device Shell.

You can observe that a shell command line appears, as shown in the screenshot.

In the shell command line, type pwd and press Enter to view the present working directory on the target Android device.

In the results, you can observe that the pwd is the root directory.

Now, type ls and press Enter to view all the files present in the root directory.

 Type cd sdcard and press Enter to navigate to the sdcard folder.

 Type ls and press Enter to list all the available files and folders.

Type cd Download and press Enter to navigate to the Download folder.

Type ls and press Enter to list all the available files in the folder. In this case, we are interested in the images.jpeg file, which we downloaded earlier.

Type exit and press Enter to exit the shell command line and return to the main menu.

In the Terminal window, type N and press Enter to navigate to additional PhoneSploit-Pro options on the Next Page.

The result appears, displaying additional PhoneSploit Pro options, as shown in the screenshot.

At the Main Menu prompt, type 23 and press Enter to choose Open a Link on Device.

When prompted to Enter URL, type the desired URL (in this case, https://pranx.com/hacker/) and press Enter.

switch to Android machine. Here, you can see that the link has been opened automatically.

switch back to the Parrot Security machine.

Now, at the Main Menu prompt, type 27 and press Enter to choose the Get Device Information option.

The result appears, displaying device information of the target Android device, as shown in the screenshot.

In the same way, you can exploit the target Android device further by choosing other PhoneSploit-Pro options such as Install an APK, Screen record a phone, Lock the Device, and Uninstall an App.