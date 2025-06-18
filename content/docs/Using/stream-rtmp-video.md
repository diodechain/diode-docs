---
_schema: default
title: Stream RTMP Video
nav_title: Stream RTMP Video
nav_section: Using
weight: 10
draft: false
---
Standards-based video streaming over the Diode network unlocks a wealth of features and video capture devices. This article demonstrates how to use RTMP video streaming from a Raspberry Pi.

<a href="https://en.wikipedia.org/wiki/Real-Time_Messaging_Protocol" target="_blank" rel="noopener"><strong>RTMP</strong></a> is a protocol for high-performance streaming of audio, video, and data. It is implemented using 3 components:

1. **Encoder** - Captures and encodes a live stream before publishing to an RTMP server.
2. **Server** - Transcodes the stream and hosts it for clients to fetch and render
3. **Client** - The receiver of the stream which renders it for the user

We will use a Raspberry Pi Camera as our source, <a href="https://www.raspberrypi.com/news/buster-the-new-version-of-raspbian/" target="_blank" rel="noopener"><strong>Raspbian Buster as the OS</strong></a> (30 Dec 2021 Bullseye will work when it is updated to support Pi Camera 2 and Noir on Pi Zero W), <a href="https://gstreamer.freedesktop.org/" target="_blank" rel="noopener"><strong>gstreamer</strong></a> as our encoder, <a href="https://www.nginx.com/" target="_blank" rel="noopener"><strong>nginx</strong></a> + <a href="https://github.com/arut/nginx-rtmp-module" target="_blank" rel="noopener"><strong>nginx-rtmp-module</strong></a> for our server, and <a href="https://videojs.com/" target="_blank" rel="noopener"><strong>video.js</strong></a> for the client.

### **Prerequisites**

#### **Hardware**

* <a href="https://www.raspberrypi.org/products/raspberry-pi-zero-w/" target="_blank" rel="noopener"><strong>Raspberry Pi Zero W</strong></a> - tested with both Pi4 and Pi Zero - will likely work with all Pi versions
* <a href="https://www.raspberrypi.org/products/camera-module-v2/" target="_blank" rel="noopener"><strong>Raspberry Pi Camera Module V2</strong></a> - NOIR also works. HOWEVER, as of this writing 30 Dec 2021, the Raspberry Pi Camera Module 2, Raspberry Pi Camera Module 2 NoIR, and Raspberry Pi High-Quality Camera are not yet working with this build under the Bullseye release on the new Raspberry Pi Zero 2 W.

#### **Software**

* <a href="https://www.raspberrypi.com/software/" target="_blank" rel="noopener"><strong>Latest PI OS</strong></a>
* <a href="https://diode.io/resources/download/" target="_blank" rel="noopener"><strong>Install the Diode CLI</strong></a> - for convenience, at the PI terminal prompt, run `curl -Ssf https://diode.io/install.sh | sh`. For instructions for how to configure the Diode CLI to start on boot, [**click here**](https://support.diode.io/article/gmo8f1f4ys-start-on-bootup).

### **Installation and Setup**

For the following steps, it is assumed you have Raspbian Buster OS installed on your Pi and you have SSH access to it as per the previous instructions. If you’re stuck, you can follow the <a href="https://www.raspberrypi.com/documentation/computers/configuration.html#setting-up-a-headless-raspberry-pi" target="_blank" rel="noopener"><strong>headless Instructions</strong></a>.

#### **Enable The Camera**

From the Pi terminal, type `sudo raspi-config` and select: **Interfacing Options -&gt; Camera -&gt; Yes**

#### **Install GStreamer**

From the Pi terminal, type:

##### **For Buster OS**

`sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-omx-rpi gstreamer1.0-omx-rpi-config`

##### **For Bullseye (as of 30<sup>th</sup> Dec 2021 no support for Noir and Picam Ver2.0 Pi Zero W):**

`sudo apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-ugly gstreamer1.0-tools gstreamer1.0-gl gstreamer1.0-gtk3`

#### **Install NGINX**

Normally, the server would be hosted on a different machine than the encoder. However, to keep it simple, we will install everything self-contained on the Raspberry Pi.

From the Pi terminal, type:

`sudo apt install libnginx-mod-rtmp nginx-full`

#### **Configure NGINX**

We will enable the rtmp module for nginx and configure it to republish the stream over the <a href="https://en.wikipedia.org/wiki/HTTP_Live_Streaming" target="_blank" rel="noopener"><strong>HTTP Live Streaming</strong></a> (HLS) protocol. HLS is a streaming protocol developed by Apple which is widely supported by all major desktop browsers and mobile devices. Also, since Diode takes care of securing the stream, you don’t have to worry about letsencrypt - we just need to set up a standard non-secure port 80.

Edit /etc/nginx/modules-enabled/rtmp.conf to include the following:

```
# /etc/nginx/modules-enabled/rtmp.conf
# RTMP configuration
rtmp_auto_push on;
rtmp {
    access_log /var/log/nginx/rtmp_access.log;
    server {
        listen 1935; # Listen on standard RTMP port ping 30s;
        chunk_size 4096;
        notify_method get;
        publish_time_fix off;

        application live {
            live on;
            record off;
            hls on;
            hls_path /var/www/html/hls;
            hls_fragment 3;
            hls_playlist_length 60;
            deny play all;
        }
    }
}
```

&nbsp;

Delete everything in the default site file (/etc/nginx/sites-enabled/default) and insert the following:

```
# /etc/nginx/sites-enabled/default
server {
    listen 80 default_server;
    listen [::]:80 default_server;
    root /var/www/html;
    index index.html index.htm index.nginx-debian.html;
    server_name _;
    location / {
        try_files $uri $uri/ =404;
    }
    location /hls {
        # Disable cache
        add_header Cache-Control no-cache;

        # CORS setup
        add_header 'Access-Control-Allow-Origin' '*' always;
        add_header 'Access-Control-Expose-Headers' 'Content-Length';

        # allow CORS preflight requests
        if ($request_method = 'OPTIONS') {
            add_header 'Access-Control-Allow-Origin' '*';
            add_header 'Access-Control-Max-Age' 1728000;
            add_header 'Content-Type' 'text/plain charset=UTF-8';
            add_header 'Content-Length' 0; return 204;
        }

        types {
            application/vnd.apple.mpegurl m3u8;
            video/mp2t ts;
        }
    }
}
```

&nbsp;

Create the hls directory:

`sudo mkdir -p /var/www/html/hls`

`sudo chown pi:pi /var/www/html/hls`

Restart NGINX:

`sudo systemctl restart nginx`

#### **Configure the GStreamer Pipeline**

GStreamer is a powerful streaming media tool. While there is a <a href="https://github.com/thaytan/gst-rpicamsrc" target="_blank" rel="noopener"><strong>gstreamer element</strong></a> for the Raspberry Pi Camera, it does not come included in the Raspbian distribution and would require compilation. It is easier to just get started by using the raspivid utility included in Raspian and pipe the output to GStreamer.

We will capture 720p 30fps video with a 2Mb bitrate. raspivid outputs h264 encoded frames, which we will then pipe into gstreamer to wrap into a [**FLVMUX - Flash Container**](https://en.wikipedia.org/wiki/Flash_Video) before uploading to the rtmp server.

Insert the following into /usr/local/bin/gst-diode-local-stream:

```
#!/bin/bash
# /usr/local/bin/gst-diode-local-stream

raspivid -t 0 -b 2097152 -w 1280 -h 720 -fps 30 -n -o - | gst-launch-1.0 fdsrc ! video/x-h264,width=1280,height=720,framerate=30/1,profile=high,stream-format=byte-stream  ! h264parse ! queue ! flvmux streamable=true ! rtmpsink location=\"rtmp://localhost:1935/live/diodecam\"
```

&nbsp;

Make the gst-diode-local-stream file executable:

`sudo chmod +x /usr/local/bin/gst-diode-local-stream`

#### **Create a Service for the Diode GStreamer Pipeline**

We will create a systemd unit file to manage the gstreamer process. We'll configure it to automatically restart the stream if it goes down.

Insert the following into /etc/systemd/system/gst-diode-local-stream.service:

```
[Unit]
Description=RPI GStreamer Diode RTMP Source

[Service]
Type=simple ExecStart=/usr/local/bin/gst-diode-local-stream
Restart=on-failure
RestartSec=5s

[Install]
WantedBy=multi-user.target
```

&nbsp;

Enable and start the service:

`sudo systemctl daemon-reload`

`sudo systemctl enable gst-diode-local-stream`

`sudo systemctl start gst-diode-local-stream`

### **Make the Website**

We will publish the stream to a microsite hosted and published by the Pi. The website will use a fullscreen video that autoplays when you load it (NOTE: some browsers like Safari disable this). You can create any player here to suit your own application.

Insert the following into /var/www/html/index.html:

```
<!DOCTYPE html>
<meta charset="UTF-8">
<html lang="en">
    <head>
        <title>Diode HLS Cam</title>
        <link href="https://unpkg.com/video.js/dist/video-js.css" rel="stylesheet">
    </head>
    <body>
        <div width="100%" height="100%">
            <video id="videojs-player" class="video-js vjs-default-skin vjs-layout-huge" preload="auto" data-setup="{}" muted fluid="true" controls="true" autoplay="autoplay">
            <source src="/hls/diodecam.m3u8" type="application/x-mpegURL">Your browser does not support the video tag.
            </video>
        </div>

        <script src="https://unpkg.com/video.js/dist/video.min.js"></script>
        <script src="https://unpkg.com/videojs-flash/dist/videojs-flash.min.js"></script>
        <script src="https://unpkg.com/videojs-flvjs/dist/videojs-flvjs.min.js"></script>
    </body>
</html>
```

&nbsp;

Remove the default website index:

`sudo rm /var/www/html/index.nginx-debian.html`

### **Access the Stream**

First, let's access the stream locally by typing in your Pi's IP address in a browser on another computer on the same network.

Once you know that the stream works locally, now it’s time to let Diode work its magic so you can access the stream remotely.

1. If you followed the [**instructions for how to start the Diode CLI on boot**](https://cli.docs.diode.io/raspberry-pi/start-diode-on-boot/), you will have a file called diode.service in /etc/systemd/system
2. In the terminal, go to /etc/systemd/system
3. `sudo nano diode.service`
4. For our video app we only need port 80, but if you want to activate more / other, modify the ports to suit your environment:

```
ExecStart=/home/pi/opt/diode/diode publish -public 22:22,80:80,3030:3030
```

5\. Save the file and exit nano

6\. Start the Diode service: `sudo systemctl start diode`

7\. Check its status:`systemctl status diode` - you should see the service with a green status as below

![](/uploads/image-28.png)

You will notice that diode prints a unique address (i.e. https://&lt;yourclientaddress&gt;.diode.link), copy and paste that into a browser window and you will then see your live stream with a letsencrypt certificate securing your video stream from your local pi out to the blockchain!

To learn more about Diode, <a href="https://cli.docs.diode.io/docs/faq/docs-on-other-products/" target="_blank" rel="noopener"><strong>read other articles here</strong></a> or to the [**telegram group**](https://t.me/diode_chain) and ask away - we’re a friendly bunch of folks!

---

&nbsp;