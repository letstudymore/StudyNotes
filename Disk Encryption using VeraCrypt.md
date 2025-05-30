
1.  Windows 11 machine.

2. Click Search icon on the Desktop, search for vera in the search field, the VeraCrypt appears in the results, click Open to launch it.

3. The VeraCrypt main window appears; click the Create Volume button.

4. The VeraCrypt Volume Creation Wizard window appears. Ensure that the Create an encrypted file container radio-button is selected and click Next to proceed.

5. In the Volume Type wizard, keep the default settings and click Next.

6. In the Volume Location wizard, click Select File….

7. The Specify Path and File Name window appears; navigate to the desired location (here, Desktop), provide the File name as MyVolume, and click Save.

8. After saving the file, the location of a file containing the VeraCrypt volume appears under the Volume Location field; then, click Next.

9. In the Encryption Options wizard, keep the default settings and click Next.

10. In the Volume Size wizard, ensure that the MB radio-button is selected and specify the size of the VeraCrypt container as 5; then, click Next.

11. The Volume Password wizard appears; provide a strong password in the Password field, retype in the Confirm field, and click Next. The password provided in this lab is qwerty@123.

12. The Volume Format wizard appears; ensure that FAT is selected in the Filesystem option and Default is selected in Cluster option.

13. Check the checkbox under the Random Pool, Header Key, and Master Key section.

14. Move your mouse as randomly as possible within the Volume Creation Wizard window for at least 30 seconds and click the Format button.

15. After clicking Format, VeraCrypt will create a file called MyVolume in the provided folder. This file depends on the VeraCrypt container (it will contain the encrypted VeraCrypt volume).

16. Depending on the size of the volume, volume creation may take some time.

17. Once the volume is created, a VeraCrypt Volume Creation Wizard dialog-box appears; click OK.

18. In the VeraCrypt Volume Creation Wizard window, a Volume Created message appears; then, click Exit.

19. The VeraCrypt main window appears; select a drive (here, I:) and click Select File….
    
20. The Select a VeraCrypt Volume window appears; navigate to Desktop, click MyVolume, and click Open.
    
21. The window closes, and the VeraCrypt window appears displaying the location of selected volume under the Volume field; then, click Mount.

22. The Enter password dialog-box appears; type the password you specified in Step#11 into the Password field and click OK
    
23. After the password is verified, VeraCrypt will mount the volume in I: drive, as shown in the screenshot.

24. MyVolume has successfully mounted the container as a virtual disk (I:). The virtual disk is entirely encrypted (including file names, allocation tables, free space, etc.) and behaves similarly to a real disk. You can copy or move files to this virtual disk to encrypt them.

25. Create a text file on Desktop and name it Test. Open the text file and insert text.

26. Click File in the menu bar and click Save.

27. Copy the file from Desktop and paste it into Local Disk (I:). Close the window.

28. Switch to the VeraCrypt window, click Dismount, and then click Exit.

29. The I: drive located in This PC disappears.