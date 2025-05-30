
**Footprinting a Target using Recon-ng**


1. In the Parrot ** machine, open a **Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

2. Now, run cd command to jump to the root directory and run recon-ng command to launch the application.

3. Run help command to view all the commands that allow you to add/delete records to a database, query a database, etc.

4. Run marketplace install all command to install all the modules available in recon-ng.

5. After the installation of modules, run modules search command. This displays all the modules available in recon-ng.

6. You will be able to perform network discovery, exploitation, reconnaissance, etc. by loading the required modules.

7. Run workspaces command to view the commands related to the workspaces.

8. Create a workspace in which to perform network reconnaissance. In this task, we shall be creating a workspace named CEH.

9. To create the workspace, run workspaces create CEH command. This creates a workspace named CEH.
 
10. Enter workspaces list. This displays a list of workspaces (along with the workspace added in the previous step) that are present within the workspaces databases.
  
11. Add a domain in which you want to perform network reconnaissance.

12. Issue the command db insert domains.

13. Under domain (TEXT) option type certifiedhacker.com and press Enter. In the notes (TEXT) option press Enter. This adds certifiedhacker.com to the present workspace.

14. You can view the added domain by issuing the show domains command, as shown in the screenshot.

15. Harvest the hosts-related information associated with certifiedhacker.com by loading network reconnaissance modules such as brute_hosts, Netcraft, and Bing.
    
16. Issue modules load brute command to view all the modules related to brute forcing. In this task, we will be using the recon/domains-hosts/brute_hosts module to harvest hosts.

17. To load the recon/domains-hosts/brute_hosts module, issue modules load recon/domains-hosts/brute_hosts command.

18. Issue run command. This begins to harvest the hosts, as shown in the screenshot.

19. Observe that hosts have been added by running the recon/domains-hosts/brute_hosts module.

20. You have now harvested the hosts related to certifiedhacker.com using the brute_hosts module. You can use other modules such as Netcraft and Bing to harvest more hosts. Use the back command to go back to the CEH attributes terminal. To resolve hosts using the Bing module, use the following commands: - back / - modules load recon/domains-hosts/bing_domain_web - run

21. Now, perform a reverse lookup for each IP address (the IP address that is obtained during the reconnaissance process) to resolve to respective hostnames.

22. Execute modules load reverse_resolve command to view all the modules associated with the reverse_resolve keyword. In this task, we will be using the recon/hosts-hosts/reverse_resolve module.

23. Run the modules load recon/hosts-hosts/reverse_resolve command to load the module.

24. Issue the run command to begin the reverse lookup.
  
25. Once done with the reverse lookup process, run the show hosts command. This displays all the hosts that are harvested so far, as shown in the screenshot.
 
26. Now, use the back command to go back to the CEH attributes terminal.

27. Now, that you have harvested several hosts, we will prepare a report containing all the hosts.

28. Execute modules load reporting command to view all the modules associated with the reporting keyword. In this lab, we will save the report in HTML format. So, the module used is reporting/html.

29. Run the modules load reporting/html command.

30. Observe that you need to assign values for CREATOR and CUSTOMER options while the FILENAME value is already set, and you may change the value if required. To do so, run the below commands:
- options set FILENAME /home/attacker/Desktop/results.html. By issuing this command, you are setting the report name as results.html and the path to store the file as Desktop.
- options set CREATOR [your name] (here, Jason).
- options set CUSTOMER Certifiedhacker Networks (since you have performed network reconnaissance on certifiedhacker.com domain).

24. Use the run command and press Enter to create a report for all the hosts that have been harvested.

25. The generated report is saved to /home/attacker/Desktop/.

26. Navigate to /home/attacker/Desktop/, right-click on the results.html file, click on Open With, and select the Firefox ESR Web Browser browser from the available options.

27. The generated report appears in the Firefox browser, displaying the summary of the harvested hosts.

28. You can expand the Hosts node to view all the harvested hosts, as shown in the screenshot.
   
29. Close all open windows.

30. Until now, we have used the Recon-ng tool to perform network reconnaissance on a target domain

31. Now, we will use Recon-ng to gather personnel information.

32. Open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

33. Run cd command to jump to the root directory and run recon-ng command.

34. Add a workspace by issuing the command workspaces create reconnaissance and press Enter. This creates a workspace named reconnaissance.

35. Set a domain and perform footprinting on it to extract contacts available in the domain.

36. Execute modules load recon/domains-contacts/whois_pocs command. This module uses the ARIN Whois RWS to harvest POC data from Whois queries for the given domain.

37. Run the info command command to view the options required to run this module.

38. Run options set SOURCE facebook.com command to add facebook.com as a target domain.

39. Execute the run command. The recon/domains-contacts/whois_pocs module extracts the contacts associated with the domain and displays them, as shown in the screenshot

40. Until now, we have obtained contacts related to the domains. Note down these contacts’ names. Close all the open windows.

41. Now, we will use Recon-ng to extract a list of subdomains and IP addresses associated with the target URL.

42. Open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

43. Now, run cd command to jump to the root directory and run recon-ng command.

44. To extract a list of subdomains and IP addresses associated with the target URL, we need to load the recon/domains-hosts/hackertarget module.

45. Run the modules load recon/domains-hosts/hackertarget command and run options set SOURCE certifiedhacker.com command.

46. Execute the run command. The recon/domains-hosts/hackertarget module searches for list of subdomains and IP addresses associated with the target URL and returns the list of subdomains and their IP addresses.

47. This concludes the demonstration of gathering host information of the target domain and gathering personnel information of a target organization.