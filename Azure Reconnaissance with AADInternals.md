
1. Click Windows machine.
    
2. Navigate to GitHub Tools and copy **AADInternals** folder and paste it on **Desktop**.
    
3. In the Windows search type **powershell** and under **PowerShell** click on **Run as Administrator** to open an administrator PowerShell window.
    
4. In the PowerShell window run **cd C:\Users\Admin\Desktop\AADInternals** command to navigate to **AADInternals** folder.
    
5. In the PowerShell window run **Install-Module AADInternals** command to install AADInternals module. In the **Do you want PowerShellGet to install and import the NuGet provider now?** Question type **Y** and press **Enter**. In the Are you sure you want to install the modules from "PSGallery"? question type **A** and press **Enter**

6. Now, run **Import-Module AADInternals** command, to import **AADInternals** module.
    
7. Now, we will gather the publicly available information of a target Azure AD such as Tenant brand, Tenant name, Tenant ID along with the names of the verified domains.
    
8. In the PowerShell window run **Invoke-AADIntReconAsOutsider -DomainName company.com | Format-table** command.
    
9. From the above screenshot we can gather information such as **DNS**, **MX**, **SPF**, **DMARC**, **DKIM** etc.
    
10. Now, we will perform user enumeration in Azure AD, in the PowerShell window type **Invoke-AADIntUserEnumerationAsOutsider -UserName user@company.com** and press **Enter**.
    
11. We can see that the result appears, **True** under **Exists** field which implies that the Azure account with the given username exists and the attacker can perform further attacks.
    
12. We can also perform the user enumeration by placing the usernames in a text file, by running **Get-Content .\users.txt | Invoke-AADIntUserEnumerationAsOutsider -Method Normal**. Where the users.txt file contains the target email addresses.
    
13. Now, to get login information for a domain type **Get-AADIntLoginInformation -Domain company.com** and press **Enter**.
    
14. Now, to get login information for a user type **Get-AADIntLoginInformation -Domain user@company** and press **Enter**.
    
15. To get the tenant ID for the given user, domain, or Access Token, type **Get-AADIntTenantID -Domain company.com**.
    
16. To get registered domains from the tenant of the given domain **Get-AADIntTenantDomains -Domain company.com**
    
17. We can see that all the domains associated with the tenant will be listed.
    
18. Alternatively you can visit **https://aadinternals.com/osint/** site and type the tenant ID, domain name, or email to get the openly available information for the given tenant.
    
19. Launch Firefox browser and go to **https://aadinternals.com/osint/** and type the **domain name** in the search box and click on **Get information** button.
    
20. We will get the Domain information and the list of domains connected with the provided domain name.
    
21. In similar way you can enter the tenant ID and email in the search field to view the information regarding the tenant and the user.