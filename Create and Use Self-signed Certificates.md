
Here, we will create a self-signed certificate in Windows  2019.

1. switch to the Windows  2019.

2. Before you start this task, you will need to check with your local sites whether they include a self-signed certificate.

3. Launch any web browser, and go to https://www.goodshopping.com (here, we are using Mozilla Firefox).**

4. As you are using an https channel to browse the website, it displays a page stating that Unable to connect.

5. As the site does not have a self-signed certificate, it displays a error message, as shown in the screenshot. Close the web browser.

6. Click the Type here to search icon present in the bottom-left of Desktop and type iis. Select Internet Information Services (IIS) Manager from the results.

7. The Internet Information Services (IIS) Manager window appears; click the machine name (SERVER2019 (SERVER2019\Administrator)) under the Connections section from the left-hand pane.

8. In SERVER2019 Home, double-click Server Certificates in the IIS section.

9. The Server Certificates wizard appears; click Create Self-Signed Certificate… from the right-hand pane in the Actions section.

10. The Create Self-Signed Certificate window appears; type GoodShopping in the Specify a friendly name for the certificate field. Ensure that the Personal option is selected in the Select a certificate store for the new certificate field; then, click OK.

11. A newly created self-signed certificate will be displayed in the Server Certificates pane, as shown in the screenshot.

12. Expand the Sites node from the left-hand pane, and select GoodShopping from the available sites. Click Bindings… from the right-hand pane in the Actions section.

13. The Site Bindings window appears; click Add….

14. The Add Site Binding window appears; choose https from the Type field drop-down list. Once you choose the https type, the port number in the Port field automatically changes to 443 (the channel on which HTTPS runs).

15. Choose the IP address on which the site is hosted (here, 10.10.1.19).

16. Under the Host name field, type www.goodshopping.com. Under the SSL certificate field, select GoodShopping from the drop-down list, and click OK.**

17. The newly created SSL certificate is added to the Site Bindings window; then, click Close.

18. Now, right-click the name of the site for which you have created the self-signed certificate (here, GoodShopping) and click Refresh from the context menu.

19. Minimize the Internet Information Services (IIS) Manager window.

20. Open the Mozilla Firefox browser and go to https://www.goodshopping.com.**

21. The Warning:Potential Security Risk Ahead message appears, click Advanced… to proceed.

22. Click Accept the Risk and Continue.

23. Now you can see Goodshopping webpage with ssl certificate assigned to it, as shown in the screenshot.