---
_schema: default
title: Uninstall
nav_title: Uninstall
nav_section: Installation
weight: 3
draft: false
---
To fully uninstall Diode, follow the instructions below corresponding to your operating system ([Windows](#windows), [MacOS](#macos), [Linux](#linux)).

### **Windows**

1. Remove Diode Collab
   * Click "Uninstall" from the Diode Collab start menu program group

     OR

   * open an explorer window (Win-E) and go to C:\\Program Files\\Diode Drive\\ and run the "Uninstall.exe" from the Diode Collab folder.
2. Remove your Diode Profile

   > **WARNING:** If you have not created a backup of your account, you will lose your username forever

   If you are certain you want to remove your Diode Profile:
   1. Open an explorer window and go to your user's home folder (e.g. C:\\Users\\myusername\\)
   2. Locate the ".config" folder and go into it
   3. Locate the "ddrive" folder and delete it
3. Remove your Zones folder

   > **WARNING:** Your Zones folder may contain the files/information you were working on in Diode - you may or may not want to delete these

   If you are certain you want to remove your Zones folder:
   1. Open an explorer window and go to your user's home folder (e.g. C:\\Users\\myusername\\)
   2. Locate the "Zones" folder and delete it

### **MacOS**

1. Remove the Diode App
   1. Open the Applications folder in Finder
   2. Move the "dDrive" or "Diode Drive" application in the Applications folder to the Trash (or delete it)
2. Remove your Diode Profile

   > **WARNING:** If you have not created a backup of your account, you will lose your username forever

   If you are certain you want to remove your Diode Profile:
   1. Open a terminal window
   2. Type "rm -r ~/.config/ddrive"
3. Remove your Zones folder

   > **WARNING:** Your Zones folder may contain the files/information you were working on in Diode - you may or may not want to delete these.

   If you are certain you want to remove your Zones folder:
   1. Open a terminal window
   2. Type "rm -r ~/Zones"

### **Linux**

1. Remove the Diode App

   Remove the "dDrive" installation directory (by default, this is located at ~/dDrive)
   * Do this from the File Manager

     OR

   * Open a terminal window
   * Type "rm -r ~/dDrive"
2. Remove your Diode Profile

   > **WARNING:** If you have not created a backup of your account, you will lose your username forever

   If you are certain you want to remove your Diode Profile:
   1. Open a terminal window
   2. Type "rm -r ~/.config/ddrive"
3. Remove your Zones folder

   > **WARNING:** Your Zones folder may contain the files/information you were working on in Diode - you may or may not want to delete these.

   If you are certain you want to remove your Zones folder:
   1. Open a terminal window
   2. Type "rm -r ~/Zones"

###