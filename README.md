# player.html
One file drop-in video player web app for using MP4 video files served using basic directory listing.

![player.html in action](https://user-images.githubusercontent.com/455424/140204106-eff3504d-64f0-4038-977b-52555dd96358.png)
![player.html on all of your devices](https://user-images.githubusercontent.com/455424/140200711-7a414217-63db-41b7-8f6e-8d00d7e9eb27.png)

## Usage
`player.html` is designed to be a drop-in video player that does not require any configuration or other files.

To use it, copy the [`./src/player.html`](src/player.html) file into a folder that is served over HTTP using the web server's folder listing functionality. `player.html` basically uses the folder listing as an API for enumerating the files and folders. It should work with almost any web server, but it has only been tested against NGINX, Apache, and IIS.

### Supported features

* Only 1 file with zero external dependencies
* [`SVG images`](https://github.com/microsoft/fluentui-system-icons/) are inlined
* May be installed as a PWA (Progressive Web App) app. Dynamically generated inline data URI manifest file.
* Playback of `MP4`, `M4V`, `MOV`, `MKV`, `WEBM`, and `OGG` files using the browser video engine
* Support for loading external `SRT` and `VTT` subtitle files
* Shareable URL that will load `player.html` in the same folder location, and video position
* Custom video playback controls (fullscreen, play, pause, mute, etc, volume, playback rate)
* Picture-in-picture support
* Progress bar with timestamp preview thumbnail on hover
* Video thumbnail generation, with concurrency configuration (default 1)*
* Animated thumbnails**
* Thumbnail caching using `localStorage`, check cache size, clear cache
* Select your own custom theme color
* Social media metadata (`og:\*`, `twitter:\*`)
* Video file metadata (bitrate, resolution, etc)
* Keyboard shortcuts (press `?` to see the list)
* Paste and Play: just do `CTRL+V` to play the video URL that you currently have in the clipboard
* Support for playing videos directly from ![onedrive](https://user-images.githubusercontent.com/455424/93652838-4cc6dd80-f9cb-11ea-8d8c-062705d5500e.png) **OneDrive** and ![gdrive](https://user-images.githubusercontent.com/455424/93652836-4c2e4700-f9cb-11ea-9a71-7325f745baf9.png) **Google Drive**. You **must supply the appropriate keys** in the `app.options.cloud` AND register your app with Microsoft and/or Google. Instructions are in the code. `player.html` also **must be served over HTTPS** for the Microsoft and Google auth flows to work. [Remix this Glitch](https://glitch.com/edit/#!/player-html-remix?path=src%2Fplayer.html%3A487%3A10) to easily check it out over HTTPS with your own API keys.

\* Be careful with concurrency. Increasing the setting above 1 does make it generate thumbnails much faster. But it is very easy for HTTP requests for generating thumbnails to saturate a connection enough that the main video gets starved for bandwidth. Especially if you browse into a folder with many dozens of videos in it.

\** Animated thumbnails can consume a lot of data. The experience may degrade on slower network connections

## Supported Browsers

The latest version of these browsers is supported:

* Edge (Chromium)
* Edge (Xbox EdgeHTML)†
* Firefox
* Safari (Mac, iPadOS, iOS)
* Chrome

† Deprecated: EdgeHTML is only supported on Xbox as it has been replaced on Windows 10.

## Supported Web Servers

The latest version of these web servers (others may work as well):

* NGINX ([`autoindex`](https://nginx.org/en/docs/http/ngx_http_autoindex_module.html) on)
* Apache ([`mod_autoindex`](https://cwiki.apache.org/confluence/display/HTTPD/DirectoryListings))
* IIS (enable [`Directory Browsing`](https://docs.microsoft.com/en-us/iis/configuration/system.webserver/directorybrowse))

## Other

* `player.html` uses [folder.api](https://github.com/pseudosavant/folder.api) to consume HTTP directory listings like an API
* `player.html` uses [video-thumbnail.js](https://github.com/pseudosavant/video-thumbnail.js) to render thumbnails from video file URLs

## License

* [MIT](./LICENSE)

&copy; 2021 Paul Ellis
