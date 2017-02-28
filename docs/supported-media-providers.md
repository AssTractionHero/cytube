# Media Providers

## Important Notice

**After January 10th, 2017, CyTube supports media hosted only on HTTPS-compliant sites.**

# Video Providers
  - YouTube:
    * Single video: `https://www.youtube.com/watch?v=(video id)` or
      `https://youtu.be/(video id)`
    * Playlist: `https://www.youtube.com/playlist?list=(playlist id)`
  - Vimeo
  - Vid.me
  - Streamable.com
  - Dailymotion
  - Google Drive: `https://docs.google.com/file/d/(doc id)/edit` or
    `https://drive.google.com/open?id=(doc id)`
    * As of 14 September 2015, Google has made a breaking change and Google Drive videos on CyTube use a hacky Flash 
    player solution that may or may not work for you. A userscript has since been developed that gives greater functionality for
    Google Drive videos. That userscript, and detailed installation instructions can be found [here.](gdrive-script-install.md)
    * Find the video in your Drive, right click it, click "Share...", then click
      "Get shareable link".
    * Paste the link into your playlist.

# Audio Providers

  - Soundcloud

# Streaming Providers

  - Twitch
    * Recorded videos on Twitch are also supported
  - Hitbox
  - Livestream.com
  - Ustream
  - RTMP streams: `rtmp://(stream link)`

# Miscellaneous

  - H.264 encoded .mp4 and .flv, VP8 / VP9 encoded WebM, and Ogg / Theora videos can
    be added as a direct link to the video file.
    * If you are trying to share a video that's on your computer, you will first
      need to upload it to a suitable host.  Unless you are running your own
      webserver (most public file hosting sites will not work), you are better
      off using one of the other video providers listed above.
  - .mp3 and Ogg / Vorbis audio files can be added as a direct link to the audio
    file.
  - `<iframe>` embeds from other websites can be embedded, however **these
    cannot be synchronized**.

Direct links can only be added when ffmpeg is installed on the server and
enabled in the CyTube configuration file.  Additionally, these are just the
codecs that are accepted by CyTube; if you are using an old version of ffmpeg
then some of these supported codecs may result in errors (e.g. VP9 is not
readable by the version of libav-tools in Debian Wheezy stable).

## For direct links, why can't I add .mkv, .avi, or some other video format?

While the server backend could potentially support a large number of formats for
raw video files, CyTube is limited by the kinds of videos that can be played on
modern browsers.  Without requiring special plugins, most HTML5 compliant
browsers can only play .mp4 / H.264, WebM / VP8, WebM / VP9, and Ogg / Theora videos.
See
[MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats#AutoCompatibilityTable)
for a table of browser support.

For best results, use .mp4 / H.264 videos as these are supported by most browsers
and can also be played by the fallback Flash player.

## Why can't I add a direct link from Putlocker?  

Some websites, such as Putlocker, restrict access to the video link to your
specific IP address.  These links cannot be added to CyTube, since CyTube is not
able to access them.

## Why does every video come up as "youtube.com/devicesupport"?

You may see this message if you are running an outdated version of CyTube, or
have not updated your configuration since the YouTube API switch.  YouTube
deprecated version 2 of their API in April 2015.  CyTube needs to be updated and
configured to use version 3 of the API.

## Can you add a new media provider?  

Probably not.  Most media providers that are requested do not have a
synchronization API, hence they cannot be synchronized on CyTube.  However, if a
provider does meet the requirements and has sufficient demand, I will consider
adding it.

[Back to Quick Reference](index.md)
