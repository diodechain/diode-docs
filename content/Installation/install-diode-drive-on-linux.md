---
_schema: default
title: Install Diode Collab on Linux
nav_title:
SEO_options:
  title: Diode App Secure Messenger
  image:
  description:
draft: false
---
Follow the three steps below to get up and running on Linux (Raspberry Pi/ARM shown below).

---

**1\. Download**

[**Download Diode Collab**](https://diode.io/download/) \*\* \*\* for Linux - pay attention to the Linux variant (x86, ARM, 32/64 bit) to ensure you download the right one for your system.

**2\. Install and run Diode Collab**

Set the File Permissions for the downloaded .run file to include "Execute".

![](/uploads/image-110.png)

Open a terminal window and run the installer - it will extract to ~/dDrive

![](/uploads/image-111.png)

You can then either run it from a terminal window from the ~/dDrive folder with: `./dDrive start_iex` , or click the "Diode Drive Decentralized Storage" icon from the UI and select "Execute".

![](/uploads/image-112.png)

Some Linux installations <a href="https://github.com/diodechain/diode_drive_feedback/issues/14" target="_blank" rel="noopener"><strong>have a bug with the UI and file updates</strong></a> (last checked: March 15, 2021)

If your installation is not automatically synchronizing file changes, install the "inotify-tools" package via the command line:

`sudo apt install inotify-tools`

If the user interface doesn't load, try installing the topicons extension from <a href="https://extensions.gnome.org/extension/495/topicons/" target="_blank" rel="noopener"><strong>https://extensions.gnome.org/extension/495/topicons/</strong></a>

Recent (as of June 2021) Raspberry Pi Linux OS (Raspbian) no longer packages <a href="https://packages.debian.org/search?keywords=libglu1-mesa" target="_blank" rel="noopener"><strong>an OpenGL driver</strong></a> required by Diode Collab. If Diode Collab does not start on your Raspberry Pi, install the drive from a terminal window: `sudo apt install libglu1-mesa`

**3\. Verify Diode Collab is running**

When Diode Collab starts up, it will load as a small orange icon in the task bar:

![](/uploads/image-113.png)

Clicking the orange Diode Collab icon will drop-down / pop-up menu options. Click "Open" to open the app.

![](/uploads/image-114.png)

---

That's it! Diode Collab is installed and active on your system.

**NEXT STEP:** [**Create an Account**](https://app.docs.diode.io/docs/using/getting-started/)

---

<u>Getting-started articles:</u>

* <a href="https://app.docs.diode.io/docs/" target="_blank" rel="noopener"><strong>Install Diode Collab</strong></a>
* <a href="https://app.docs.diode.io/docs/using/getting-started/" target="_blank" rel="noopener"><strong>Create an Account</strong></a>
* <a href="https://app.docs.diode.io/docs/using/create-a-zone/" target="_blank" rel="noopener"><strong>Create a Zone</strong></a>
* <a href="https://app.docs.diode.io/docs/using/linked-devices/" target="_blank" rel="noopener"><strong>Link additional Devices to your Account</strong></a>
* <a href="https://app.docs.diode.io/docs/using/share-a-file-or-folder-via-web-browser/" target="_blank" rel="noopener"><strong>Share files or folders via web browser</strong></a>
* <a href="https://app.docs.diode.io/docs/using/add-a-team-member-or-additional-device/" target="_blank" rel="noopener"><strong>Invite other team members to your Zone</strong></a>
* <a href="https://app.docs.diode.io/docs/using/backup-your-confidential-files/" target="_blank" rel="noopener"><strong>Backup and persistently host your files</strong></a>
* <a href="https://app.docs.diode.io/docs/using/join-a-zone-by-invite-code/" target="_blank" rel="noopener"><strong>Join a Zone via Invite Code</strong></a>

  &nbsp;

---