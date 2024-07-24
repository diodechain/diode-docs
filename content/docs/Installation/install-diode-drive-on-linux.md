---
_schema: default
title: Install Diode Drive on Linux
nav_title:
nav_section: Installation
weight: 5
draft: false
---
Follow the three steps below to get up and running on Linux (Raspberry Pi/ARM shown below).

---

**1\. Download**

[**Download Diode Drive**](https://diode.io/resources/download) for Linux - pay attention to the Linux variant (x86, ARM, 32/64 bit) to ensure you download the right one for your system.

**2\. Install and run Diode Drive**

Set the File Permissions for the downloaded .run file to include "Execute".

![](https://files.helpdocs.io/qwk5dmv7m8/articles/d3eguu0pem/1615810674835/image.png)

Open a terminal window and run the installer - it will extract to ~/dDrive

![](https://files.helpdocs.io/qwk5dmv7m8/articles/d3eguu0pem/1615810812636/image.png)

You can then either run it from a terminal window from the ~/dDrive folder with: `./dDrive start_iex` , or click the "Diode Drive Decentralized Storage" icon from the UI and select "Execute".

![](https://files.helpdocs.io/qwk5dmv7m8/articles/d3eguu0pem/1615811022243/image.png)

Some Linux installations <a href="https://github.com/diodechain/diode_drive_feedback/issues/14" target="_blank" rel="noopener"><strong>have a bug with the UI and file updates</strong></a> (last checked: March 15, 2021)

If your installation is not automatically synchronizing file changes, install the "inotify-tools" package via the command line:

`sudo apt install inotify-tools`

If the user interface doesn't load, try installing the topicons extension from <a href="https://extensions.gnome.org/extension/495/topicons/" target="_blank" rel="noopener"><strong>https://extensions.gnome.org/extension/495/topicons/</strong></a>

Recent (as of June 2021) Raspberry Pi Linux OS (Raspbian) no longer packages <a href="https://packages.debian.org/search?keywords=libglu1-mesa" target="_blank" rel="noopener"><strong>an OpenGL driver</strong></a> required by Diode Drive. If Diode Drive does not start on your Raspberry Pi, install the drive from a terminal window: `sudo apt install libglu1-mesa`

**3\. Verify Diode Drive is running**

When Diode Drive starts up, it will load as a small orange icon in the task bar:

![](https://files.helpdocs.io/qwk5dmv7m8/articles/d3eguu0pem/1615794188005/image.png)

Clicking the orange Diode Drive icon will drop-down / pop-up menu options. Click "Open" to open the app.

![](https://files.helpdocs.io/qwk5dmv7m8/articles/rywr2hzmjg/1650666373818/image.png)

---

That's it! Diode Drive is installed and active on your system.

**NEXT STEP:** [**Create an Account**](https://app.docs.diode.io/docs/navigating/getting-started/)

---

<u>Getting-started articles:</u>

* <a href="https://app.docs.diode.io/docs/" target="_blank" rel="noopener"><strong>Install Diode Drive</strong></a>
* <a href="https://app.docs.diode.io/docs/navigating/getting-started/" target="_blank" rel="noopener"><strong>Create an Account</strong></a>
* <a href="https://app.docs.diode.io/docs/navigating/create-a-zone/" target="_blank" rel="noopener"><strong>Create a Zone</strong></a>
* <a href="https://app.docs.diode.io/docs/navigating/linked-devices/" target="_blank" rel="noopener"><strong>Link additional Devices to your Account</strong></a>
* <a href="https://app.docs.diode.io/docs/navigating/share-a-file-or-folder-via-web-browser/" target="_blank" rel="noopener"><strong>Share files or folders via web browser</strong></a>
* <a href="https://app.docs.diode.io/docs/navigating/add-a-team-member-or-additional-device/" target="_blank" rel="noopener"><strong>Invite other team members to your Zone</strong></a>
* <a href="https://app.docs.diode.io/docs/navigating/backup-your-confidential-files/" target="_blank" rel="noopener"><strong>Backup and persistently host your files</strong></a>
* <a href="https://app.docs.diode.io/docs/navigating/join-a-zone-by-invite-code/" target="_blank" rel="noopener"><strong>Join a Zone via Invite Code</strong></a>

  &nbsp;

  &nbsp;

---

&nbsp;