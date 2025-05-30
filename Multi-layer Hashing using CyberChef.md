
CyberChef - https://gchq.github.io/CyberChef/


1. switch to the Windows 11 machine.**

2. Navigate to Desktop, right-click on the Desktop window, and navigate to New --> Text Document to create a new text file. A newly created text file appears; rename it to Secret.txt and open it. Write some text in it  and press Ctrl+S to save the file. Close the text file.

3. Launch any web browser, and go to https://gchq.github.io/CyberChef/ (here, we are using Mozilla Firefox).**

4. CyberChef website appears, click on Open file as input button present at the top of the Input section.

5. File Upload window appears, select Secret.txt file from Desktop and click Open.

6. The contents of the Secret.txt file will be displayed in the Input window.

7. Now, we will calculate MD5 hash of the Secret.txt file, to do so, in the search field present under Operations section, type md5 and drag MD5 from the results in the Operations section in to the Recipe section.

8. The tool calculates the MD5 hash of the given input file and displays the output in the Output section.

9. Now, we will compute SHA1 hash of the output. To do so, search for sha1 and drag SHA1 from the Operations section to Recipe section ensure the number of rounds is 80.

10. The Output section displays the computed SHA1 hash of the MD5 value.

11. Now, we will add HMAC as another layer of hash, search for hmac and drag HMAC from Operations section to Recipe section.

12. In HMAC Recipe, enter the key as 12 and select the Hashing function as MD5 from the drop-down.

13. The Output section displays the HMAC hash of the SHA1 hash.

14. In addition, we can set break point to the hash operation by clicking on the Set breakpoint button present in the Recipe.

15. We can also disable a hash operation by clicking the Disable Operation button present in the Recipie.