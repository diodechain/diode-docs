---
_schema: default
title: Tunneled (P2P) Dashboards
nav_title: Tunneled (P2P) Dashboards
nav_section: Using
weight: 222
draft: false
---
A common IT, OT, and IoT need is for team members to securely access a remote dashboard for a piece of equipment (machine or server).

In Diode Collab, Team Members can access a remote dashboard using a Bookmark. A Team Member's self-custody identity, or just their membership in the Zone, gives them end-to-end encrypted access to the dashboard.

This guide walks through an example of setting up Bookmark to launch a secure remote dashboard. It uses the following hardware and software:

* **Device:** Raspberry Pi 4 (Using Raspbian 32 bit Bullseye)
* **Dashboard:** <a href="https://cockpit-project.org/" target="_blank" rel="noopener"><strong>Cockpit</strong></a>
* **Diode CLI:** v0.13.5
* **Diode Collab:** v1.9.4

NOTE: If you have equipment that already has a dashboard available on its Local Area Network, you can use the $99 <a href="https://diode.io/solutions/vault" target="_blank" rel="noopener"><strong>Vault Mini</strong></a> as a gateway to establish a P2P/E2EE link to the dashboard (instead running the Diode CLI on the equipment itself).

If you just need to remotely SSH into a device, <a href="https://cli.docs.diode.io/docs/using/remote-ssh/" target="_blank" rel="noopener"><strong>see here</strong></a>.

### **Device Setup**

Let's assume you've been able to get your Raspberry Pi up and running and connected to SSH / VNC, or to a keyboard/mouse/monitor.

**1\.** <a href="https://cockpit-project.org/running.html" target="_blank" rel="noopener"><strong>Install Cockpit</strong></a>

* Verify it is working by opening a browser on your Pi and going to [http://localhost:9090](http://localhost:9090)
  * You should see a login screen - you can type your Pi's username / password there to load Cockpit

![](/uploads/image-157.png)

**2\.** <a href="https://cli.docs.diode.io/docs/" target="_blank" rel="noopener"><strong>Install the Diode CLI</strong></a> (recommend using the curl command)

* Verify it is working by opening a terminal window and typing "diode time"
  * You should see output with "Minimum Time" and "Maximum Time" like this:

![](/uploads/image-158.png)

* Copy your Client address - you will need this in the App Setup below
  * For this example, let's pretend the Client address is 0xa5c8ee625db628b493b1d084afe25e962a570cd9

**3\.** <a href="https://cli.docs.diode.io/raspberry-pi/start-diode-on-boot/" target="_blank" rel="noopener"><strong>Configure the Diode CLI to run at startup</strong></a>

* After you've followed the instructions in that <a href="https://cli.docs.diode.io/raspberry-pi/start-diode-on-boot/" target="_blank" rel="noopener"><strong>guide</strong></a>, you'll want to further modify the diode.service file to publish the Cockpit port
* Change this line: `ExecStart=/home/pi/opt/diode/diode publish -public 22:22,80:80,3030:3030`
  * To: `ExecStart=/home/pi/opt/diode/diode publish -public 22:22,9090:80`
    * That publishes your localhost port 9090 to your Web3 Client address' port 80
    * Don't forget to change the `pi` to your Raspberry Pi's actual username, if you used a different username
* We will circle back to this step later on to make this a private linkage, instead of a public linkage (see Setup Restricted Access below)

### **Collab Setup**

Let's assume you are already running the <a href="https://diode.io/download#app" target="_blank" rel="noopener"><strong>Diode Collab</strong></a> and <a href="https://app.docs.diode.io/docs/using/create-a-zone/" target="_blank" rel="noopener"><strong>have a Zone</strong></a> that you own and can configure. Additionally, we will use the Brave Browser to load the tunneled dashboard - you'll need to be on a desktop/laptop system and <a href="https://brave.com/" target="_blank" rel="noopener"><strong>install Brave</strong></a> (see <a href="https://app.docs.diode.io/docs/faq/why-does-the-diode-app-use-the-brave-browser-for-some-bookmarks/" target="_blank" rel="noopener"><strong>here for an FAQ</strong></a> on why we are using Brave).

**1\.** <a href="https://app.docs.diode.io/docs/features/diode-bookmarks/" target="_blank" rel="noopener"><strong>Make a Web3 Link Bookmark to your Client Address</strong></a>

* Type: Web3 Link
* Browser: Brave (Beta) (for now: 2024-02)
* Address: your Client address from step 2 in Device Setup (with a ".diode" suffix)
  * e.g. 0xa5c8ee625db628b493b1d084afe25e962a570cd9.diode
* Click "Save" - the Bookmark should immediately show up in the Quick Access Bar.

2\. Try it!

* Click the bookmark - a message should flash across the top of your screen saying "Launching Brave" - the Brave Browser should launch and the login to your Cockpit dashboard should be displayed!
* Use your Pi's username and password to login - you should then see a screen that looks the same as the screen you saw on the localhost browser in Device Setup step 1:

![](/uploads/image-159.png)

### **Setup Restricted Access**

For this step, you'll need to modify the Device settings to restrict access to only your App system.

1\. Find your App's Device ID

* Every endpoint in the Diode environment has a unique identifier/address called a "Client address" or a "Device ID" - you found the Client address for your dashboard device in Step 2 of Device Setup above. Now we need to find the same identifier for your desktop/laptop device you are running Collab on.
* In Diode Collab, click the profile picture/circle in the upper right corner and select "About"
* In the About page, find the Device ID listed under the word "Device:"
  * For this example, we'll pretend your App's Device ID is 0xebf25e5b07abd13606a7e49be693b0031d83f2b5

![](/uploads/image-160.png)

2\. Change your diode.service file on your device to privately publish ONLY to your App's Device ID

* Open a terminal on your device (or SSH into it)
* Modify the diode.service file by typing `sudo nano /etc/systemd/system/diode.service`
* That will open the Nano editor. In the editor, find the line you edited in Device Setup step 3:
  * `ExecStart=/home/pi/opt/diode/diode publish -public 22:22,9090:80`
    * And change it to:
      * `ExecStart=/home/pi/opt/diode/diode publish -public 22:22 -private 9090:80,0xebf25e5b07abd13606a7e49be693b0031d83f2b5`
    * That will publish your SSH port still publicly via Web3 and your Cockpit dashboard private to \_only\_ your App's Device ID
    * Of course, modify the `0xeb...b5` to be your App's actual Device ID

3\. Try it!

* In Collab, click the bookmark - the Brave Browser should launch and the login to your Cockpit dashboard should be displayed!
* Invite another user / device to your Zone (or setup a second profile) to verify they cannot access the dashboard - their App's Device ID will be different and will be blocked
  * Have the other user try to load the dashboard by clicking on the bookmark. They will get a screen that looks like below (the network automatically blocks access from the device to anyone NOT in the allow list):

![](/uploads/image-161.png)

4\. Explore more!

* If you'd like your whole Zone to have access to the dashboard, or a sub-group from within the Zone, you can use private publishing via domain. Instead of specifying a Device ID / Client address in the private list, you instead specify a group that has been <a href="https://network.docs.diode.io/docs/faq/what-is-bns/" target="_blank" rel="noopener"><strong>registered as a BNS name</strong></a>.
* A BNS name (aka "Domain") can be associated with as many Device IDs as you like. Diode Collab's Network area provides an easy way to create and configure a Domain.
* The diode.service line could be modified to be, for example:
  * `ExecStart=/home/pi/opt/diode/diode publish -public 22:22 -private 9090:80,pi-authorization-01`
  * Where "pi-authorization-01" is a Domain that has an number of Device IDs associated with it