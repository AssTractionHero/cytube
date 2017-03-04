### Before you proceed...
Please consider scanning the [FAQ](frequently-asked-questions.md) or the [Quick Reference](index.md) first to check if your question is answered there.

***
# Table of Contents
1. [What's New](#wiki-whats-new)
2. [Registering a New Account](#registering-a-new-account)  
      2.1. [Account Profile](#account-profile)  
      2.2. [Changing your Password or Email Address](#changing-your-password-or-email-address)  
      2.3. [Recovering an Account If You Lost The Password](#recovering-an-account-if-you-lost-the-password)  
3. [User Settings](#user-settings)  
     3.1. [General](#general)  
     3.2. [Playback](#playback)  
     3.3. [Chat](#chat)  
     3.4. [Moderator](#moderator)
4. [Channel UI](#channel-ui)  
     4.1. [Chat Box](#chat-box)  
     4.2. [Playlist Controls](#playlist-controls)  
     4.3. [Playlist](#playlist)  
     4.4. [Poll Area](#poll-area)  
     4.5. [Changing the Size of the Video Frame](#changing-the-size-of-the-video-frame)  
5. [Channel Management](#channel-management)  
     5.1. [Registering a Channel](#registering-a-channel)  
     5.2. [Deleting a Channel](#deleting-a-channel)  
     5.3. [Channel Settings](#channel-settings)  
6. [Chat Commands](#chat-commands)  
     6.1. [Standard Commands](#standard-commands)  
     6.2. [Moderator Commands](#moderator-commands)  
     6.3. [Default Formatting](#default-formatting)  
7. [Supported Media Providers](#supported-media-providers)
8. [Adding Subtitles to Google Drive Videos](#adding-subtitles-to-google-drive-videos)
9. [Userscript for Google Drive Media Playback](#userscript-for-google-drive-media-playback)
10. [Help / Support](#help--support)

***
# What's new
  * UI Changes
    * Updated bootstrap to v3.0
    * Redesigned playlist controls
    * Redesigned channel moderation settings
    * Added HD layout
    * Added Slate and Cyborg themes
    * Moved guest login form to the chat box
    * Added alias list to user profile box (for moderators)
    * Added buttons to increase / decrease the size of the video frame
  * Webserver changes
    * Changed login system
      * Allows you to be logged in from more than one device
      * Permits more secure storage of authentication data
    * Changed account management system
  * New channel features
    * Built-in emote support
    * Private messaging

# Registering a New Account
To register an account, click the **Account** dropdown on the navigation bar at the top of the page, then click **Register**. This option will appear only if you are not already logged in. When choosing a username, make sure it meets the following requirements:
* It must be 1-20 characters long.
* It may contain only the letters 'A' through 'Z' (upper or lowercase), the digits '0' through '9', hyphens '-', and underscores '_'.

Be sure to pick a strong password that is both not easily guessable and is not the same as your accounts on other websites. Entering an email address is optional, however it will allow you to recover your account if you ever forget your password.

### Account Profile
Each CyTube account can set a profile photo and short description. On the navigation bar at the top of the page click **Account**, then **Profile**. You can then enter the URL of a profile image (the URL must end in .gif, .jpg, or .png,) and enter a short text blurb that will be displayed when users hover over your name in the chat username list.  
**Important**: this is publicly visible to anyone, so don't use a private photo or include private information in your description.

### Changing your Password or Email Address
On the navigation bar at the top of the page click **Account**, then **Change Password / Email**. You must provide your current password in order to change either of these settings. You can leave the email address box blank if you wish to remove the email address from your account. (Be aware that this means you will no longer be able to receive password reset emails.)

### Recovering an Account If You Lost the Password
From the login page, click **Forgot password?** You will be prompted to enter your username and email address. The email address must match the one associated with your account. If you have not linked an email address to your account, you cannot reset your password automatically and will need to contact an administrator for help. Otherwise, you will receive an email with a link to reset your password.

# User Settings
At the top of the page, you should see a button labeled **Options**.  This will open a dialog that allows you to configure various personal settings.  These are divided into 4 categories.

## General
### Theme
The theme selector allows you to choose a different colorscheme for the site.  By default there are 4 themes.  **Slate** and **Cyborg** are both dark themes, **Light** is a flat, light colored scheme, and **Bootstrap** is the same colors as **Light** but with added gradients.

### Layout
The layout selector changes how the elements on the page are positioned and sized.  **Compact** and **Fluid** have chat on the left, video on the right, and polls and the playlist below.  **Synchtube** and **Synchtube + Fluid** are the same as **Compact** and **Fluid** except reversed -- chat is on the right with video on the left.  **Fluid** and **Synchtube + Fluid** will expand the chat and video to fill the width of your screen, whereas **Compact** has a static size.  **HD** places video on top, then the playlist and chat side by side, then polls below chat.

### Ignore Channel CSS
CyTube includes the ability to style channels with CSS, you can use this option to override these changes and use the default CSS.

### Ignore Channel JavaScript
This is analagous to **Ignore Channel CSS**.  If enabled, it will not run any custom JavaScript from the channel.  This is useful for recovering your channel if you make a mistake in your JavaScript that makes it impossible to revert.

## Playback
### Synchronize video playback
This checkbox controls whether or not your video will be synchronized with the server.

### Synch threshold
This is the number of seconds representing how close your video will be synchronized with the server.  For example, with the default value (2), your video will be forced to re-sync only if it is at least 2 seconds ahead or behind the server.  Smaller values indicate more accurate synchronization, but may cause interruptions in the video due to inadequate buffering.  If you're having trouble with a slow connection, you may want to increase this setting to 5 or 10 seconds.

### Set wmode=transparent
The `wmode=transparent` parameter on the video player allows elements to be rendered over the video like normal.  However, on some implementations of Flash (e.g. Linux,) this is extremely laggy, so I added this option to force an opaque `wmode`.

### Remove the video player
This option will automatically remove the video player every time you load a channel.  It's useful if you're using CyTube on a computer or in a location where you don't want the video present.  You can do a one-time removal of the video by clicking on **Layout** then **Remove Video** from the navigation bar at the top of the page.

### Hide playlist buttons by default
Instead of **Play** / **Queue Next** / **Make Temporary** / **Delete** buttons being visible on every playlist item, they will start out hidden.  You can then right-click a playlist item to expand the buttons, and right-click it again to hide them.

### Old style playlist buttons
This is a legacy feature for people who prefer the icon-style playlist buttons from CyTube 1.0.

### Quality Preference
This dropdown allows you to select the quality parameter passed to the player when it loads a video.

## Chat
### Show timestamps in chat
If enabled, prepends a timestamp of the form [HH:MM:SS] to the beginning of each chat message with the time it was sent.

### Sort userlist by rank
If enabled, all admins will be sorted to the top of the userlist, followed in order by moderators, registered users, and guests.  Within each rank group, names are sorted in alphabetical order.

### Sort AFKers to bottom
If enabled, users marked as AFK will appear at the bottom of the userlist.

### Blink page title on new messages
This option controls whether the page title will flash (alternate between channel title and `*Chat*`) when certain conditions occur.  If set to **Always** it will flash on every new message.  If set to **Only when I am mentioned or PMed** it will only flash if your name is present in the message, or the message is a PM.  If set to **Never** the page title will not be flashed for any message.  Please note this applies only when CyTube is not the active window.

### Notification sound on new messages
Same as above, but plays a notification sound instead of flashing the page title.

### Add a send button to chat
This adds an extra button below the chat box you can click to send a message.  This is for devices with soft keyboards that don't have an enter key (because apparently those exist?)

### Tab Completion method
This selects how tab completion behaves when used to autocomplete a string in chat with the `Tab` key, such as a username or emote tag. You can set it to cycle through all matches, or use the longest unique match that is found. 

## Moderator
### Show name color
Colors your username when you send a chat message, based on your rank.  

### Show join messages
Shows a notification in chat whenever a user joins the channel.  

### Show shadowmuted messages
If this option is checked, the chat of shadowmuted users is visible, subdued and with a strikethrough, to moderator rank (rank 2) and above.

# Channel UI
Each channel page consists of several basic sections: the chat box, the video port, the playlist controls, the playlist, and the poll area.

### Chat box
The chat box allows you to communicate with the other users in the channel.  At the top, there is a bar with the number of connected users.  Clicking this will hide the userlist to expand the message area.

The userlist consists of all the names of users in the channel who are logged in.  Right-click on a name to see a pop up with available actions for that user.  If you are not a moderator, you can choose only either to ignore the user or send them a private message.  Moderators can use this menu to kick, ban, and perform other moderating tasks.

At the bottom, there is a chat input bar.  If you are not logged in, it will prompt you to choose a guest name. If you do not choose a name, after a short period one will be chosen for you. After logging in, simply type your message in the input box and press enter to send it.  Certain types of messages will be interpreted as commands, which will be covered below in [Chat Commands](#wiki-chat-commands).

### Playlist controls
Below the video port, there are 2 strips of buttons for playlist and video control.  Depending on your permission level, certain buttons may be disabled.  Hover over each button to see what it does.

On the left are playlist controls:  

     Control name | Description
------------------|------------  
Search for a video: | Search for a video title in the channel library or on YouTube.
Add from URL: | Paste a supported media link and add it to the playlist.
Embed a custom frame: | Embed an `<iframe>` or `<object>` tag for media that is not officially supported.
Manage playlists: | Save and load playlists from your user account. Playlists are attached to your username, and not to the channel name.
Clear playlist: | Remove all videos from the playlist.
Shuffle playlist: | Randomize the order of the playlist and start playing from the top.
Lock / Unlock playlist: | Toggle the locked status of the playlist.  Unlocked state is useful for allowing non-moderators to add videos to the playlist.  Exact open / locked permissions can be configured under the [Channel Settings](#wiki-edit--permissions) permissions editor.

On the right are video controls:  

    Control name | Description
 ----------------|------------ 
Reload the video player: | Remove the current video and load it again. (Useful for dealing with playback issues.)
Retrieve playlist links: | Get a comma-separated list of all the videos in the playlist.
Voteskip: | Vote to skip the currently playing video.  If enough votes are counted, the next item in the playlist will immediately begin playing.

The **Retrieve playlist links** button will not function if you do not have the proper permission to use it. The **Voteskip** button will not function if Voteskip is disabled for the channel.

### Playlist
The playlist is a list of videos that will be played in order from top to bottom.  Each entry will display the title and duration of the video.  Each item has a few buttons to perform certain actions, the locations of which will depend on how your user preferences are set.  Click and drag playlist items to rearrange the order.

Item actions:  

    Action | Description
 ----------|------------
Play: | Immediately jump to this playlist item and begin playing.
Queue Next: | Move this video to the next slot after the currently playing video.
Make Temporary / Permanent: | Toggle whether this video will be automatically removed from the playlist after playing once.
Delete: | Remove this item from the playlist.

### Poll area
The poll area allows moderators to conduct polls.  When a moderator opens a poll, a poll box will be added to the poll area.  Each option in the poll has a button next to it for users to select that option.  Each IP address can vote only once, and your vote is cleared when you leave the page.

The buttons next to each option will display the number of votes for that option.  If it displays **?**, the user that opened the poll has elected to hide the results until the poll is over.  

### Changing the Size of the Video Frame

In early 2017, a feature was added that allows users to change the size of the video frame on a channel page. These buttons, **+** and **-**, located over the right side of the top of the video frame, control the size of it in relation to the chat pane. The **+** button increases the size of the video frame, **-** decreases the size.

# Channel Management
You must be logged in to your account to manage your channels.

### Registering a Channel
In the navigation bar at the top of the page click on **Account** then click on **Channels**.  In the right column, enter the desired channel name and click **Register**.  If that channel is not already registered to another account, it will be created and registered to your name.  The website administrator may limit the number of channels that can be registered to one account.

### Deleting a Channel
In the navigation bar at the top of the page click on **Account** then click on **Channels**.  The left column lists all channels registered to your name.  Click the **Delete** button to unregister a channel.  This will permanently clear all database information (ranks, library, bans,) and state information (playlist, configuration, MOTD, filters, etc.,) and is **non-reversible**.  You will be asked to confirm your deletion.  

# Channel Settings
From your channel page (/r/channelname), users with moderator or higher rank will see a **Channel Settings** button on the top navigation bar.  This opens a dialog box which allows various aspects of your channel to be managed, explained below:

## General Settings
  * **Convert URLs in chat to links**: If enabled, URLs entered into chat (e.g. http://google.com) will be converted to clickable hyperlinks.
  * **Allow voteskip**: If enabled, users may click the voteskip button to indicate a preference to skip the currently playing video.
  * **Voteskip ratio**: The proportion of votes from non-AFK users required to skip the current video.  The number of votes required is calculated as `ceil(voteskip ratio * number of non-AFK users)`.
  * **Max video length**: Specify the maximum duration of a playlist item.  Set this to `00:00:00` to allow unlimited length.
  * **Auto-AFK Delay**: After this delay (in seconds) of a user sending no chat messages and not voteskipping, the user will be automatically marked as "AFK".
  * **Throttle chat**: Enables a flood filter that will limit how quickly a user can send chat messages.
  * **# of messages allowed before throttling**: When **Throttle chat** is active, this controls the number of messages a user can send with no time delay before the flood filter engages.
  * **# of messages allowed per second**: After the threshold of the flood filter is exceeded, only this number of messages from a certain user are allowed per second.  Additional messages are ignored.  

### Restricting New Accounts from Chat
With the rising availability and popularity of VPNs and proxies, dedicated
trolls may often come back again and again with a new proxy after being IP
banned and continue spamming.  In order to combat this, a new feature has been
added to make it more difficult to rejoin quickly and continue spamming. Channel
moderators now have the ability to configure 2 different settings:

* **Delay before new accounts can chat:**  
How long an account must be active before the user can send any chat message. Setting it to `00:00` disables this restriction.
* **Delay before new accounts can post links in chat:**  
How long an account must be active before the user can send a chat message containing a URL. Setting it to `00:00` disables this restriction.  
    
This restriction applies to both chat messages sent to the channel as well as private
messages. By default, accounts must be at least 10 minutes old to chat, and 1 hour old to send links
in chat. The age of an account is determined as follows:
  * If the user is logged in as a registered account, the registration time of
    the account is used.
  * Otherwise, the timestamp of the session cookie is used.
The session cookie is set whenever a user first joins a channel, and is reset
whenever the user's IP address changes.  Different browsers will have unique
session cookies.

## Admin Settings
  * **Page title**: The title displayed on the browser window / tab.
  * **Password**: An optional password required for non-moderators to enter the room.  Leave blank to disable.
  * **External CSS**: URL to an external stylesheet to apply to the page.
  * **External Javascript**: URL to an external script to run on the page.
  * **List channel publicly**: When enabled, displays the channel name on the index page.  Only active channels (channels with at least 1 user) will be displayed.

### Edit / Chat Filters
Chat filters provide a way for specific text to be recognized and changed in chat messages.  For example, it could be used to transform profanity to strings of asterisks.  **Please do not use chat filters for image emotes.**  CyTube has an [Emotes](#edit--emotes-new-in-cytube-30) feature which is better-suited for adding emoticons. Adding them as chat filters is more difficult to manage and uses more server resources.  

### Adding a new filter
  * **Filter name**: A name to identify the filter.  For informational purposes only, but must be unique.
  * **Filter regex**: A regular expression describing the text to match.
  * **Flags**: A set of regular expression flags to apply.  `g` means to match all instances in the message (instead of just the first), `i` means to match without case sensitivity.
  * **Replacement**: The HTML that will replace the matched text.

See the MDN page for [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) for reference on Regular Expressions and flags.

### Managing existing filters
Filters will be applied in the order they are listed.  You can click and drag individual filters to rearrange them.  The **Active** checkbox allows you to easily enable / disable individual filters.  Under the **Control** column, the left button with a list icon opens an editor to change the regular expression, flags, and replacement for a filter.  The red button with a trashcan icon will delete the filter.

The **Filter Links** checkbox controls whether this filter will be applied to links in chat.  By default, this is off, to prevent filters from breaking links pasted in chat by changing them.

### Importing / Exporting filters (New in CyTube 3.0)
You can export and import your channel's filter list in order to back it up or transfer it to another channel.  Clicking **Export filter list** will populate the text area with a JSON-encoded list of filter data.  To import a filter list, paste the JSON data in the textbox and click **Import filter list**.  The import tool is very strict on format and will reject invalid filters, so please be careful to store the exported data verbatim.

### Edit / Emotes (New in CyTube 3.0)
The channel **Emotes** feature provides an easy way to replace certain words in chat with an image.  Each image will be rendered at a maximum of 200px by 200px.  If this is too large, you can use channel CSS to set the `max-width` and `max-height` properties of the `.channel-emote` CSS class, or you can scale your images before uploading them.  For example, if you want all emotes to have a maximum width and height of 70px, you would include this in your CSS:

```css
.channel-emote
{
  max-width: 70px;
  max-height: 70px;
}
```

The emote editing interface is similar to the one for chat filters, except the emote names are automatically converted from plain text to regular expressions.  Click on the text containing the image URL to change the image for an emote.

### Edit / MOTD
The MOTD is a block at the top of the page where you can display a Message of the Day to your channel, for example: a header image, rules, or important announcements.  The MOTD editor accepts HTML formatting, but will filter out any attempts to execute JavaScript.

### Edit / CSS
The CSS editor allows you to add up to 20,000 characters of inline CSS (as opposed to External CSS, which requires you to host the file elsewhere.)  Use this to apply custom styles or colors to your channel.

### Edit / JavaScript
The JavaScript editor allows you to add up to 20,000 characters of inline JavaScript (as opposed to External JavaScript, which requires you to host the file elsewhere.)  Use this to run JavaScript on your page, for example: to make layout changes to the page or add your own timer.

### Edit / Permissions
The permissions editor provides a way for you to configure what rank is required to carry out certain actions.  Each permission option has a dropdown for selecting the minimum rank required to perform that action.

Since there is sometimes some confusion over "Open Playlist" vs. "General Playlist", I'll note the difference here:  When the playlist is unlocked (the button below the video is green with a checkmark), the Open Playlist Permissions will take precedence over the same permissions under General Playlist Permissions.

### Edit / Moderators
This menu allows you to manage the moderators of the channel.  To add a new moderator, enter their username in the text field and click **+Mod** for moderator rank, **+Admin** for channel admin rank, or **+Owner** for channel owner rank.  Moderators have most channel moderation permissions (by default,) channel admins have additional permissions such as promoting users to moderators and editing certain channel settings, and channel owners are equivalent to channel admins except they can also promote and demote administrators and owners.

In the moderator list, you can use the **Edit** dropdown to change a user's rank, or remove them from the moderator list.  You may not promote or demote a user that's equal to or greater than your own rank.

### Ban list
The ban list shows a table of ban entries for the channel.  Each entry consists of a name, partially obscured IP address (or `*` if only the username was banned), the name of the moderator who added the ban, and optionally a note on why the ban was added.  Hovering over a row will reveal the ban reason.

### Log
The log allows you to see chat history as well as moderation actions, playlist changes, and other data about your channel.  Above the log text, there is a multiple select box that you can use to display only certain kinds of log data (e.g. chat, joins/quits, playlist actions, moderation actions, etc.)

# Chat Commands
### Standard Commands
  * `/me <message>` - Sends a message as an action, for example *calzoneman gets a snack*.
  * `/sp <message>` - Hides a message in a hover-to-expose spoiler box.
  * `/afk` - Toggles your AFK status.  You will automatically be unmarked as AFK after sending a chat message or voteskipping a video.

### Moderator Commands
  * `/say <message>` - Sends a message in big red text.
  * `/poll <title>,<option1>,<option2>,...` - Opens a new poll (this is from before the New Poll button was added).
  * `/hpoll <title>,<option1>,<option2>,...` - Same as above, but hides poll results.
  * `/mute <user>` - Mutes a user from sending chat messages.
  * `/smute <user>` - Shadowmutes a user.  They will still receive their own chat messages but nobody else will see them except for moderators that have "Show shadowmuted messages" enabled, and they will not appear muted except to moderators.
  * `/unmute <user>` - Unmutes a user.  This will unmute both muted and smuted users.
  * `/kick <user> [<reason>]` - Kicks a user, optionally providing a kick reason.
  * `/kickanons` - Kicks all anonymous users from the channel.
  * `/ban <user> [<reason>]` - Bans a user by name, optionally providing a ban reason.
  * `/ipban <user> [<reason>]` - Bans a user and all IP addresses they've used in the past month, optionally providing a ban reason.
  * `/ipban <user> range [<reason>]` - Bans an IP range (/24 block for IPv4 or /64 block for IPv6.)
  * `/ipban <user> wrange [<reason>]` - Bans a wider IP range (/16 block for IPv4, /48 block for IPv6.)
  * `/clear` - Clears the chat buffer.
  * `/clean <user>` - Removes all playlist entries from the given user.
  * `/cleantitle <title>` - Removes all playlist entries that match the given title.
  * `/d <message>` - Calls a drink with the given message.
  * `/d# [<message>]` - Calls # drinks, optionally with a message.  # can be positive or negative.

### Default formatting
By default, channels come with a few default chat filters that can be used for formatting:

  * `_message_` - *message*
  * `*message*` - **message**
  * `` `message` `` - `message` (monospace, code text)
  * `~~message~~` - ~~message~~

#  Supported Media Providers
See the [FAQ](frequently-asked-questions.md#which-media-providers-are-supported) for a list of supported media providers.

# Adding Subtitles to Google Drive Videos
1. Upload your video to Google Drive.
2. Right-click the video in Google Drive and click **Manage caption tracks**.
3. Click **Add new captions or transcripts**.
4. Upload a supported subtitle file.
   * It has been verified that Google Drive will accept .srt and .vtt subtitles. It might accept others as well, but they have not been tested.

Once you have uploaded your subtitles, they should be available the next time the video is refreshed by CyTube (either restart it or delete the playlist item and add it again.) In the video frame you should see a speech bubble icon in the controls, which will pop up a menu of available subtitle tracks.

### Limitations
* Google Drive converts the subtitles you upload into a custom format which loses some information from the original captions. For example, annotations for who is speaking are not preserved.
* As far as I know, Google Drive is not able to automatically detect when subtitle tracks are embedded within the video file. You must upload the subtitles separately (there are plenty of tools to extract captions / subtitles from .mkv and .mp4 files.)

# Userscript for Google Drive Media Playback
An additional userscript must be installed in a browser host extension / add-on in order to view media on CyTube that's hosted on Google Drive. A detailed installation guide can be found here: [CyTube Google Drive Userscript Installation Guide](gdrive-script-install.md)

# Help / Support
If you need help, you are encouraged to join the official CyTube support channel in IRC at [irc.6irc.net#cytube](http://webchat.6irc.net/?channels=cytube).  calzoneman is the developer, nuclearace is a CyTube admin, and many other people in the channel can help with common questions.

Please be patient; users in the support channel may not be able respond immediately. Most of the users in the channel are in the United States, so if you have trouble getting a response please try to come during USA daytime hours.

[Return to the Table of Contents for this page](#table-of-contents)  
[Go to the FAQ page](frequently-asked-questions.md)  
[Go to the Quick Reference page](index.md)
