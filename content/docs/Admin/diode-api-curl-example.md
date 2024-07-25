---
_schema: default
title: Diode API Curl Example  (send_message)
nav_title: Diode API Curl
nav_section: IT Admin
weight: 305
draft: false
---
### **Diode API Curl Example**

<a href="https://diode.io/solutions/app/" target="_blank" rel="noopener"><strong>Diode Drive</strong></a> version 1.9.3 introduced version 1 of the Diode Drive API. The Diode Drive API implements JSON-RPC and authenticates via a bearer token. It can be used to send chat messages programmatically and to do other Web3 - Web2 integrations. See the full API documentation <a href="https://app.docs.diode.io/docs/admin/diode-api-docs/" target="_blank" rel="noopener"><strong>here</strong></a>.

The API is device-based, and therefore grants access to send messages to all Zone and Channels (including DM's) that the device has access to. Reading incoming messages is not yet supported.

The following steps show how to call the API to send a Diode Drive message from a remote command line terminal using <a href="https://github.com/curl/curl" target="_blank" rel="noopener"><strong>curl</strong></a>.

1. Check to make sure Diode Drive is at least at version 1.9.3. To check the version number, click the username in the top right of Diode Drive, then click "About" from the drop down. On that about page, the number under "Patch:" is the effective version number. If Diode Drive is not on at least version 1.9.3, it must be updated to such before the following steps will work.
2. To enable the API on a device, navigate to any Channel in any Zone and type `/sysconfig remote-api enable` and send the message. Messages that start with "/" are chat commands; the chat commands and the automated responses to them don't send any data to the channel members, only the sender can see them, and they disappear after leaving the page. After sending the command a message will show that the API has been enabled.
3. Next, a bearer token that will be used to authenticate API calls must be generated. This token must be kept secret as it allows whoever has it to send messages on behalf of the device. To generate a new token, type `/sysconfig remote-api generate-token` and send the message.
4. After the token has been generated, it can be viewed by typing `/sysconfig remote-api view-token` and sending the message. The token will be printed to the screen. Write this token down in a secure place.
5. Now that the API is enabled and token is generated, it's time to decide which Channel the API call should send a message to, it can be any Channel (including DMs). Once in the selected channel, type `/sysconfig remote-api template` and send the message to see how the curl command will work. The output contains placeholders for the bearer\_token, zone\_id, channel\_id, message\_text, and device\_address. The bearer\_token was already obtained in the previous step and the message\_text is arbitrary. The zone\_id, channel\_id, and device\_address can be manually obtained by typing and sending `/info` to the Channel, however, it is easier in this case to auto-populate them into the curl template by sending `/sysconfig remote-api example` to the Channel. Remember that this be done inside the Channel that the API call will send a message to.
6. Finally, copy and paste the populated curl example into a command line terminal (the terminal could be on the same device or a difference device) and click enter to send (this example uses the diode.link gateway to forward the connection, so make sure all devices involved have internet access). The API will send back info to the terminal to show the status of the API call; if there is an error, it will explain what went wrong. If the API call is successful, the message will be visible as sent inside the specified Diode Drive Channel.

**Troubleshooting**

* If the chat commands aren't generating the expected output, double check that they are typed correctly and that Diode Drive is at least version 1.9.3.
* If the curl command renders a lot of HTML text in the terminal, make sure the device\_address is correct, that the device is online, and that there is internet connection.
* If the API call returned success, the message isn't shown in the Diode Drive Channel, try navigating away from the channel and back again.

&nbsp;

---

&nbsp;