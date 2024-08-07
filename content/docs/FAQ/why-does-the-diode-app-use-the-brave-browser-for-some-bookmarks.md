---
_schema: default
title: Why does the Diode App use the Brave Browser for some bookmarks?
nav_title: Why the Brave Browser for bookmarks?
nav_section: FAQ
weight: 20018
draft: false
---
Through Q1 of 2024, there are two browser options for tunneled Bookmarks: 1) Integrated (Alpha) and 2) Brave (Beta)

Although the Diode App can load may types of websites via its integrated browser, it does not yet have full support for all types of websites. More complex sites are often not rendered correctly due to the way that the integrated browser manages the tunnels.

Therefore, as a stop gap, we added support for automatically launching a <a href="https://en.wikipedia.org/wiki/Chromium_(web_browser)" target="_blank" rel="noopener"><strong>Chromium browser</strong></a> - the Brave Browser - if the bookmark is so-configured. The Brave Browser has full support for all of the browser edge cases required. A bookmark configured to use the Brave Browser will open it configured to use the Diode proxy tunnel specified in the bookmark's settings (e.g. route and regional exit location).

However, there are a few "gotchas" still with bookmarks that use the Brave Browser:

1. Each user has to <a href="https://brave.com/" target="_blank" rel="noopener"><strong>install the Brave Browser</strong></a> separately from Diode
2. If a new bookmark is created, the Diode App has to be restarted before the tunnel becomes available
3. If Brave is launched on one bookmark, but the user then accesses a different bookmark that uses a different tunnel, the Brave Browser must be fully shut down between clicking on the different bookmarks
4. Bookmarks configured to use Brave will not work on mobile

We are under development on full integrated browser and mobile support, targeted for late Q2 2024. Once this is released, the four items above will cease to be a factor.