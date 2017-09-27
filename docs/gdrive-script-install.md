## Google Drive Userscript Installation

This guide will walk you through the installation of a userscript necessary to play media hosted by Google Drive on newer CyTube installations. This userscript will function only if you connect to CyTube from cytu.be or www.cytu.be, connections from other URLs are not supported by this script.

### If you already know what a userscript is, you can install it from this link: 
[CyTube Google Drive Userscript](https://cytu.be/js/cytube-google-drive.user.js?v=1.1)

### Chrome

The installation of the userscript into Chrome is a three-step process:
 
1. First, in order to enable the installation of userscripts in Chrome you will need to add the userscript host extension 
[Tampermonkey](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo) from the 
[Chrome Web Store](https://chrome.google.com/webstore/category/extensions).
   
   ![Tampermonkey Extension](http://i.imgur.com/sgQfsAw.png)
   
2. Second, confirm the addition of the Tampermonkey extension into Chrome by clicking on the **Add extension** button 
in the dialog box that appears.

   ![Confirming Tampermonkey](http://i.imgur.com/zA6zzKN.png)
   
3. Finally, open the [CyTube Google Drive userscript](https://cytu.be/js/cytube-google-drive.user.js?v=1.1) link, 
which will turn the tab into an installation dialog. Here you may review the source code of the userscript. 
Once you are satisfied it does only what the developers say that it will do, click the **Install** button.

   ![Installing the userscript](http://i.imgur.com/fssRiFO.png)
   
You may now return to CyTube and resume viewing Google Drive-hosted media normally. If you haven't logged-out of CyTube, 
you will either need to logout and log back in again, or refresh the page to activate the userscript.

### Firefox

The process for the installation of the userscript into Firefox is similar to the one for Chrome:

 1. Install the [Tampermonkey](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/) userscript host add-on from 
 [addons.mozilla.org](https://addons.mozilla.org/en-US/firefox/).
 2. Open the [CyTube Google Drive userscript](https://cytu.be/js/cytube-google-drive.user.js?v=1.1) link and click the 
 **Install script** button in the dialog box to install it into Tampermonkey.

Logout and log back in to CyTube, or refresh the page to activate the userscript.

The script is also compatible with [Greasemonkey](https://addons.mozilla.org/en-Us/firefox/addon/greasemonkey/).

### Other browsers
The installation process for other browsers should work in much the same way: 
 1. Install a userscript host extension / plugin. 
 2. Install the [CyTube Google Drive userscript](https://cytu.be/js/cytube-google-drive.user.js?v=1.1) into it.

[Tampermonkey](http://tampermonkey.net/) supports most browsers.

## Troubleshooting

### Third-party cookies
In both the Chrome and the Firefox installations of the userscript, **it's important that your browser does not block 
third-party cookies**. CyTube itself does not use third-party cookies, but Google Drive requires them to be enabled in 
order to function.  

#### Chrome
In Chrome, the setting for third-party cookies is found from entering **chrome://settings/content/cookies** into the omnibox. Either the switch for **Block third-party cookies and site data** should be toggled off, or an exception for **cytu.be** should be made by 
clicking on the **Manage exceptions...** button.

![](https://i.imgur.com/pRGXM9C.png)

#### Firefox
In Firefox, the third-party cookies setting is found from entering **about:preferences#privacy**
into the omnibox. It's shown only if Firefox uses custom settings for the History and the checkbox for 
**Always use private browsing mode** is unchecked. The **Accept cookies from sites** checkbox should be checked 
and **Accept third-party cookies** should be set to **Always**, or an exception should be made for **cytu.be** by 
clicking on the **Exceptions...** button.

![](http://i.imgur.com/RQtbCnX.png)

### AdBlock and Privacy Badger
Other extensions such as AdBlock and Privacy Badger may also block the necessary trackers for Google Drive media playback 
on CyTube, even if third-party cookies are not blocked. Disabling the AdBlock or Privacy Badger extensions while on 
the CyTube site should fix this problem. CyTube does not show ads or use invasive tracking content, but Google Drive
may have issues with it.

[Return to the top of this page](#google-drive-userscript-installation)  
[Back to the CyTube 3.0 User Guide](index.md)
