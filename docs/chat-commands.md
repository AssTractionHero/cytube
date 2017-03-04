## Chat Commands
### Standard Commands
  * `/me <message>` - Sends a message as an action, e.g. *calzoneman gets a snack*.
  * `/sp <message>` - Hides a message in a hover-to-expose spoiler box.
  * `/afk` - Toggles your AFK status.  You will automatically be unmarked as AFK after sending a chat message or voteskipping a video.

### Moderator Commands
  * `/say <message>` - Sends a message in big red text.
  * `/poll <title>,<option1>,<option2>,...` - Opens a new poll (this is from before the New Poll button was added).
  * `/hpoll <title>,<option1>,<option2>,...` - Same as above, but hides poll results.
  * `/mute <user>` - Mutes a user from sending chat messages.
  * `/smute <user>` - Shadowmutes a user.  They will still receive their own chat messages but nobody else will see them except 
  for moderators that have "Show shadowmuted messages" enabled, and they will not appear muted except to moderators.
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
  
[Back to CyTube 3.0 User Guide](index.md)
