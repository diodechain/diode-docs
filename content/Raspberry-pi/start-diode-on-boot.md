---
_schema: default
title: Start Diode on Boot
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
If you are running the Diode Client on a Raspberry Pi, it is nice to auto-start it on boot up so you don't have to SSH or manually login to start it every time the system reboots.

Raspberry Pi’s as well as most other Linux distributions such as Debian and Linux nowadays use *systemd* for controlling services and startup applications.

See the steps below to configure *systemd* on your Raspberry Pi to auto-start Diode on boot.

Have fun with this, and let use know in our [**Telegram**](https://t.me/diode_chain) channel any feature requests you have!

1\. Install Diode via:

```
curl -Ssf https://diode.io/install.sh | sh
```

2\. Create the *systemd* configuration entry

The following entry for systemd uses the Diode Client to publish port 80 for HTTP, port 22 for SSH, and port 3030 for an additional service. You can copy the contents below and save it to a *diode.service* file:

```
[Unit]
Description=Diode blockchain network client

[Service]
Type=simple
ExecStart=/home/pi/opt/diode/diode publish -public 22:22,80:80,3030:3030
Restart=always
User=pi

[Install]
WantedBy=multi-user.target
```

or you can download the *diode.service* file from our website via: `wget https://diode.io/diode.service`

**IMPORTANT NOTE:** The example file assumes that diode is installed for the *pi* user on a Raspberry Pi. When running on Ubuntu or another distribution, ensure that the username matches the user who installed the Diode Client in these two locations in the diode.service file:

ExecStart=/home/*username*/opt/diode/diode publish -public 22:22,80:80,3030:3030

User=*username*

3\. Copy the *diode.service* file to the /etc/systemd/system/folder:

```
sudo cp diode.service /etc/systemd/system/
```

4\. Start the service and check that it is working

```
sudo systemctl start diode
systemctl status diode
```

After the second call you should see something like:

```
diode.service - Diode blockchain network client
   Loaded: loaded (/etc/systemd/system/diode.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2020-07-27 13:29:51 CEST; 1h 53min ago
 Main PID: 259 (diode)
   CGroup: /system.slice/diode.service
           └─259 /home/pi/opt/diode/diode publish -public 22:22,80:80,3030:3030

Jul 27 13:30:12 betahaus-berlin diode[259]: 07/27/2020 13:30:12 [INFO] Network is validated, last valid block number: 563440
Jul 27 13:30:12 betahaus-berlin diode[259]: 07/27/2020 13:30:12 [INFO]                      :
Jul 27 13:30:12 betahaus-berlin diode[259]: 07/27/2020 13:30:12 [INFO] Http Gateway Enabled : http://0xc206e1255cbace8ba904daa259d7a5b7f90e2d50.diod
Jul 27 13:30:12 betahaus-berlin diode[259]: 07/27/2020 13:30:12 [INFO] Port      <name>     : <extern>     <mode>    <protocol>     <allowlist>
Jul 27 13:30:12 betahaus-berlin diode[259]: 07/27/2020 13:30:12 [INFO] Port         22      :       22      public       any
Jul 27 13:30:12 betahaus-berlin diode[259]: 07/27/2020 13:30:12 [INFO] Port         80      :       80      public       any
Jul 27 13:30:12 betahaus-berlin diode[259]: 07/27/2020 13:30:12 [INFO] Port       3030      :     3030      public       any
```

5\. If everything seemed like it worked, break out of the Diode Client with `ctrl-c` and permanently enable it so that it will start on boot:

```
sudo systemctl enable diode
```

You’re all set! Diode will now run on every system start!