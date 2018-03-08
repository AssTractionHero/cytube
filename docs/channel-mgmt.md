## Channel Management
You must be logged in to your account to manage your channels.

### Registering a Channel
In the navigation bar at the top of the page click on **Account** then click on **Channels**.  In the right column, enter the desired channel name and click **Register**.  If that channel is not already registered to another account, it will be created and registered to your name.  The website administrator may limit the number of channels that can be registered to one account.

### Deleting a Channel
In the navigation bar at the top of the page click on **Account** then click on **Channels**.  The left column lists all channels registered to your name.  Click the **Delete** button to unregister a channel.  This will permanently clear all database information (ranks, library, bans,) and state information (playlist, configuration, MOTD, filters, etc.,) and is **non-reversible**.  You will be asked to confirm your deletion.  

## Channel Settings
From your channel page (/r/channelname), users with moderator or higher rank will see a **Channel Settings** button on the top navigation bar.  This opens a dialog box which allows various aspects of your channel to be managed, explained below:

### General Settings

 Setting | Description
 --------|------------
 Convert URLs in chat to links | If enabled, URLs entered into chat (e.g. http://google.com) will be converted to clickable hyperlinks.
Allow voteskip | If enabled, users may click the voteskip button to indicate a preference to skip the currently playing video.  
Voteskip ratio | The proportion of votes from non-AFK users required to skip the current video.  The number of votes required is calculated as `ceil(voteskip ratio * number of non-AFK users)`.
Max video length | Specify the maximum duration of a playlist item.  Set this to `00:00:00` to allow unlimited length.
Auto-AFK Delay | After this delay (in seconds) of a user sending no chat messages and not voteskipping, the user will be automatically marked as "AFK".
Throttle chat | Enables a flood filter that will limit how quickly a user can send chat messages.  
-# of messages allowed before throttling | When Throttle chat is active, this controls the number of messages a user can send with no time delay before the flood filter engages.
-# of messages allowed per second | After the threshold of the flood filter is exceeded, only this number of messages from a certain user are allowed per second.  Additional messages are ignored.  
Delay before new accounts can chat | How long an account must be active before the user can send any chat message. Setting it to `00:00` disables this restriction.
Delay before new accounts can post links in chat | How long an account must be active before the user can send a chat message containing a URL. Setting it to `00:00` disables this restriction.  
    
### Admin Settings

 Setting | Description
 --------|------------ 
Page title | The title displayed on the browser window / tab.
Password | An optional password required for non-moderators to enter the room.  Leave blank to disable.
External CSS | URL to an external stylesheet to apply to the page.
External Javascript | URL to an external script to run on the page.
List channel publicly | When enabled, displays the channel name on the index page.  Only active channels (channels with at least 1 user) will be displayed.
Block connections from TOR | Prevents users from connecting through TOR.
Allow ASCII control characters (e.g. newlines) | When enabled, control characters are enabled in chat.
Max # of videos per user | When enabled, limits the number of videos that a user may add to the playlist. Set this to '0' for no limit.

### Edit / Chat Filters
Chat filters provide a way for specific text to be recognized and changed in chat messages.  For example, it could be used to transform profanity to strings of asterisks.  **Please do not use chat filters for image emotes.**  CyTube 3.0 has an emotes feature which is better-suited for adding emoticons. Adding them as chat filters is more difficult to manage and uses more server resources.  

#### Adding a new filter

 Setting | Description
 --------|------------ 
Filter name | A name to identify the filter.  For informational purposes only, but must be unique.
Filter regex | A regular expression describing the text to match.
Flags | A set of regular expression flags to apply.  `g` means to match all instances in the message (instead of just the first), `i` means to match without case sensitivity.
Replacement | The HTML that will replace the matched text.

See the MDN page for [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) for reference on Regular Expressions and flags.

#### Managing existing filters
Filters will be applied in the order they are listed.  You can click and drag individual filters to rearrange them.  The **Active** checkbox allows you to easily enable / disable individual filters.  Under the **Control** column, the left button with a list icon opens an editor to change the regular expression, flags, and replacement for a filter.  The red button with a trashcan icon will delete the filter.

The **Filter Links** checkbox controls whether this filter will be applied to links in chat.  By default, this is off, to prevent filters from breaking links pasted in chat by changing them.

#### Importing / Exporting filters (New in CyTube 3.0)
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

[Return to the top of this page](#channel-management)  
[Back to the CyTube 3.0 User Guide](index.md)
