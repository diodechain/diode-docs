---
_schema: default
title: Diode API Docs
nav_title: Diode API Docs
nav_section: IT Admin
weight: 307
draft: false
---
### **Enabling the Diode API**

This API runs on every Diode app instance, and is disabled by default.

The API is device-wide. To enable the API on your device:

1. Open the Diode app (version 1.10.7 or later)
2. Navigate to any Zone and any Channel, it doesn't matter which Channel
3. Send the following chat command to the Channel: `/sysconfig remote-api enable`.

Messages that start with "/" are [**chat commands**](https://app.docs.diode.io/docs/navigating/diode-drive-chat-commands/). Chat commands and the automated responses to them don't send any data to the channel members, only the sender can see them, and they disappear after leaving the page.

1. Next, a token will need generated. To generate a token, send this chat command: `/sysconfig remote-api generate-token`
2. To view the newly generated token, use this command: `/sysconfig remote-api view-token`

WARNING: When your API is enabled, anyone with this token can perform API functions on your behalf. Keep it a secret.

1. The API is now enabled device-wide and a token has been obtained. The device is now ready to accept API requests by whoever has the token. Here are some other helpful commands:
   1. Regenerate Token (Note: This will replace the previous token):<br>`/sysconfig remote-api generate-token`
   2. Disable API:<br>`/sysconfig remote-api disable`
   3. API Status:<br>`/sysconfig remote-api status`
   4. API Version:<br>`/sysconfig remote-api version`

### **Calling the API (HTTP)**

A valid request is an HTTP POST request containing the following two headers and a <a href="https://www.jsonrpc.org/specification#response_object" target="_blank" rel="noopener"><strong>JSON-RPC 2.0</strong></a> payload.

There are two ways to reach the API endpoint:

* Via the Diode Web2 Gateway (most convenient, use anywhere):<br>`https://<device_address>.diode.link/api/json_rpc`
* Direct via Web3 (most secure, requires web3 pipe between caller and device where the API is enabled):<br>`http://<device_address>.diode/api/json_rpc`

The "device\_address" can be found on the "About" page in Diode Drive, or by sending the `/info` chat command to any Channel.

#### **Headers:**

`Content-Type: application/json`

`Authorization: Bearer <bearer_token>`

#### **JSON-RPC 2.0 Payload Format:**

`{"jsonrpc":"2.0","method":"<method>","params":["<param1>", "<param2>", ..., <paramN>], "id":N}`

##### **Curl Example:**

```
curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer <bearer_token>" -d '{"jsonrpc":"2.0","method":"<method>","params":["<param1>", "<param2>", ..., <paramN>], "id":N}' https://<device_address>.diode.link/api/json_rpc
```

You can use the following chat commands to get curl templates for the "send\_message" method. Please note that the second command will auto-populate the "zone\_id" and "channel\_id" for the specific channel the command is sent to; the "device\_address" will also be auto-populated.<br><br><code>/sysconfig remote-api template<br />/sysconfig remote-api example</code>

### **Calling the API (WebSocket)**

To use advanced methods such as "subscribe\_channel", the WebSocket API can be used. Once connected, the WebSocket payload must contain a valid <a href="https://www.jsonrpc.org/specification#response_object" target="_blank" rel="noopener"><strong>JSON-RPC 2.0</strong></a> method call. Authentication is done via the "authenticate" method when calling the WebSocket API . Once authenticated successfully, any method can be called.

Like the HTTP API, there are two ways to reach the WebSockets API endpoint:

* Via the Diode Web2 Gateway (most convenient, use anywhere):<br>`ws://<device_address>.diode.link/api/json_rpc/ws`
* Direct via Web3 (most secure, requires web3 pipe between caller and device where the API is enabled):<br>`ws://<device_address>.diode/api/json_rpc/ws`

&nbsp;

Here is an <a href="https://support.diode.io/article/o77e2w21lq" target="_blank" rel="noopener"><strong>example of a python script</strong></a> calling the API via WebSockets.

### **API Methods**

Some of these methods required "zone\_id" and "channel\_id" parameters. To obtain these values, navigate to the target Channel in the Diode App and send the `/info` chat command to that Channel. The "zone\_id" and "channel\_id" will be printed out, amongst other helpful information. Passing a <a href="https://support.diode.io/article/5nsoxvhug1-what-is-bns" target="_blank" rel="noopener"><strong>bns name</strong></a> (such as a Diode username) as the "channel\_id" is also valid.

#### **"ping"**

##### **Call**

```
{"jsonrpc":"2.0","method":"ping","id":1}
```

##### **Success Response**

```
{"jsonrpc":"2.0","result":"The RPC endpoint has been successfully contacted.","id":1}
```

#### **"send\_message"**

##### **Call**

```
{"jsonrpc":"2.0","method":"send_message","params":["<zone_id>", "<channel_id>", "<message_text>"], "id":1}
```

##### **Success Response**

```
{"jsonrpc":"2.0","result":"Message sent","id":1}
```

#### **"subscribe\_channel" (WebSocket only)**

##### **Call**

```
{"jsonrpc":"2.0","method":"subscribe_channel","params":["<zone_id>", "<channel_id>"], "id":1}
```

##### **Success Response**

```
{"jsonrpc":"2.0","result":"Subscribed","id":1}
```

##### **Incoming Message(s)**

```
{
  "jsonrpc":"2.0",
  "result":
      {
        "messages":
          [
            {
              "attributes": {
                "mentions": <peer_address>,
                "reply": <unix_timestamp>,
                "t": <hex>
              },
              "creation_time": <unix_timestamp>,
              "edited_at": <unix_timestamp>,
              "group_id": <channel_id>,
              "message": <string>,
              "reply_to": <message_object>,
              "sender": {
                "address": <sender_hex_address>,
                "domain": <sender_bns_name>,
                "nickname": <sender_nickname>
                }
            },
            ...
          ]
      },
  "id":1
}
```

#### **"subscribe\_all\_channels\_in\_zone" (WebSocket only)**

##### **Call**

```
{"jsonrpc":"2.0","method":"subscribe_all_channels_in_zone","params":["<zone_id>"], "id":1}
```

##### **Success Response**

```
{"jsonrpc":"2.0","result":"Subscribed","id":1}
```

##### **Incoming Message(s)**

```
# Same format as the "subscribe_channel" function.
```

#### **"authenticate" (WebSocket only)**

##### **Call**

```
{"jsonrpc":"2.0","method":"authenticate","params":["<bearer_token>"], "id":1}
```

##### **Success Response**

```
{"jsonrpc":"2.0","result":"Authentication successful","id":1}
```

&nbsp;

---

&nbsp;