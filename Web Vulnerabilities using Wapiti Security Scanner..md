

switch to the Parrot Security machine. Open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

In the terminal window run cd wapiti command to navigate into wapiti directory and run python3 -m venv wapiti3 command to create virtual environment in python.

Now, run . wapiti3/bin/activate command to activate virtual environment.

Run pip install . command to install wapiti web application security scanner.

After installing the tool run wapiti -u https://www.certifiedhacker.com command to perform web application security scanning on certifiedhacker.com website.

Now, in the terminal run cd /root/.wapiti/generated_report/ to navigate to generated_report directory.

Run ls command to view the contents of the directory. we can see that the certifiedhacker.com_xxxxxxxx_xxxx.html file is created.

Run cp certifiedhacker.com_xxxxxxxx_xxxx.html /home/attacker/ command to copy the .html file to /home/attacker location.

 Open a new terminal and run firefox certifiedhacker.com_xxxxxxxx_xxxx.html command to open the .html file in Firefox browser.

Wapiti scan report opens upp in Firefox browser, you can analyze the scan result with the discovered vulnerabilities.

Scroll down to view the detailed information regarding each discovered vulnerability.

 This concludes the demonstration of discovering vulnerabilities in a target website scanning using wapiti.