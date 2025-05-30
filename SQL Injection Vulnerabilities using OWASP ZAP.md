

1.  switch to the **Windows  2019** machine.
    
2. Click windows **Search** icon, search for **Zap 2.14.0** in the search bar and launch **ZAP**.
    
3. OWASP ZAP initialized and a prompt that reads **Do you want to persist the ZAP Session?** appears; select the **No, I do not want to persist this session at this moment in time** radio button, and click **Start**.
    
4. The **OWASP ZAP** main window appears; under the **Quick Start** tab, click the **Automated Scan** option.
    
5. The **Automated Scan** wizard appears, enter the target website in the **URL to attack** field (in this case, **http://www.moviescope.com**). Leave other options set to default, and then click the **Attack** button.
    
6. **OWASP ZAP** starts performing **Active Scan** on the target website, as shown in the screenshot.
    
7. After the scan completes, **Alerts** tab appears. You can observe the vulnerabilities found on the website under the **Alerts** tab.
    
8. Now, expand the **SQL Injection** vulnerability node under the **Alerts** tab.
    
9. Click on the discovered **SQL Injection** vulnerability and further click on the vulnerable URL.
    
10. You can observe the information such as **Risk**, **Confidence**, **Parameter**, **Attack**, etc., regarding the discovered SQL Injection vulnerability in the lower right-bottom, as shown in the screenshot.
    
    - **Red Flag**: High risk
    - **Orange Flag**: Medium risk
    - **Yellow Flag**: Low risk
    - **Blue Flag**: Provides details about information disclosure vulnerabilities

11. Similarly, expand any other vulnerability (here, **SQL Injection-MsSQL**) node under the **Alerts** tab and further click on the vulnerable URLs
    
12. This concludes the demonstration of how to detect SQL injection vulnerabilities using OWASP ZAP.
    
13. Close all open windows and document all the acquired information.
    

Tools such as **Damn Small SQLi Scanner** (**DSSS**) (https://github.com), Snort (https://snort.org), **Burp Suite** (https://www.portswigger.net), **HCL AppScan** (https://www. hcl-software.com) etc. to detect SQL injection vulnerabilities.