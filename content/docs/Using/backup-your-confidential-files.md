---
_schema: default
title: Backup Your Confidential Files
nav_title: Backup  Files
nav_section: Using
weight: 205
draft: false
---
Diode Drive can be used to keep an offsite backup of your files up to date at all times, no matter where you are in the world, without storing your files in the cloud. If anything should happen to your device, your files will be safe.

The way this works is by adding a second device to your Zone - the second device keeps a mirror of all the files stored in your Zone.

These instructions assume that you've already <a href="https://app.docs.diode.io/docs/" target="_blank" rel="noopener"><strong>setup Diode Drive</strong></a> on your main system, and have already <a href="https://app.docs.diode.io/docs/using/create-a-zone/" target="_blank" rel="noopener"><strong>created a Zone</strong></a> that you want to back up.

**1\. Setup Diode Drive on a backup device**

In this example, we'll add a Raspberry Pi device to our Zone to act as an always-on, anywhere, 256bit E2E encrypted, backup system. Instead of a Raspberry Pi, you could use another computer, a server, or even an old cell phone (assuming OS is sufficiently current).

<a href="https://app.docs.diode.io/raspberry-pi/use-your-raspberry-pi-as-a-remote-file-server-backup-device/" target="_blank" rel="noopener"><strong>Setup your Raspberry Pi</strong></a>, plug in a large USB drive/thumb drive to use as the storage device, and <a href="https://app.docs.diode.io/docs/" target="_blank" rel="noopener"><strong>install / start Diode Drive on the device</strong></a>.

In the global settings area, set the "Default Location for New Zones" to be the large USB drive you plugged in.

![](/uploads/image-62.png)

**2\. Add the backup device to your Zone**

You can either set the backup device up as a separate Account, or you can <a href="https://app.docs.diode.io/docs/using/linked-devices/" target="_blank" rel="noopener"><strong>link it to your Account.</strong></a> Because a Linked Device has all the same permissions as other devices on your Account, we recommend setting the backup device up with its own Account - these instructions will assume it is using its own Account.

Give the device its own <a href="https://app.docs.diode.io/docs/using/getting-started/" target="_blank" rel="noopener"><strong>Account</strong></a>.

From your main system, use the invite mechanism to<a href="https://app.docs.diode.io/docs/using/add-a-team-member-or-additional-device/" target="_blank" rel="noopener"><strong> invite the backup device's account</strong></a> to your Zone.

Accept the invitation on the backup device. Zone files will now be synchronized automatically to the back up device.

**3\. Enable Deleted Files Backup**

Even if your Zone's subscription plan doesn't support the Deleted Files Backup feature, the backup device will still keep a copy of your files at all times in case your main device is lost.

If the Zone has the right <a href="https://app.docs.diode.io/docs/features/pricing-and-plans/" target="_blank" rel="noopener"><strong>subscription plan</strong></a>, you can enable the "Deleted Files Backup" feature on the device. This will ensure that any accidental file deletions can be recovered. This is useful if your Zone has multiple Team Members - if one of them accidentally deletes a file, the Deleted Files Backup will archive the deleted file instead of permanently deleting it. This setting is under the Zone Setting page:

![](/uploads/image-63.png)

Click the setting to view information about the backup folder. You can click the open icon to open the folder on your device.

![](/uploads/image-64.png)

**4\. Advantages for "availability"**

Your backup device not only keeps a copy of your files, it also acts as an "availability" device.

When your main system is offline, the device will synchronize updates from other Team Members, and will also serve files/folders for web links and other Zone functions. This "availability" functionality is especially important when Team Members are operating in different time zones - the backup device keeps all intermittently connected Team Members synchronized.

---

<u>Getting-started articles:</u>

* <a href="https://app.docs.diode.io/docs/" target="_blank" rel="noopener"><strong>Install Diode Drive</strong></a>
* <a href="https://app.docs.diode.io/docs/using/getting-started/" target="_blank" rel="noopener"><strong>Create an Account</strong></a>
* <a href="https://app.docs.diode.io/docs/using/create-a-zone/" target="_blank" rel="noopener"><strong>Create a Zone</strong></a>
* <a href="https://app.docs.diode.io/docs/using/linked-devices/" target="_blank" rel="noopener"><strong>Link additional Devices to your Account</strong></a>
* <a href="https://app.docs.diode.io/docs/using/share-a-file-or-folder-via-web-browser/" target="_blank" rel="noopener"><strong>Share files or folders via web browser</strong></a>
* <a href="https://app.docs.diode.io/docs/using/add-a-team-member-or-additional-device/" target="_blank" rel="noopener"><strong>Invite other team members to your Zone</strong></a>
* <a href="https://app.docs.diode.io/docs/using/backup-your-confidential-files/" target="_blank" rel="noopener"><strong>Backup and persistently host your files</strong></a>
* <a href="https://app.docs.diode.io/docs/using/join-a-zone-by-invite-code/" target="_blank" rel="noopener"><strong>Join a Zone via Invite Code</strong></a>

  &nbsp;

  &nbsp;