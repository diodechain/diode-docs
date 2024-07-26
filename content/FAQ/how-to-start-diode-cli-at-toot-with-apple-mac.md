---
_schema: default
title: How To Start Diode CLI at Toot With Apple Mac
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
In this tutorial we install the Diode CLI so that it will run silently at boot on a Mac OS computer.

By running the Diode CLI at boot, the computer can publish certain network resources securely (via the Diode Network) so that they can be accessed remotely.

1\. Configure the Automator application to run the Diode CLI in a shell script

* Start Automator.app
* Go to File -&gt; New and select "Application"
* Click "Show library" in the toolbar (if hidden)
* Add "Run shell script" (from the Actions/Utilities)
* Copy-and-paste your script into the window - here is an example:

`source ~/.bash_profile`

`diode publish -public 80:80`

* Click "Run" to test it
* Save it somewhere: a file called diode.app will be created

2\. Configure the automator app to run on startup

* Depending on your MacOSX version:
  * Old versions: Go to System Preferences → Accounts → Login items, or
  * New version: Go to System Preferences → Users and Groups → Login items (top right);
* Add your newly-created diode.app

3\. Verify it is running

* Log off, log back in, and you should be done. 😉
* Run `ps aux | grep diode` to verify it is running

---

&nbsp;