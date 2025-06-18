---
_schema: default
title: Remote VNC over SSH on Windows
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
### **Introduction**

<a href="https://en.wikipedia.org/wiki/Virtual_Network_Computing" target="_blank" rel="noopener"><strong>VNC</strong></a> is a remote desktop protocol used as a remote desktop solution across many different platforms. It's sort of like <a href="https://en.wikipedia.org/wiki/Secure_Shell" target="_blank" rel="noopener"><strong>SSH</strong></a>, which provides remote secure shell access. In this tutorial, we walk through how to set up an SSH and VNC server on Microsoft Windows, along with the Diode CLI, so that the machine can be remotely accessed via the Diode network.

Using the Diode Network brings the following advantages:

1. **Dodge NAT.** This method works even behind [**NAT**](https://en.wikipedia.org/wiki/Network_address_translation), making this solution particularly helpful in situations where you are behind a router that you are not able to configure, as is the case in a hotel or dorm room.
2. **Mobility.** Using the Diode network allows for a single connection address regardless of which physical network you are connected to. This is ideal for use on devices such as laptops and smartphones that are constantly jumping from network to network.
3. **Friendly.** Your Diode address won't change on you like your IP address does. This means that with Diode, you don't have to pay your ISP extra for a static IP address or deal with a dynamic DNS service. Your Diode address stays consistent out-of-the-box. Additionally, an easy-to-remember <a href="https://network.docs.diode.io/docs/features/what-is-bns/" target="_blank" rel="noopener"><strong>BNS</strong></a> address such as "mysurfacepro.diode" can be optionally <a href="https://network.docs.diode.io/docs/using/reserve-a-domain-name/" target="_blank" rel="noopener"><strong>registered to your Diode address</strong></a>; this name can then be used in place of your Diode address.
4. **Anonymity**. Without the Diode Network, you would have to use your public <a href="https://en.wikipedia.org/wiki/IP_address" target="_blank" rel="noopener"><strong>IP address</strong></a> to connect, tying your internet traffic to your real-world identity. With the Diode Network, there is no personal information attached to your traffic by default.
5. **Secure.** Using Diode to connect to your device provides security that your router can't match. The Diode Network is fully decentralized and uses 256 bit public key cryptography for authentication. It's easy to restrict access to only the devices you explicitly allow to connect.

&nbsp;

#### **Stage 1: Diode CLI**

1. Download the <a href="https://diode.io/resources/download/" target="_blank" rel="noopener"><strong>Diode CLI for Windows</strong></a> diode\_windows\_arm64.zip file
2. Extract diode\_windows\_arm64.zip and copy the resulting folder containing the extracted Diode file into the `%PROGRAMFILES%` directory.
3. Update the system path variable to include the Diode CLI
   1. Type "Edit the system environment variables" into the Windows search bar and click the result.
   2. Click the "Environment Variables" button at the bottom right of the popup
   3. Click on the "Path" variable
   4. With the "Path variable row highlighted, click "Edit"
   5. In the popup, click "New" & type the path to the parent directory of your recently-installed Diode CLI (it will be something like this: `%PROGRAMFILES%\diode_windows_amd64`)
   6. Click "Ok" to save & close each of the 3 popup Windows
   7. <a href="https://www.howtogeek.com/235101/10-ways-to-open-the-command-prompt-in-windows-10/" target="_blank" rel="noopener"><strong>Open up the command prompt</strong></a> and type "diode version" (make sure you're not in the same directory as the installed Diode CLI). If you get a nice readout containing version info for the Diode CLI, then you've done the above configuration successfully. If you don't get this nice readout, revisit the steps above.
4. Take note of your servers Diode client address by running `diode config` in the command prompt
5. Build your connection string to publish port 22 (see the "diode publish" section of [**this linked article**](https://cli.docs.diode.io/docs/features/cli-commands/) for more information).
   1. To publish your port publicly on the Diode Network, the following string is used: `diode publish -public 22:22`
   2. To publish a port privately to a specific Diode Client, the following string is used: `diode publish -private 22:22,<authorized_diode_client_address>`. The leading "0x" must be included in the Diode client address. f you don't have a Diode client address on another device yet, use option A for now to publish the port publicly. You will get a Diode client address in Stage 4 of this tutorial that you can use to lock down the Diode connection.
6. Follow the steps in [**this short tutorial**](https://cli.docs.diode.io/faq/how-to-start-diode-cli-at-boot-with-microsoft-windows/) to set up the Diode CLI to publish your port automatically every time your Windows computer boots up. Use the connection string from the previous step when following this tutorial.

#### **Stage 2: OpenSSH Server**

1. Install OpenSSH
   1. Type "Manage optional features" into the Windows search bar and click the result.
   2. Click "Add a feature" at the top
   3. Search for "OpenSSH" and install the "OpenSSH Server"
2. Start OpenSSH Service
   1. Type "services" in the Windows search bar and click the result
   2. In the services window, scroll down to "Open SSH Server"
   3. Right click "Open SSH Server"
   4. Click "properties"
   5. Change "Startup Type" dropdown from "Manual" to "Automatic"
   6. Click "OK"
   7. Right click "Open SSH Server" again
   8. Click "start"
   9. Close the Services window
3. **\*OPTIONAL\*** Configure OpenSSH
   1. Navigate to `%PROGRAMDATA%\ssh` and open the file named "sshd\_config" in notepad
   2. Use this file to configure your SSH settings. I recommend disabling password-based authentication in favor of <a href="https://www.concurrency.com/blog/may-2019/key-based-authentication-for-openssh-on-windows" target="_blank" rel="noopener"><strong>key-based authentication</strong></a>, but that is another topic.

#### **Stage 3: VNC Server**

1. Download & install the <a href="https://www.tightvnc.com/download.php" target="_blank" rel="noopener"><strong>TightVNC Server</strong></a> for Windows, sticking to defaults and using the "Typical" settings option if prompted (you can use any VNC server, but we'll use this one for this tutorial).
2. Set the administrative and remote access passwords as prompted.

#### **Stage 4: Connecting to the Server Via Diode Network**

1. On a different machine, <a href="https://diode.io/resources/download/" target="_blank" rel="noopener"><strong>download &amp; install the Diode CLI</strong></a>
2. In a terminal window, run: `diode socksd`
3. In a separate terminal window, use the following string to connect via ssh over the Diode Network. Be sure to substitute &lt;user&gt; and &lt;diode\_address&gt; for the proper values. The &lt;user&gt; is the username of the user on the server you're connecting to, and &lt;diode\_address&gt; is the Diode client address that you took note of in stage 1 step 4. The leading "0x" should be included in the &lt;diode\_address&gt;.

`ssh -o "ProxyCommand=nc -X 5 -x localhost:1080 %h %p" -L 5900:localhost:5900 <user>@<diode_address>.diode`

1. Use a VNC client to connect to localhost:5900 (as for VNC clients, <a href="https://remmina.org/" target="_blank" rel="noopener"><strong>Remmina</strong></a> is good on Linux, and <a href="https://tigervnc.org/" target="_blank" rel="noopener"><strong>TigerVNC Viewer</strong></a> is good on Windows)
2. **\*OPTIONAL\*** Secure the Diode Connection<br>You can secure the Diode connection so that only whitelisted clients can connect to the port published on the server. To do this, follow the steps below.
   1. Get this clients Diode address by running `diode config` in the windows command prompt. Take note of the "client address" in the output of that command.
   2. Edit your connection string that we set up in Stage 1 steps 5 & 6 to this format: `diode publish -private 22:22,0x361a8a27C3d1b939011198c69F4120CA4ea12E99` . This string publishes port 22 to the Diode network, but only for the client who's address is listen in the string. Make sure to swap out the made up address in the example above for your actual clients address that you took note of in the previous step.

#### **Alternative Stage 4: Connecting to the Server Via Diode Gateway**

The most secure and dependable way to connect to your server is by following the steps in Stage 4 directly above; however, there is also the option of using a Diode Gateway such as diode.link which will allow you to connect to your server without installing the Diode CLI on your client. This also means that you must publish your port publicly on the Diode network, and not privately. Using this method, we only have to run the following command to connect to our server via ssh: `ssh -o "ProxyCommand=nc -X 5 -x diode.link:1080 %h %p" -L 5900:localhost:5900 <user>@<diode_address>.diode`. Check out the "SSH Client Usage" section of <a href="https://cli.docs.diode.io/docs/using/remote-ssh/" target="_blank" rel="noopener"><strong>this linked article</strong></a> for more information on this topic.

---

&nbsp;