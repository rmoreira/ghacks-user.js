### ![][b] user.js
A `user.js` is a configuration file that can control hundreds of Firefox settings. For a more technical breakdown and explanation, you can read more on the [overview](https://github.com/ghacksuserjs/ghacks-user.js/wiki/1.1-Overview) wiki page.

### ![][b] ghacks user.js
The `ghacks user.js` is a **template** which aims to provide as much privacy and enhanced security as possible, and to reduce tracking and fingerprinting as much as possible - while minimizing any loss of functionality and breakage (but it will happen).

Everyone, experts included, should at least read the [implementation](https://github.com/ghacksuserjs/ghacks-user.js/wiki/1.3-Implementation) wiki page, as it contains important information regarding a few `ghacks user.js` settings.

Note that we do *not* recommend connecting over Tor on Firefox. Use the [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en) if your [threat model](https://www.torproject.org/about/torusers.html.en) calls for it, or for accessing hidden services. 

Also be aware that this `user.js` is made specifically for Firefox. Using it as-is in other Gecko-based browsers can be counterproductive, especially in the Tor Browser.

Sitemap: [Releases](https://github.com/ghacksuserjs/ghacks-user.js/releases), [changelogs](https://github.com/ghacksuserjs/ghacks-user.js/issues?utf8=%E2%9C%93&q=is%3Aissue+label%3Achangelog), [Wiki](https://github.com/ghacksuserjs/ghacks-user.js/wiki), [stickies](https://github.com/ghacksuserjs/ghacks-user.js/issues?q=is%3Aissue+is%3Aopen+label%3A%22sticky+topic%22). [diffs](https://github.com/ghacksuserjs/ghacks-user.js/issues?q=is%3Aissue+label%3Adiffs)

### ![][b] acknowledgments
Literally thousands of sources, references and suggestions. That said...

* Martin Brinkmann at [ghacks](https://www.ghacks.net/) <sup>1</sup>
* The ghacks community and commentators
* [12bytes](https://12bytes.org/articles/tech/firefox/firefoxgecko-configuration-guide-for-privacy-and-performance-buffs)
   * The 12bytes article now uses this user.js and supplements it with an additional JS hosted at [GitLab](https://gitlab.com/labwrat/Firefox-user.js/tree/master)

<sup>1</sup> The ghacks user.js was an independent project by [Thorin-Oakenpants](https://github.com/Thorin-Oakenpants) started in early 2015 and was [first published](https://www.ghacks.net/2015/08/18/a-comprehensive-list-of-firefox-privacy-and-security-settings/) at ghacks in August 2015. With Martin Brinkmann's blessing, it will keep the ghacks name.

### ![][b] [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[b]: /wikipiki/bullet01.png

## What is this?

This is a branch I use on my desktop.

### Addons
I have made some changes to this `user.js` that would possibly be considered unsafe.

The intent is to use this `user.js` with some of the [extensions mentioned on the wiki](https://github.com/ghacksuserjs/ghacks-user.js/wiki/4.1-Extensions).

The current extensions I am using:

| **Extension**                                                                                  | **Source**                                                     | **Main Purpose**                                                                                                                 | Extra Settings                                                                                                                                                                                                                                                                                                |
|------------------------------------------------------------------------------------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ClearURLs](https://addons.mozilla.org/addon/clearurls/)                                       | [Source](https://gitlab.com/KevinRoebert/ClearUrls)            | Remove tracking elements from URLs                                                                                               |                                                                                                                                                                                                                                                                                                               |
| [CSS Exfil Protection](https://addons.mozilla.org/addon/css-exfil-protection/)                 | [Source](https://github.com/mlgualtieri/CSS-Exfil-Protection)  | Protect against [css exfil vulnerability](https://www.mike-gualtieri.com/css-exfil-vulnerability-tester)                         |                                                                                                                                                                                                                                                                                                               |
| [Decentraleyes](https://addons.mozilla.org/addon/decentraleyes/)                               | [Source](https://git.synz.io/Synzvato/decentraleyes)           | Protect against tracking through [CDN](https://en.wikipedia.org/wiki/Content_delivery_network)s                                  |                                                                                                                                                                                                                                                                                                               |
| [Firefox Multi-Account Containers](https://addons.mozilla.org/addon/multi-account-containers/) | [Source](https://github.com/mozilla/multi-account-containers)  | [Stay logged in](https://medium.com/@stoically/enhance-your-privacy-in-firefox-with-temporary-containers-33925cd6cd21)           | Add for sites I use                                                                                                                                                                                                                                                                                           |
| [HTTPS Everywhere](https://addons.mozilla.org/addon/https-everywhere/)                         | [Source](https://github.com/EFForg/https-everywhere)           | Prefer [HTTPS](https://en.wikipedia.org/wiki/HTTPS)                                                                              |                                                                                                                                                                                                                                                                                                               |
| [Redirect AMP to HTML](https://addons.mozilla.org/addon/amp2html/)                             | [Source](https://github.com/da2x/amp2html)                     | Prefer [decentralized web](https://www.daniel.priv.no/web-extensions/amp2html.html)                                              |                                                                                                                                                                                                                                                                                                               |
| [Temporary Containers](https://addons.mozilla.org/addon/temporary-containers/)                 | [Source](https://github.com/stoically/temporary-containers)    | Prevent cache fingerprinting ([ETags](https://en.wikipedia.org/wiki/HTTP_ETag#Tracking_using_ETags) etc), isolate/delete cookies | Automatic Mode, Random Container Color, Reuse availible numbers, [Set Global Isolation rules](#global-isolation)                                                                                                                                                                                              |
| [Tree Style Tab](https://addons.mozilla.org/addon/tree-style-tab/)                             | [Source](https://github.com/piroor/treestyletab)               | Useable web browsing                                                                                                             | Hide ["Tree Style Tab"](https://github.com/piroor/treestyletab/wiki/Code-snippets-for-custom-style-rules#hide-the-tree-style-tab-header-at-the-top-of-the-sidebar), also other [userChrome.css options](#userchrome-options), and TST [preferences](#tst-preferences)                                         |
| [uBlock Origin](https://addons.mozilla.org/addon/ublock-origin/)                               | [Source](https://github.com/gorhill/uBlock)                    | Filtering                                                                                                                        | [Add decentraleyes rules](https://git.synz.io/Synzvato/decentraleyes/wikis/Frequently-Asked-Questions#for-umatrix-and-ublock-origin-non-easy-mode-users)                                                                                                                                                      |
| [uMatrix](https://addons.mozilla.org/firefox/addon/umatrix/)                                   | [Source](https://github.com/gorhill/uMatrix)                   | Filtering according to src, dst and type                                                                                         | [Add decentraleyes rules](https://git.synz.io/Synzvato/decentraleyes/wikis/Frequently-Asked-Questions#for-umatrix-and-ublock-origin-non-easy-mode-users), [1st party mode](https://github.com/gorhill/uMatrix/wiki/How-to-block-1st-party-scripts-everywhere-by-default) for media, script, XHR, frame, other |
| [Violentmonkey](https://addons.mozilla.org/addon/violentmonkey/)                               | [Source](https://github.com/violentmonkey/violentmonkey)       | [Various scripts used with Violentmonkey](#various-scripts-used-with-violentmonkey)                                              |                                                                                                                                                                                                                                                                                                               |

#### Global Isolation
[Temporary Containers wiki article](https://github.com/stoically/temporary-containers/wiki/Global-Isolation):

- Navigating in Tabs should open new Temporary Containers
  - If the Navigation Target Domain does not match the active Tabs Domain (Subdomains won't get isolated)
- Mouse Clicks on Links should open new Temporary Containers
  - Middle Mouse
    - If the clicked Link Domain does not exactly match the active Tabs Domain (Subdomains also get isolated)
  - Ctrl/Cmd+Left Mouse
    - Always
  - Left Mouse
    - If the clicked Link Domain does not match the current Tabs Domain (Subdomains won't get isolated)

#### Various scripts used with Violentmonkey
- [Disable Youtube autoplay](https://greasyfork.org/en/scripts/34651-disable-youtube-autoplay) 
- [Old Reddit Please!](https://greasyfork.org/en/scripts/40897-old-reddit-please)
- [viewimage.user.js](https://gist.github.com/bijij/58cc8cfc859331e4cf80210528a7b255/#file-viewimage-user-js)

#### Configure once off search engines and keywords

More [info](https://www.ghacks.net/2016/08/09/firefox-one-off-searches-address-bar).

#### Userchrome options
```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/* Remove default items from the urlbar-container */
#back-button,
#forward-button,
#stop-reload-button,
#reload-button,
#customizableui-special-spring1,
#home-button,
#customizableui-special-spring2,
#library-button,
#sidebar-button {
    display:none;
}

/* Disable Tab toolbar for Tree Style Tab */
#tabbrowser-tabs {
    visibility: collapse !important;
}

#sidebar-header {
    display: none;
}
```

#### TST Preferences
- Tree Behavior
  - ☐ "When a new tree appears, collapse others automtically"
  - ☐ "When a tab gets focus, expand its tree and collapse others automatically"
  - ☐ "Except focus moving caused by current tab closing"
  - ☑️ "Double-click on a tab to collapse/expand tree"

### Thunderbird specific addons:

Not strictly relevant but I thought I'd mention it anyway.

| **Extension**                                                                | **Source**                                                           | **Main Purpose**                                                                                                                                                                                                                                                                                                                 |
|------------------------------------------------------------------------------|----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Cardbook](https://addons.thunderbird.net/addon/cardbook/)                   | [Source](https://gitlab.com/CardBook/CardBook)                       | Access [radicale](https://radicale.org) instance for contacts                                                                                                                                                                                                                                                                    |
| [Header Tools Lite](https://addons.thunderbird.net/addon/header-tools-lite/) | [Home](https://freeshell.de/~kaosmos/headertoolslite-en.html)        | Used to edit [`References`](https://en.wikipedia.org/wiki/Email#Header_fields) to have correct [`Message-ID`](https://en.wikipedia.org/wiki/Message-ID) to maintain [threading on mailing lists when not subscribed](https://superuser.com/questions/1177870/how-to-manually-set-the-in-reply-to-header-in-thunderbird/1189889). |
| [Lightning](http://www.mozilla.org/projects/calendar/)                       | [Source](https://hg.mozilla.org/comm-central/file/tip/calendar)      | Calendars                                                                                                                                                                                                                                                                                                                        |
| [Markdown Here](https://markdown-here.com)                                   | [Source](https://github.com/adam-p/markdown-here)                    | Write pretty HTML emails sometimes                                                                                                                                                                                                                                                                                               |
| [Enigmail](https://addons.thunderbird.net/addon/enigmail/)                   | [Source](https://www.enigmail.net/index.php/en/download/source-code) | PGP                                                                                                                                                                                                                                                                                                                              |
