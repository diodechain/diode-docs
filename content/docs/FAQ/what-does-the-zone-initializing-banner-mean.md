---
_schema: default
title: What does the "Zone Initializing" banner mean?
nav_title: What does the "Zone Initializing" banner mean?
nav_section: FAQ
weight: 20019
draft: false
---
The "Zone Initializing" banner in the app indicates your new Zone is not fully setup yet.  This banner will never be shown if you are creating the Zone, but will usually show up if you are joining the Zone or adding it to a <a href="/docs/using/linked-devices/" target="_blank" rel="noopener">Linked Device</a>.  It looks like this:

![](/uploads/image-99.png)

If the banner is showing, it means one or more settings in your Zone have not yet been received by your device.  Until all settings are received, your Zone may not work like you expect it to. However, sometimes the banner will persist for a long time.  Usually, this will only happen if no other team member is online.  In this case, there will be no-one to relay to you the Zone settings - your Zone will remain at least partially unconfigured until a team member comes online and you are able to sync the settings and content from them.

However, if your device is able to reach the Diode Network, the progress bar should be at least at 10% - meaning it is able to resolve who the other members are in the Zone.

If the initialization makes some progress, a small "X" will appear on the right side of the initializing banner, allowing you to close the banner and to access the features in your Zone.  Once you close the banner, it will not re-appear for your Zone no matter if the Zone is properly initialized or not.

The following milestones contribute to the bar's overall progress when your device:

* Can resolve other team members: 10%
* Is up to date with chat data: 25%
* Knows which files it is missing: 15%
* Has less than 1,000 files to sync: 5%
* Has less than 100 files to sync: 10%
* Has less than 10 files to sync: 10%
* Has all files up to date: 25%