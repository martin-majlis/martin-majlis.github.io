---
layout: post
title:  "Chrome Extension Usage Mystery"
date:   2017-06-26 11:38:57 +0100
categories: facebook "Google Analytics" "Chrome extensions"
---

Last month I have published my extension [Facebook Backup][facebook-backup] for downloading photos and videos from Facebook groups and pages. When I wanted to check it's usage, I have found out, that there three different ways, how it can be measured.

# Developer Dashboard #

These statistics are for free since they are available directly in Developer Dashboards. They are showing number in impressions, installation, total users, and uninstalls.

![Developers Dashboard - Usage](/assets/2017-06-26-chrome-extension-dd-usage.png)

# Google Analytics in Developer Dashboard #

In developer dashboard is's possible to set up Google Analytics code.

![Developers Dashboard - Google Analytics](/assets/2017-06-26-chrome-extension-dd-settings.png)


This allows tracking visits of detail page as well as from which location the extension was installed. Visited pages looks like this:

* `/webstore/detail/ext/free/...` - view of detail page
* `/track_install/search/ext/free/...` - installation from search page
* `/track_install/detail/ext/free/...` - installation from detail page

# Google Analytics in extension #

It's possible to integrate Google Analytics directly into [extension][extension-tut] and track usage in the same way as any other web page. It should be also possible to track installations also from [here][extension-track-installs], but I haven't implemented it yet.

# Statistics #

Combining all these different sources should provide an easy way for measuring number of current users as well as their growth. For example usage growth could be received from:

* Number of istallations minus number of uninstallations from Developer Dashboard
* Change in total current users from Developer Dashboard
* Change in number of active users for various time period

Raw data are available in following [google docs].

# Observations #
* Number of installations reported in developer dashboard is lower than number of installations from Google Analytics.
* Growth in user count doesn't much difference between installations and uninstallations.
* Total number of users is not cummulative sum over difference between installs and unistalls.
* Total number of users is somewhere between number of active users in last 14 and 30 days.
* Total number of users should represents number of users whose Chrome browser checked for an update within the last week. ([in 2012])

[facebook-backup]: https://chrome.google.com/webstore/detail/facebook-backup-download/cipgolmkimeojgfilkiofiifhpecjbkj
[extension-tut]: https://developer.chrome.com/extensions/tut_analytics
[extension-track-installs]: https://developer.chrome.com/extensions/runtime#event-onInstalled
[google docs]: https://goo.gl/MfuPq9
[in 2012]: https://groups.google.com/a/chromium.org/forum/#!msg/chromium-apps/Sie4cmSTZmk/d-YJtCdcvW0J
