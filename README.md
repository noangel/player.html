# player.html
One file drop-in video player web app for using MP4 video files served using basic directory listing.

![player.html in action](https://user-images.githubusercontent.com/455424/91237221-df3ad080-e6ee-11ea-83c7-f13be539c73e.jpg)
![player.html on all of your devices](https://user-images.githubusercontent.com/455424/91237209-d649ff00-e6ee-11ea-9f8d-3a33cd535e81.png)

## Usage
`player.html` is designed to be a drop-in video player that does not require any configuration or other files.

To use it, copy the [`./src/player.html`](src/player.html) file into a folder that is served over HTTP using the web server's folder listing functionality. `player.html` basically uses the folder listing as an API for enumerating the files and folders. It should work with almost any web server, but it has only be tested against NGINX, Apache, and IIS.

### Supported features

* Only 1 file with zero external dependencies
* [`SVG images`](https://github.com/microsoft/fluentui-system-icons/) are inlined
* May be installed as a PWA (Progressive Web App) app. Dynamically generated inline data URI manifest file.
* Playback of `MP4`, `M4V`, `MKV`, `WEBM`, and `OGG` files using the browser video engine
* Sharable URL that will load `player.html` in the same folder location, and video position
* Custom video playback controls (fullscreen, play, pause, mute, etc)
* Progress bar with timestamp preview thumbnail on hover
* Jump forward/backward 15 seconds
* Video thumbnail generation, with concurrency configuration (default 1)*
* Thumbnail caching using `localStorage`
* Social media metadata (`og:\*`, `twitter:\*`)
* Support for playing videos directly from **OneDrive** and **Google Drive**. You **must supply the appropriate keys** in the `app.options.cloud` AND register your app with Microsoft and/or Google. Instructions are in the code. `player.html` also *must be served over HTTPS* for the Microsoft and Google auth flows to work. [Remix this Glitch](https://glitch.com/edit/#!/player-html-remix?path=src%2Fplayer.html%3A487%3A10) to easily check it out over HTTPS with your own API keys.

\* Be careful with concurrency. Increasing the setting above 1 does make it generate thumbnails much faster. But it is very easy for HTTP requests for generating thumbnails to saturate a connection enough that the main video gets starved for bandwidth. Especially if you browse into a folder with many dozens of videos in it.

### Supported Web Servers

* NGINX ([`autoindex`](https://nginx.org/en/docs/http/ngx_http_autoindex_module.html) on)
* Apache ([`mod_autoindex`](https://cwiki.apache.org/confluence/display/HTTPD/DirectoryListings))
* IIS (enable [`Directory Browsing`](https://docs.microsoft.com/en-us/iis/configuration/system.webserver/directorybrowse))

## License

* [MIT](./LICENSE)

&copy; 2020 Paul Ellis
