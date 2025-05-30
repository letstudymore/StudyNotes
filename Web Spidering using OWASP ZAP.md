

In the Parrot  machine, open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

Now, run cd command to jump to the root directory.

 In the Terminal window, type zaproxy and press Enter to launch OWASP ZAP.

The OWASP ZAP initializing window appears; wait for it to complete.

After completing initialization, a prompt that reads Do you want to persist the ZAP Session? appears; select the No, I do not want to persist this session at this moment in time radio button and click Start.

The OWASP ZAP main window appears. Under the Quick Start tab, click the Automated Scan option under Welcome to OWASP ZAP.

The Automated Scan wizard appears; enter the target website under the URL to attack field (here, www.moviescope.com). Leave the other settings to default and click the Attack button.

OWASP ZAP starts scanning the target website. You can observe various URLs under the Spider tab.

After performing web spidering, OWASP ZAP performs active scanning. Navigate to the Active Scan tab to observe the various scanned links.

After completing the active scan, the results appear under the Alerts tab, displaying the various vulnerabilities and issues associated with the target website, as shown in the screenshot.

Now, click on the Spider tab from the lower section of the window to view the web spidering information. By default, the URLs tab appears under the Spider tab.

The URLs tab contains various links for hidden content and functionality associated with the target website (www.moviescope.com).

Now, navigate to the Messages tab under the Spider tab to view more detailed information regarding the URLs obtained while performing the web spidering, as shown in the screenshot.

 This concludes the demonstration of how to perform web spidering on a target website using OWASP ZAP.