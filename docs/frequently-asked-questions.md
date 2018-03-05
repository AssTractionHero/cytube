# Frequently Asked Questions  

## Table of Contents

  * [Which media providers are supported?](#which-media-providers-are-supported)
  * [For direct links, why can't I add .mkv, .avi, or some other video
    format?](#for-direct-links-why-cant-i-add-mkv-avi-or-some-other-video-format)
  * [Why can't I add a direct link from
    Putlocker?](#why-cant-i-add-a-direct-link-from-putlocker)
  * [How do I pause or seek the video?](#how-do-i-pause-or-seek-the-video)
  * [Why does every video come up as
    "youtube.com/devicesupport"?](#why-does-every-video-come-up-as-youtubecomdevicesupport)
  * [Can you add a new media provider?](#can-you-add-a-new-media-provider)
  * [How can I set a background image / customize my
    channel?](#how-can-i-set-a-background-image-customize-my-channel)
  * [Why does the video show "Video format or MIME type not
    supported"?](#why-does-the-video-show-video-format-or-mime-type-not-supported)
  * [Why don't chat and the video load when I join a
    channel?](#why-dont-chat-and-the-video-load-when-i-join-a-channel)
  * [How do I enable subtitles on Google Drive
    videos?](#how-do-i-enable-subtitles-on-google-drive-videos)
  
### Don't see your question here?

You may also find more information here:

[CyTube 3.0 User Guide](index.md)  
[CyTube 3.0 Wiki](cytube-3-wiki.md)

Community support for CyTube is provided on
[EsperNet](http://webchat.esper.net/?channels=cytube).  Please be patient; users in
the support channel may not respond immediately.  Most of the users in the
channel are in the United States, so if you have trouble getting a response,
please try to come during U.S.A. daytime hours.

You can also get support for CyTube via email.  CyTube is developed by
[calzoneman/cyzon](mailto:cyzon@cytu.be), but
[nuclearace](mailto:nuclearace@cytu.be) is also an administrator, and can help
with common problems and questions.

## Which media providers are supported?

### Video Providers

  * YouTube:
    * Single video: `https://www.youtube.com/watch?v=(video id)` or
      `https://youtu.be/(video id)`
    * Playlist: `https://www.youtube.com/playlist?list=(playlist id)`
  * Vimeo
  * Vid.me
  * Streamable.com
  * Dailymotion
  * Google Drive: `https://docs.google.com/file/d/(doc id)/edit` or
    `https://drive.google.com/open?id=(doc id)`
    * Find the video in your drive, right click it, click "Share...", then click
      "Get shareable link". 

## Important Notice  
In August 2016, after numerous failures that resulted in the disruption of the operation of many channels, 
the decision was made to phase out native support for Google Drive and instead require users to install a 
userscript to view Google Drive-hosted videos.  Installation instructions can be found  here for the [CyTube Google Drive Userscript](gdrive-script-install.md) that gives the necessary functionality to play Google Drive media.
 
### Audio Providers

  * Soundcloud

### Streaming Providers

  * Twitch
    * Recorded videos on Twitch are also supported
  * Hitbox
  * Livestream.com
  * Ustream
  * RTMP streams: `rtmp://(stream link)`

## Miscellaneous

  * H.264 encoded .mp4 and .flv, VP8 / VP9 encoded WebM, and Ogg / Theora videos can
    be added as a direct link to the video file.†
    * If you are trying to share a video that's on your computer, you will first
      need to upload it to a suitable host.  Unless you are running your own
      webserver (most public file hosting sites will not work), you are better
      off using one of the other video providers listed above.
  * .mp3 and Ogg / Vorbis audio files can be added as a direct link to the audio
    file.†
  * `<iframe>` embeds from other websites can be embedded, however **these
    cannot be synchronized**.

† Direct links can only be added when ffmpeg is installed on the server and
enabled in the CyTube configuration file.  Additionally, these are just the
codecs that are accepted by CyTube; if you are using an old version of ffmpeg
then some of these supported codecs may result in errors, e.g. VP9 is not
readable by the version of libav-tools in Debian "Wheezy" (stable).

### For direct links, why can't I add .mkv, .avi, or some other video format?  

While the server backend could potentially support a large number of formats for
raw video files, CyTube is limited by the kinds of videos that can be played on
modern browsers.  Without requiring special plugins, most HTML5 compliant
browsers can only play .mp4 / H.264, .webm / VP8, .webm / VP9, and Ogg / Theora videos.
See
[MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats#AutoCompatibilityTable)
for a table of browser support.

For best results, use .mp4 / H.264 videos as these are supported by most browsers
and can also be played by the fallback flash player.

### Why can't I add a direct link from Putlocker?

Some websites, such as Putlocker, restrict access to the video link to your
specific IP address.  These links cannot be added to CyTube, since CyTube is not
able to access them.

### How do I pause or seek the video?

CyTube controls the video playback with a timer on the server in order to
provide smooth playback and prevent accidental clicks by channel moderators
from interrupting the video for other people.  However, if you need to control
the video, you can right click your name in the userlist and click "Give
Leader".  While you are leader, you will be able to pause/unpause and seek the
video.  When you're done, right click your name again and click "Take Leader".  
This feature is disabled if you do not have the proper permission to use it.

### Why does every video come up as "youtube.com/devicesupport"?

You may see this message if you are running an outdated version of CyTube, or
have not updated your configuration since the YouTube API switch.  YouTube
deprecated version 2 of their API in April 2015.  CyTube needs to be updated and
configured to use version 3 of the API.

### Can you add a new media provider?

Probably not.  Most media providers that are requested do not have a
synchronization API, hence they cannot be synchronized on CyTube.  However, if a
provider does meet the requirements and has sufficient demand, I will consider
adding it.

### How can I set a background image / customize my channel?

CyTube channels are customizable with CSS.  Click on **Channel Settings**, then
click the **Edit** drop down and click **CSS**.  Mozilla has an introductory tutorial
about CSS
[here](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started).  
This is another site that has a good tutorial for learning CSS:
[W3Schools Online](https://www.w3schools.com/css/default.asp).  

If you're not concerned about other customizations and just want a background
image, you can use the following CSS:

```css
body {
    background-image: url(http://link-to-image);
}
```

(replace `link-to-image` with the full URL of the background image)

### Why does the video show "Video format or MIME type not supported"?

This error message means the video codec being embedded is not able to be played
by your browser.  For best codec support, try loading the website with Firefox
or Chrome.

### Why don't chat and the video load when I join a channel?  

If you don't see a green box in chat with the text "Connected", then your
websocket connection could not be established.  This is often caused by
antivirus or firewall software on your computer that detects the websocket
connection as a false positive and blocks it.

Try disabling your antivirus or firewall temporarily and connecting again.  If
it works, then the antivirus or firewall is the problem.  You should check the
manual or customer support for that specific software to figure out how to
allow websocket connections without completely disabling the software.

### How do I enable subtitles on Google Drive videos?

As of July 28th, 2015, it is now possible to use Google Drive subtitles on
CyTube.  Please see [this link](google-drive-subtitles.md)
for instructions on adding subtitles to your Google Drive videos.

[Return to the top of this page](#frequently-asked-questions)  
[Back to CyTube 3.0 User Guide](index.md)  
