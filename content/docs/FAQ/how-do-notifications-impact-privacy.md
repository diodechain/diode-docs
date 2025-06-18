---
_schema: default
title: How do notifications impact privacy?
nav_title: How do notifications impact privacy?
nav_section: FAQ
weight: 20012
draft: false
---
New messages and invitations in Diode create system-level notifications.  Please read below to understand the privacy implications of notifications.

There are two types of notifications Diode creates:

1. App notifications
2. Push notifications

### App notifications

App notifications are created when you are running the application and a new message arrives, but you are not viewing the chat it arrived for.  In this case, your app will raise a notification on your phone or computer to get your attention - clicking the notification will take you to the message.

* You must use your operating system's notification controls to turn this feature off.
* App notifications are created by your device and remain local to your device.
* App notifications contain the Zone name, the sender name, and the message.

App notifications are considered "self custody" notifications - you are in full control of meta data exposure, if any.

### Push notifications

Push notifications are created by the sender's device in order to send you a notification even if your app is not running.  In this case, Google or Apple will send out a notification that appears on your phone - clicking the notification will open the app and view the message.

* You are prompted to choose whether you want to enable Push notifications when first configuring a new phone.  You can disable this feature at a profile level (all Zones) in your profile settings.
* These notifications are sent from the sender's app to the Diode push notification server, where they are then relayed to the Google or Apple push servers for distribution to your phone.
* Push notifications contain an encrypted blob consisting of the sender name and the message.  Push notification contents cannot be read by either the Diode push notification server or the Google/Apple push servers.  They are encrypted by the sender, and decrypted real-time on your device (end to end encrypted).
* The push token used by Google/Apply push servers is associated with your phone (that is how Google/Apple know where to send the notification).  Therefore, enabling push notifications has a liability similar to that of associating a phone number with your Diode profile.

Push notifications are **not** considered fully "self custody" notifications. Read more below.

#### Why should you enable Push notifications?

You should enable Push notifications if you are comfortable with the privacy implications and want to receive message alerts even if your app is closed or has exited.

#### Why should you not enable Push notifications?

You should not enable Push notifications if you are otherwise taking measures to ensure your account is pseudo-anonymous.

#### What steps does Diode take to protect my account?

Diode end-to-end encrypts all Push notification content, and encrypts "push token" information on Team Member devices.

#### If I enable Push notifications, can I still collaborate securely?

Yes, your collaborations are all still end-to-end encrypted.  However, push notifications leave a breadcrumb that could theoretically be used to link your Diode profile to your non-Diode digital profile.