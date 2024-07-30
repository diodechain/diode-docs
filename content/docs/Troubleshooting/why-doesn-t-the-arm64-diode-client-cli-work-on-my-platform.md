---
_schema: default
title: Why doesn't the ARM64 Diode client / CLI work on my platform?
nav_title: Why Doesn't The ARM64 Diode Client / CLI Work on My Platform?
nav_section: Troubleshooting
weight: 300
draft: false
---
I have recently installed the diode client on an arm64 Ubuntu 18.04 platform, but when I installed using the install script, the installation fails. And, when I install the diode client manually, the commands don't seem to trigger any actions. How do I start using the Diode client?

Unfortunately, the arm64 build for the Diode CLI is compiled for the ARM processor used in 64 bit Raspberry Pis. If you are using a 64 bit Linux installation on a different platform, it will require you to compile from source for your machine from [**https://github.com/diodechain/diode\_client**](https://github.com/diodechain/diode_client).