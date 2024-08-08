---
_schema: default
title: Access Web3.0 Content / Run a Local Gateway
nav_title: Access Web3.0 Content
nav_section: Using
weight: 8
draft: false
---
Diode hosts a public gateway to the Diode Network at &lt;address&gt;.diode.link. All the public Web3.0 content published on the Diode Network can be accessed using this gateway. However, some of the Web3.0 content is published in Private mode (only accessible to specific identities) or in Protected mode (only accessible to identities registered in the same [**Fleet Contract**](https://network.docs.diode.io/docs/features/what-is-a-fleet-contract/) as the publisher) - this content cannot be accessed via the public gateway.

In order to access Private or Protected content, you can [**run the Diode Client locally**](https://network.docs.diode.io/docs/using/developers-start-here/) as a local gateway / proxy server into the Diode Network. Once it is running, you can use a browser or other applications directly access Web3.0 content you are authorized for.

Have fun with this, and let use know in our [**T**]()[**elegram**](https://t.me/diode_chain) channel if you have any feature requests!

### **Run the Diode Client as a Proxy Server**

Many applications have builtin support for socks proxy servers - we'll start the Diode Client as a socks proxy server so those applications can access Web3.0 content published on the Diode Network. See the sections below for some examples.

1\. [**Install the most recent Diode Client**](https://network.docs.diode.io/docs/using/developers-start-here/)

2\. Open a terminal window and run the command

```
diode socksd
```

This will start a local socks proxy server - by default, it is launched on port 1080. This command authenticates your proxy server communications over the Diode Network via your Client address. Therefore, any content that is published in Private or Protected mode to your Client address will be accessible to your system at the content's corresponding address.

### **Firefox**

You can browse website content via Firefox by setting it up to use your local socks proxy server.

In Firefox, go to the network settings and select `manual proxy configuration`. Set as proxy server `localhost` and port `1080`. Ensure it’s using `SOCKS v5` and check `Proxy DNS when using SOCKS v5`.

![](/uploads/image-27.png)

To access a website, for example, being published by Client address 0x70114a27f3d1b549012498c69a4120ca4ea11e21, you can type `0x70114a27f3d1b549012498c69a4120ca4ea11e21.diode` into Firefox's address bar.

If the particular host has configured a BNS name, you can access it at &lt;bns-name&gt;.diode.

### **SSH**

SSH has no built-in support for socks but instead offers a general `ProxyCommand` facility that can be used to proxy SSH through the socks proxy.

This can be enabled by adding the options `ProxyCommand=nc -X 5 -x localhost:1080` to the connection command. `-X 5` hereby means SOCKS v5 and `-x localhost:1080` is the local Diode socks proxy.

```
ssh -o "ProxyCommand=nc -X 5 -x localhost:1080 %h %p" <user>@<client_address>.diode
```

Where:

* &lt;user&gt; is your username (e.g. on a Raspberry Pi it will usually be `pi`\- e.g. `pi@<client_address>.diode`)
* &lt;client\_address&gt; is the Client address or BNS name for the SSH server

For more information, see the [**Remote SSH article**](https://cli.docs.diode.io/docs/using/remote-ssh/).

### **Curl**

The curl command line tool has built-in support for socks5 and dns proxying with the `–proxy` or `-x` short option. For example, downloading a file from a Client via the Diode Network with curl works like this:

```
curl -x socks5h://localhost:1080 <client_address>.diode
```

Where:

* &lt;client\_address&gt; is the Client address or BNS name for the server hosting the file

## **VideoLAN Client (VLC)**

VLC is a great tool for viewing or listening to streaming media - we can use it in conjunction with our local Diode proxy server to consume streaming content over the Diode Network.

VLC has only partial support for SOCKS v5 - it lacks support for hostname resolution through SOCKS v5, but can be tricked to accept SOCKS v5 connections through the `nc` command line tool.

```
nc -X 5 -x localhost:1080 <client_address>.diode.link <port> | vlc -
```

Where:

* &lt;client\_address&gt; is the Client address or BNS name for the server providing streaming content

  &nbsp;

---