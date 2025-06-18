---
_schema: default
title: What are the hardware requirements for running a Diode Client?
nav_title: What are the hardware requirements for running a Diode Client?
nav_section: FAQ
weight: 20021
draft: false
---
Diode uses the <a href="https://network.docs.diode.io/docs/faq/what-is-blockquick-tm/" target="_blank" rel="noopener"><strong>BlockQuick</strong></a> algorithm to uniquely enable communication with and via the <a href="https://network.docs.diode.io/" target="_blank" rel="noopener"><strong>Diode Network</strong></a>. BlockQuick has relatively small hardware resource requirements, allowing it to be ran on almost any communications processor:

<table><thead><tr><th><p><strong>Storage</strong></p></th><th><p><strong>RAM</strong></p></th><th><p><strong>Sync Bandwidth</strong></p></th></tr></thead><tbody><tr><td><p>20kb</p></td><td><p>50kb</p></td><td><p>20kb per sync</p></td></tr></tbody></table>

&nbsp;

However, because a fundamental requirement is <a href="https://support.diode.io/article/jieo6utgv9" target="_blank" rel="noopener"><strong>secure communications</strong></a>, systems running a Diode client must be able to support the minimum requirements for TLS <a href="https://www.secg.org/sec2-v2.pdf" target="_blank" rel="noopener"><strong>secp256k1</strong></a> security parameters (the elliptic curve used for Diode API communications).

The published <a href="https://github.com/diodechain/diode_client" target="_blank" rel="noopener"><strong>Diode client application</strong></a>, which incorporates the Diode API, security, and multiple commands & services (including an <a href="https://support.diode.io/article/k0bjp824av" target="_blank" rel="noopener"><strong>HTTP web server</strong></a>!), is about 5MB in ROM size. In the case of using the Diode client app to[**publish a localhost website**](https://support.diode.io/article/ss32engxlq) via the Diode Network (e.g. invoked by `diode publish -public 2368:80`), the process uses 21 MB of real memory (on MacOS).

As another data point, the Diode team uses the <a href="https://www.raspberrypi.org/products/raspberry-pi-zero/" target="_blank" rel="noopener"><strong>Raspberry Pi Zero</strong></a> for many blockchain communication use cases (e.g. <a href="https://diode.io/diode/Diode-Network-and-Video-Streaming-Using-Raspberry-Pi-Zero-W-20189/" target="_blank" rel="noopener"><strong>real time video streaming</strong></a>). If using a Raspberry Pi to host a graphical website, however, due to the rendering requirements of the images and other content, a <a href="https://www.raspberrypi.org/products/raspberry-pi-4-model-b/" target="_blank" rel="noopener"><strong>Raspberry Pi 4 with 8GB of RAM</strong></a> seems to be a good fit.

For additional information, see the<a href="https://diode.io/iot/hardware-requirements-of-blockchain-clients-19196/" target="_blank" rel="noopener"><strong> blog post about hardware requirements for blockchain clients</strong></a>.

---

&nbsp;