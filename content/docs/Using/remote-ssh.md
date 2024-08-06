---
_schema: default
title: Remote SSH
nav_title: Remote SSH
nav_section: Using
weight: 9
draft: false
---
[**SSH**](https://en.wikipedia.org/wiki/Secure_Shell) provides a Secure Shell access to many server systems, IT equipment, and devices. It is the defacto way of remotely connecting to an IT system for the purpose of managing and maintaining the asset. However, if the system does not have a globally unique static IP address, or does not expose port 22 (or as configured) to the public Internet, SSH cannot be used to access the system.

Diode can be used to create a secure connection to a system implementing SSH without requiring a static IP address and without exposing port 22 to the public Internet.

Have fun with this, and let use know in our [**telegram**](https://t.me/diode_chain) channel if you have any feature requests!

### **SSH Server Setup**

1\. Ensure that a local SSH server (sshd) is already running on your system, and that you have valid SSH credentials that allows you to SSH into the server. See here for an [**example**](https://cli.docs.diode.io/raspberry-pi/enable-ssh/) of enabling <a href="https://www.raspberrypi.org/documentation/remote-access/ssh/" target="_blank" rel="noopener"><strong>SSH on a Raspberry Pi</strong></a>.

2\. Install the most recent Diode Client

3\. Open a terminal window and publish the SSH service through diode:

```
diode publish -public 22:22
```

4\. Copy the presented Client Address (see red box below). This is the primary identifier of your target device and will never change. You will need it in the next step.

![](https://files.helpdocs.io/qwk5dmv7m8/articles/ub9xrruimv/1599728705235/image.png)

That's it - once Diode is running and publishing your port, you can now SSH into the system from anywhere in the world.

#### **Start Diode at Boot**

If everything works fine we recommend to <a href="https://cli.docs.diode.io/raspberry-pi/start-diode-on-boot/" target="_blank" rel="noopener"><strong>setting up the Diode Client to start at boot time</strong></a> on your SSH Server device.

#### **Restrict Access to SSH**

If you want to further secure your system, you can publish port 22 `private` (only the specific client can gain access) or `protected` (only other clients listed in your [**Fleet Contract**](https://network.docs.diode.io/docs/features/what-is-a-fleet-contract/) can gain access). Both of these options will require the SSH Client system run the Diode Client (see "SSH Client Usage" below).

##### **Private Access**

If you only want a specific system (in this example, client address "0x6311...") to access the SSH interface, you would run the following command:

```
diode publish -private 22:22,0x63115a27C3d1b549011198c69F4120CA4ea12EE9
```

You can also combine private and public publication of different ports:

```
diode publish -public 80:80 -private 22:22,0x63115a27C3d1b549011198c69F4120CA4ea12EE9
```

##### **Protected Access**

If you are not sure which systems will need access to the SSH interface, you can use the "protected" mode to publish SSH. This restricts access to only the systems authorized for the same Fleet Contract as the SSH server system belongs to.

To <a href="https://network.docs.diode.io/docs/features/what-is-a-fleet-contract/" target="_blank" rel="noopener"><strong>set this up</strong></a>, you first have to <a href="https://cli.docs.diode.io/docs/faq/configure-metamask/" target="_blank" rel="noopener"><strong>enable MetaMask on your browser</strong></a> (save the private key of the wallet you create so you, or other admins, can administrate the Fleet Contract even if your computer is no longer available!), then create a Fleet Contract at [https://diode.io/prenet/#/fleets](https://diode.io/prenet/#/fleets), then add your SSH Server's Diode client address to the Fleet Contract, and finally configure the SSH Server's Diode client to communicate as a member of the Fleet Contract (via terminal: `diode config -set fleet=<fleet address>`).

After setting up the Fleet Contract, you can use the same process to add and configure the SSH Client systems you would like to access the SSH server (use the Prenet site to add the SSH Client's Diode client address to the Fleet Contract, then configure the SSH Client's Diode client to communicate as part of the Fleet Contract via `diode config -set fleet=<fleet address>`).

Finally, you would run the Diode client on the SSH Server system to publish the SSH interface as "protected":

```
diode publish -protected 22:22
```

### **SSH Client Usage**

1\. Change to another machine so we can connect to the server via an SSH client

2\. Open a terminal window and connect via SSH over the Diode Network:

```
ssh -o "ProxyCommand=nc -X 5 -x diode.link:1080 %h %p" <user>@<client_address>.diode
```

Where:

* &lt;user&gt; is your username (e.g. on a Raspberry Pi it will usually be `pi`\- e.g. `pi@<client_address>.diode`)
* &lt;client\_address&gt; is the Client Address you copied in the SSH Server Setup section step 4

***Explainer:*** SSH has no built-in support for socks but instead offers a general `ProxyCommand` facility that can be used to proxy through the diode network.

#### **Using SSH via a Private Connection**

The "diode.link" routes the SSH connection through a public Web2:Web3 gateway so that you don't have to run the Diode Client on your SSH client machine. However, if you want to connect fully decentralized (without using the public gateway), you can [**run the Diode Client to be your own Web3.0 gateway on your SSH client machine**](https://cli.docs.diode.io/docs/using/access-web3-0-content-run-a-local-gateway/) and connect directly peer to peer.

To do this, open two terminal windows on the computer you want to SSH from.

In one terminal window, start the Diode client in socksd mode:

```
diode socksd
```

In the other terminal window, start SSH using the localhost private Diode connection:

```
ssh -o "ProxyCommand=nc -X 5 -x localhost:1080 %h %p" <user>@<client_address>.diode
```

Tip: Some ISPs, for example satellite Internet providers, manipulate traffic and break public connections via SSH. By using this method, even if you've published your SSH port publicly, you can tunnel through the non-compliant ISP and still connect to your remote machine!