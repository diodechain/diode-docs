---
_schema: default
title: Diode Drive Chat Commands
nav_title: Chat Commands
nav_section: Navigating
weight: 217
draft: false
---
In a Diode Drive channel, messages that start with "/" are called chat commands. These chat commands can perform various functions and display helpful information.

Chat commands and the automated responses to them don't send any data to the Channel members, only the sender can see them, and they disappear after leaving the page.

### **Chat Commands**

#### **`/sysconfig remote-api COMMAND`**

&nbsp;

<table><thead><tr><th><p><strong>COMMAND</strong></p></th><th><p><strong>Description</strong></p></th></tr></thead><tbody><tr><td><p>version</p></td><td><p>display the current Diode Drive API version</p></td></tr><tr><td><p>enable</p></td><td><p>enable the Diode Drive API on this device</p></td></tr><tr><td><p>disable</p></td><td><p>disable the Diode Drive API on this device</p></td></tr><tr><td><p>status</p></td><td><p>display status of the Diode Drive API on this device</p></td></tr><tr><td><p>generate-token</p></td><td><p>generate a new bearer token (this replaces any previous token)</p></td></tr><tr><td><p>view-token</p></td><td><p>view the current bearer token (this is a secret)</p></td></tr><tr><td><p>template</p></td><td><p>display a curl template for the "send_message" API method</p></td></tr><tr><td><p>example</p></td><td><p>auto-populate a curl command for the "send_message" API method with the current "channel_id", "zone id", and "device_address" of the channel/zone/device this command was run on - the bearer token will still need manually filled in</p></td></tr></tbody></table>

#### **`/info`**

Outputs the following values:

* ddrive\_version
* device\_address
* zone\_domain
* zone\_id
* channel\_id