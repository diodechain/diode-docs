---
_schema: default
title: How Do I Change My Diode Drive Account / Profile?
nav_title: How Do I Change My Diode Drive Profile?
nav_section: FAQ
weight: 20004
draft: false
---
When signing up for Diode Drive as a new user, the first thing you configure is your Account Name - this Account Name is globally unique and allows others using Diode Drive to know with whom they are interacting. Of course, although your Account Name could be your real name, it can also be any other unique combination of letters and characters.

Sometimes, after configuring an initial Account Name, you may want to configure a new Account Name and use the new name as your Diode Drive handle. Today (January 2022), you can accomplish this, but requires a little bit of technical expertise.

The overall idea is that Diode Drive will use whatever valid profile exists in a folder called "ddrive" in your ".config" folder. Therefore, you can simply close Diode Drive, move the existing profile to a different folder, and rename another profile's folder to "ddrive" located in the ".config" folder, and restart Diode Drive.

Read below for more detail (instructions provided for MacOS/Linux).

WARNING: These instructions use the terminal window and involve moving folders around on your system. If you don't feel comfortable in that general environment, and make a mistake, it is possible that you will lose access to your account.

WARNING: Please make sure to backup your account code before taking these steps so you can recover your account if you make a mistake. To backup your account code, click the Diode Drive icon in the top left, got to the Profile menu option, and print out your backup code.

**On MacOS and Linux**

![](/uploads/image-13.png)

![](/uploads/image-14.png)

* **MAKE SURE YOUR** <a href="https://app.docs.diode.io/docs/navigating/diode-drive-backup-codes/" target="_blank" rel="noopener"><strong>ACCOUNT BACKUP CODE </strong></a>**IS SAVED SOMEWHERE SAFE**
* Quit Diode Drive (must click "Quit" in the task bar menu and then click "Yes" in the dialog that says "Do you want to exit Diode Drive?")

![](/uploads/image-15.png)

* Open a terminal window
* Move your existing Diode Drive configuration directory to a backup.

mv ~/.config/ddrive ~/.config/ddrive-backupoldaccount

The "ddrive-backupoldaccount" part can be named anything you want - you may want to name it something much more memorable. For example, if your account name is "acme", you may want to rename it as "ddrive-acme" so you can remember the folder contains the profile for your "acme" account.

* Start Diode Drive
* Enter a new Account Name - this is now your operating Diode Drive profile!

If desired, once you've created your new account, you can switch the Diode Drive profile folder back to the one for your old account and then invite your new account to the Zones that you own so that you have access to all your information and team members. You could also transfer ownership of a Zone to the new account.<br><br>To switch back to your old account, simply close Diode Drive and use the terminal to move (mv) the folder names so that your new account is named something \_other\_ than "ddrive" and your old account folder is renamed back to "ddrive".