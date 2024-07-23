---
_schema: default
title: Move Zone Folder To a Different Disk
nav_title: Move Zone Folder To a Different Disk
nav_section: IT Admin
weight: 302
draft: false
---
While you can use the app's "Location on Disk" Zone setting to move a Zone folder to a new location on the same disk, it will not allow you to move the Zone folder to another disk or external drive.

This article describes how to move the Zone folder to another disk or external drive.

This article is primarily for apps installed on a computer. Mobile app folder locations are much more complicated to move since each application on iOS and Android usually operates inside of its own process space.

Do not unlink/restore a Zone folder before it has finished syncing an initial complete file set - this could result in a loss of data. Instead, it is better to unlink your Zone (steps 1 and 2), then set your profile's default Zone location to your external disk, and then goto Profile-&gt;Invites and accept your Zone invite again and re-build the files from scratch.

1. Before moving the Zone folder, first open your Zone's folder in your OS's explorer/finder window

In your Zone, click the folder icon:

![](/uploads/image-21.png)

In the folder/file view, make sure you are at the base of your files for the Zone, and click the "open in OS" icon:

![](/uploads/image-22.png)

This will open a folder on your desktop:

![](/uploads/image-23.png)

Go "up" a level so you can see the folder from its base location:

![](/uploads/image-24.png)

Leave this open - you will cut/paste the Zone folder to a new location in step 3.

1. Unlink / Disable your Zone

Next, you need to unlink your Zone from the app so that it is not active.

To do this, click the profile image/circle in the upper right of your app:

![](/uploads/image-25.png)

Select "Zones":

![](/uploads/image-26.png)

In the Zone list, select the Zone you want to move, and click "Disable":

![](/uploads/image-27.png)

Accept the warning, and you will see the Zone disappear from your Zone list and also from your Zone selector side bar.

1. Use your OS explorer to physically move the Zone folder

Go back to your folder view and copy the folder:

![](/uploads/image-28.png)

Open a folder view to your external drive and paste the folder there:

![](/uploads/image-29.png)

1. Restore your Zone folder from its new location

Go back to your Profile-&gt;Zones page and click the + icon and click "Restore":

![](/uploads/image-30.png)

Navigate to your external drive and select your moved Zone folder and click "Restore":

![](/uploads/image-31.png)

Voila - your Zone is now back up and running at your new location!

&nbsp;

---

&nbsp;