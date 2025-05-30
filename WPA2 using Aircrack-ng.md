
to switch to the Parrot Security machine and login with attacker/toor

Navigate to the Places in the top-section of the window and click Desktop from the drop-down list

The Desktop window appears, navigate to the Hacking Wireless Networks folder and copy Sample Captures and Wordlist folders

Now, navigate to the Desktop and press Ctrl+V to paste the copied folders (Sample Captures and Wordlist). Close the Desktop window

Open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor)

In the Parrot ** window, run aircrack-ng -a2 -b [Target BSSID] -w /home/attacker/Desktop/Wordlist/password.txt '/home/attacker/Desktop/Sample Captures/WPA2crack-01.cap'. Example of the target is 22:7F:AC:6D:E6:8B

- -a is the technique used to crack the handshake, 2=WPA technique.
- - -b refers to bssid; replace with the BSSID of the target router.
- - -w stands for wordlist; provide the path to a wordlist.

The result appears, showing the WPA handshake packet captured with airodump-ng. The target access point's password is cracked and displayed in plain text next to the message KEY FOUND!, as shown in the screenshot

If the password is complex, aircrack-ng will take a long time to crack it

Use other tools such as hashcat (https://hashcat.net), Portable Penetrator (https://www.secpoint.com), WepCrackGui (https://sourceforge.net) to crack WEP/WPA/WPA2 encryption


