### Restricting New Accounts from Chat
With the rising availability and popularity of VPNs and proxies, dedicated
trolls may often come back again and again with a new proxy after being IP
banned and continue spamming.  In order to combat this, a new feature has been
added to make it more difficult to rejoin quickly and continue spamming. Channel
moderators now have the ability to configure 2 different settings, which are accessed from the 
**Channel Settings** button at the top of the page on the **General Settings** tab.
* **Delay before new accounts can chat:**  
How long an account must be active before the user can send any chat message. Setting it to `00:00` disables this restriction.
* **Delay before new accounts can post links in chat:**  
How long an account must be active before the user can send a chat message containing a URL. Setting it to `00:00` disables this restriction.  
    
This restriction applies to both chat messages sent to the channel as well as private
messages. By default, accounts must be at least 10 minutes old to chat, and 1 hour old to send links
in chat. The age of an account is determined below.  
* If the user is logged in as a registered account, the registration time of 
     the account is used.  
* Otherwise, the timestamp of the session cookie is used.
     
The session cookie is set whenever a user first joins a channel, and is reset
whenever the user's IP address changes.  Different browsers will have unique
session cookies.
