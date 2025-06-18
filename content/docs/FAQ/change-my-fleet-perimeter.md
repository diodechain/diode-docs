---
_schema: default
title: How do I change my fleet/perimeter?
nav_title: How do I change my fleet/perimeter?
nav_section: FAQ
weight: 20002
draft: false
---
The Fleet Contract (AKA Perimeter) can be changed using the `diode config` parameters.

1\. Open terminal

2\. Type `diode config` to list the current config settings. It will show something like:

![](/uploads/image-30.png)

3\. Copy your new fleet address (for example: 0x6000000000000000000000000000000000000000) and type `diode config -set fleet=<address>` (where `<address>` is your actual address). It will show something like:

![](/uploads/image-31.png)

4\. You can verify it worked by typing `diode config` again - it will now show your updated Fleet Contract address.