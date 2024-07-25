---
_schema: default
title: How Is Diode Using Websockets?
nav_title: How Is Diode Using Websockets?
nav_section: FAQ
weight: 20032
draft: false
---
The default Diode Go Client has a built-in capability to convert any binary TCP socket into a websocket.

So, for example, the Raspberry Pi video streaming demo is simply publishing the raw video to a port, and then the Diode Client is converting that into websocket frames.