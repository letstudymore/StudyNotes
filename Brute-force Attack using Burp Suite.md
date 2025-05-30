
switch to the Parrot  machine.

Launch the Mozilla Firefox web browser and go to the  site URL

Now, we shall set up a Burp Suite proxy by first configuring the proxy settings of the browser.

 In the Mozilla Firefox browser, click the Open application menu icon in the right corner of the menu bar and select Settings from the drop-down list.

The General settings tab appears. In the Find in Settings search bar, search for proxy and in the Search Results, click the Settings button under the Network Settings option.

 The Connection Settings window appears; select the Manual proxy configuration radio button and specify the HTTP Proxy as 127.0.0.1 and the Port as 8080. Tick the Also use this proxy for HTTPS checkbox and click OK. Close the Settings tab and minimize the browser window.

Now, minimize the browser window, click the Applications menu form the top left corner of Desktop, and navigate to Pentesting --> Web Application Analysis --> Web Application Proxies --> Burpsuite CE to launch the Burpsuite CE application.

The Burp Suite Community Edition pop-up appears, click OK.

In the Terms and Conditions wizard, click the I Accept button.

The Burp Suite main window appears; ensure that the Temporary project radio button is selected and click the Next button, as shown in the screenshot

In the next window, select the Use Burp defaults radio-button and click the Start Burp button.

The Burp Suite main window appears; click the Proxy tab from the available options in the top section of the window.

In the Proxy settings, by default, the Intercept tab opens-up. Observe that by default, the interception is active as the button says Intercept is on. Leave it running.

Switch back to the browser window. On the login page of the target WordPress website, type random credentials, here admin and password. Click the Log In button.

Switch back to the Burp Suite window; observe that the HTTP request was intercepted by the application.

Now, right-click anywhere on the HTTP request window, and from the context menu, click Send to Intruder.

Now, click on the Intruder tab from the toolbar and observe that under the Intruder tab, the Positions tab appears by default.

In the Positions tab under the Intruder tab observe that Burp Suite sets the target positions by default, as shown in the HTTP request. Click the Clear § button from the right-pane to clear the default payload values.

Once you clear the default payload values, select Cluster bomb from the Attack type drop-down list.

Now, we will set the username and password as the payload values. To do so, select the username value entered in Step#14 and click Add § from the right-pane. Similarly, select the password value entered in Step#14 and click Add § from the right-pane.

Once the username and password payloads are added. The symbol '§' will be added at the start and end of the selected payload values. Here, as the screenshot shows, the values are admin and password.

Navigate to the Payloads tab under the Intruder tab and ensure that under the Payload Sets section, the Payload set is selected as 1, and the Payload type is selected as Simple list.

Under the Payload settings [Simple list] section, click the Load… button.

A file selection window appears; navigate to the location /home/attacker/Desktop/Hacking Web Applications/Wordlist, select the username.txt file, and click the Open button.

Observe that the selected username.txt file content appears under the Payload settings [Simple list] section, as shown in the screenshot.

Similarly, load a password file for the payload set 2. To do so, under the Payload Sets section, select the Payload set as 2 from the drop-down options and ensure that the Payload type is selected as Simple list.

Under the Payload settings [Simple list] section, click the Load… button.

A file selection window appears; navigate to the location /Wordlist, select the password.txt file, and click the Open button.

Observe that selected password.txt file content appears under the Payload settings [Simple list] section, as shown in the screenshot.

Once the wordlist files are selected as payload values, click the Start attack button to launch the attack.

A Burp Intruder notification appears. Click OK to proceed.
    
The Intruder attack of 10. window appears as the brute-attack initializes. It displays various username-password combinations along with the Length of the response and the Status.

Wait for the progress bar at the bottom of the window to complete.

After the progress bar completes, scroll down and observe the different values of Status and Length. Here, Status=302 and Length= 1155.

In the Raw tab under the Request tab, the HTTP request with a set of the correct credentials is displayed. (here, username=), as shown in the screenshot. Note down these user credentials.

Now, that you have obtained the correct user credentials, close the Intruder attack of 10.10.1.22 window.

Navigate back to the Proxy tab and click the Intercept is on button to turn off the interception. The Intercept is on button toggles to Intercept is off, indicating that the interception is off.

Switch to the browser window and perform Step#4-5. Remove the browser proxy set up in Step#6, by selecting the No proxy radio-button in the Connection Settings window and click OK. Close the tab.

Reload the target website http://10.10.1.22:8080/CEH/wp-login.php?, enter the Username and Password obtained in Step#35 and click Log In.

You are successfully logged in using the brute-forced credentials. The Welcome to WordPress! Page appears, as shown in the screenshot.