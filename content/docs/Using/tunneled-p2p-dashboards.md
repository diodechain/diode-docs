---
_schema: default
title: Remote Drive Mapping (SMB Shares) on Windows and Mac
nav_title: 'Remote Drive Mapping '
nav_section: Using
weight: 13
draft: false
---
With this tutorial, you can "Map Network Drive" on Windows, or "Connect to server" on Mac, to securely mount a drive that is on a remote computer or server. The Diode Network tunnels your Windows box (or Linux or Mac) directly to the remote shared drive. No static IP address or VPN required.

This is handy if you want to provide multi-user access to the same files - such as in the case of a MS Access database.

If you have any questions, connect with us in our <a href="https://t.me/diode_chain" target="_blank" rel="noopener"><strong>telegram group</strong></a>!

### **The moving pieces**

1. Remote drive - we'll run this as a Samba share on a Linux box
2. Local machine - a Windows box that wants filesystem access to a remote drive

### **Remote Drive Setup**

**System:** Ubuntu running on a Contabo VM

#### **Setup Samba**

Basically, you can follow the instructions at: <a href="https://ubuntu.com/tutorials/install-and-configure-samba#1-overview" target="_blank" rel="noopener"><strong>https://ubuntu.com/tutorials/install-and-configure-samba#1-overview</strong></a>. But, just to clarify, this is the step-by-step we did from a terminal:

* `sudo apt update`
* `sudo apt install samba`
* `whereis samba`
  * `>> samba: /usr/sbin/samba /usr/lib/x86_64-linux-gnu/samba /etc/samba /usr/share/samba /usr/share/man/man8/samba.8.gz /usr/share/man/man7/samba.7.gz`
* `adduser sambademo`
  * Set pw: &lt;`yourpwd1`&gt;
* `mkdir /home/sambademo/sambashare`
* `touch /home/sambademo/helloworld.txt`
* `sudo nano /etc/samba/smb.conf`
  * Add the following<br><code>[sambashare]<br />comment = Samba on Ubuntu<br />path = /home/sambademo/sambashare<br />read only = no<br />browsable = yes</code>
* `sudo service smbd restart`
* `sudo smbpasswd -a sambademo`
  * Set pw: &lt;`yourpwd2`&gt;
* `sudo ufw allow samba`
  * This is only required if you want to ALSO access/verify your share to your public IP address. Otherwise, leave the firewall blocking Samba.

At this point, your Samba share is up and running. If you have a static IP / LAN IP, you can skip down to Local machine setup if you want to sanity-check it and then come back here to continue on.

#### **Setup Diode**

The steps below use `diode publish -public.` You may want to use `diode publish -private` to publish your Samba share not just via Diode tunneling, but only via Diode tunneling to specific authorized clients.

Basically, you can follow the instructions <a href="https://support.diode.io/article/gmo8f1f4ys" target="_blank" rel="noopener"><strong>here</strong></a>. But, just to clarify, this is the step-by-step we did from a terminal:

* `curl -Ssf https://diode.io/install.sh | sh`
  * This installs the Diode CLI
  * `diode time`
    * Verify the Diode CLI is installed correctly
    * Copy your Server's Diode Address for use later. e.g. the 0xb....9 address as in the following image

    ![](/uploads/image-18.png)

* `wget https://diode.io/diode.service`
* `sudo mv diode.service /etc/systemd/system/`
* `sudo nano /etc/systemd/system/diode.service`
  * Change `ExecStart=/home/pi/opt/diode/diode publish -public 22:22,80:80,3030:3030` to `ExecStart=<user home path>/opt/diode/diode publish -public 22:22,445:445,139:139` (where `<user home path>` is whatever your user name is - on Ubuntu something like `/diodeuser/`)
  * Change `User=pi` to `User=<yourusername>`(where &lt;yourusername&gt; is whatever your user name is - e.g. `User=diodeuser`)
  * Save it (ctrl-X, Y)
* `sudo systemctl enable diode`
* `sudo systemctl start diode`
* `sudo systemctl status diode`
  * To verify diode is running - you'll see output that includes your Samba ports:

![](/uploads/image-19.png)

At this point, your Samba share is up and running and accessible from anywhere in the world via its Diode Address. Now you can `sudo ufw deny samba` if you want to disable external IP-address-based access to Samba (recommended).

### **Local Machine Setup**

#### **MacOS**

OK, super quick - on Mac, Finder allows you to specify a port for your network drives. So it is super easy to mount a network drive on Mac:

* Make sure you have the Diode CLI installed (`curl -Ssf https://diode.io/install.sh | sh`)
* `diode -bind 1039:0xb...9:445`
  * Where 0xb...9 is the full Diode Address you copied above
  * This "binds" your local machine's port 1039 to the remote server's port 445 - which is where Samba lives
* Open Finder and, in the top menu bar, select "Go" and "Connect to Server"

  ![](/uploads/image-20.png)

* Enter the address smb://localhost:1039/sambashare and click "Connect"

![](/uploads/image-21.png)

* Enter "sambademo" and the `<yourpwd2>` password you configured above

![](/uploads/image-22.png)

* Finder will open to your remote Samba share!

![](/uploads/image-23.png)

#### **Windows**

Windows is not so helpful - it won't let you specify a port to find a network drive on. And, it won't allow you to bind port 445 - that is already taken by the selfish lanman. So, we'll create our own loopback adapter on which no-one is using port 445, then port-map that to a normal localhost ephemeral port, and then bind that port to our remote server.

* Download the Diode CLI for Windows from [**https://diode.io/download**](https://diode.io/download) - we recommend putting diode.exe in the user's home folder (e.g. C:\\users\\diodeuser\\diode.exe) since that is where the terminal always opens to by default
  * Open a terminal window (cmd.exe) and you can test to see if Diode is working by typing `diode time`

For the next steps, you can do it via Powershell or via the UI. We'll do it the Powershell way, although UI is arguably easier (see <a href="https://github.com/jjkeijser/cifs-over-ssh/blob/main/Win10/Multihost.md" target="_blank" rel="noopener"><strong>here for directional UI guidance</strong></a>).

* Open Powershell as administrator (right click, Run as Administrator)
* Setup some variables (type these as is in powershell)
  * `$loopback_name = 'SMB-Loopback'`
  * `$primary_interface = 'Ethernet'`
  * `$loopback_ipv4 = '10.254.1.3'`
  * `$loopback_ipv4_length = '32'`
* Install the loopback module
  * `Install-Module -Name LoopbackAdapter -MinimumVersion 1.2.0.0 -Force`
    * Asks to install NuGet → Y
    * Completes with no additional messages
* Import the module
  * `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Unrestricted`
    * Allows running scripts
  * `Import-Module -Name LoopbackAdapter`
    * Completes with no additional messages
* Create loopback interface
  * `New-LoopbackAdapter -Name $loopback_name -Force`
    * Installed Chocolately and finally printed out success
    * Network settings now show “Etherenet 2” and “Identifying…” status!
* Now setup some more variables
  * `$interface_loopback = Get-NetAdapter -Name $loopback_name`
  * `$interface_main = Get-NetAdapter -Name $primary_interface`
* Ensure the adapter is not preferred so it will not jack anything up - it will only be used when EXPLICITLY called out
  * `Set-NetIPInterface -InterfaceIndex $interface_loopback.ifIndex -InterfaceMetric "254" -WeakHostReceive Enabled -WeakHostSend Enabled -DHCP Disabled`
  * `Set-NetIPInterface -InterfaceIndex $interface_main.ifIndex -WeakHostReceive Enabled -WeakHostSend Enabled`
  * `Set-NetIPAddress -InterfaceIndex $interface_loopback.ifIndex -SkipAsSource $True`
* Disable DNS registration so there is nothing routed here intentionally
  * `Get-NetAdapter $loopback_name | Set-DNSClient –RegisterThisConnectionsAddress $False`
* Setup the IPs for the loopback
  * `New-NetIPAddress -InterfaceAlias $loopback_name -IPAddress $loopback_ipv4 -PrefixLength $loopback_ipv4_length -AddressFamily ipv4`
    * Prints out a big table of infos, confirming at the top that we are at 10.254.1.3
* Disable unused bindings (may not be required)
  * `Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_msclient`
  * `Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_pacer`
  * `Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_server`
  * `Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_lltdio`
  * `Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_rspndr`
* Use netsh to port forward to work around the lanman dominance of localhost:445
  * `netsh interface portproxy add v4tov4 listenaddress=10.254.1.3 listenport=445 connectaddress=127.0.0.1 connectport=44445`
  * Verify port mapping
    * `netsh interface portproxy show v4tov4`

    ![](/uploads/image-24.png)

* Reset your system to apply all the settings

Finally now we can connect to the remote server!

* Open a terminal window and type our bind command
  * `diode -bind 44445:0xb...9:445`
    * Where 0xb...9 is the full Diode Address you copied above
    * This "binds" your local machine's port 44445 (which is mapped to your loopback's 445) to the remote server's port 445 - which is where Samba lives
* Open explorer, right click on “Network”, select “map network drive” and use \\\\10.254.1.3\\sambashare
  * This will popup a box asking for your credentials - enter "sambademo" and the `<yourpwd2>` password you configured above

Windows will map your network drive and you can now access your remote drive.

&nbsp;

&nbsp;

&nbsp;

---

&nbsp;