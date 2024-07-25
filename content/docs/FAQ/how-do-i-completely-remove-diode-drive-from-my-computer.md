---
_schema: default
title: How Do I Completely Remove Diode Drive From My Computer?
nav_title: 'How Do I Remove Diode Drive? '
nav_section: FAQ
weight: 20009
draft: false
---
### **MacOS**

1\. Remove the Diode App

* Open the Applications folder in Finder
* Move the "dDrive" or "Diode Drive" application in the Applications folder to the Trash (or delete it)

2\. Remove your Diode Profile

**WARNING:** If you have not created a backup of your account, you will lose your username forever

* If you are certain you want to remove your Diode Profile:
  * Open a terminal window
  * Type "rm -r ~/.config/ddrive"

3\. Remove your Zones folder

**WARNING:** Your Zones folder may contain the files/information you were working on in Diode - you may or may not want to delete these.

* If you are certain you want to remove your Zones folder:
  * Open a terminal window
  * Type "rm -r ~/Zones"

### **Linux**

1\. Remove the Diode App

* Remove the "dDrive" installation directory (by default, this is located at ~/dDrive)
  * Do this from the File Manager

  OR
  * Open a terminal window
  * Type "rm -r ~/dDrive"

2\. Remove your Diode Profile

**WARNING:** If you have not created a backup of your account, you will lose your username forever

* If you are certain you want to remove your Diode Profile:
  * Open a terminal window
  * Type "rm -r ~/.config/ddrive"

3\. Remove your Zones folder

**WARNING:** Your Zones folder may contain the files/information you were working on in Diode - you may or may not want to delete these.

* If you are certain you want to remove your Zones folder:
  * Open a terminal window
  * Type "rm -r ~/Zones"

### **Windows**

1\. Remove the Diode App

* Click "Uninstall" from the Diode Drive start menu program group

OR

* open an explorer window (Win-E) and go to C:\\Program Files\\Diode Drive\\ and run the "Uninstall.exe" from the Diode Drive folder.

2\. Remove your Diode Profile

**WARNING:** If you have not created a backup of your account, you will lose your username forever

* Open an explorer window and go to your user's home folder (e.g. C:\\Users\\myusername\\)
  * Locate the ".config" folder and go into it
  * Locate the "ddrive" folder and delete it

3\. Remove your Zones folder

**WARNING:** Your Zones folder may contain the files/information you were working on in Diode - you may or may not want to delete these.

* Open an explorer window and go to your user's home folder (e.g. C:\\Users\\myusername\\)
  * Locate the "Zones" folder and delete it

&nbsp;

---

&nbsp;