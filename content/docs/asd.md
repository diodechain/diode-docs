---
_schema: default
title: asD
nav_title: UninstadsaSDall
nav_section: Installation
weight: 3
draft: false
---
Follow the three steps below to get up and running on Linux (Raspberry Pi/ARM shown below).

---

1. ##### **Download**

[**Download Diode Drive**](https://diode.io/resources/download) for Linux - pay attention to the Linux variant (x86, ARM, 32/64 bit) to ensure you download the right one for your system.

1. ##### **Install and run Diode Drive**

![](/uploads/image-8.png)

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

1. ##### **Verify Diode Drive is running**

When Diode Drive starts up, it will load as a small orange icon in the task bar:

![](https://files.helpdocs.io/qwk5dmv7m8/articles/d3eguu0pem/1615794188005/image.png)

Clicking the orange Diode Drive icon will drop-down / pop-up menu options. Click "Open" to open the app.