---
_schema: default
title: How Do I Change My Fleet/Perimeter?
nav_title: How Do I Change My Fleet/Perimeter?
nav_section: FAQ
weight: 6
draft: false
---
The Fleet Contract (AKA Perimeter) can be changed using the `diode config` parameters.

1\. Open terminal

2\. Type `diode config` to list the current config settings. It will show something like:

![](https://files.helpdocs.io/qwk5dmv7m8/articles/tk1913nsjc/1699465470862/image.png)

3\. Copy your new fleet address (for example: 0x6000000000000000000000000000000000000000) and type `diode config -set fleet=<address>` (where `<address>` is your actual address). It will show something like:

![](https://files.helpdocs.io/qwk5dmv7m8/articles/tk1913nsjc/1709393035976/image.png)

4\. You can verify it worked by typing `diode config` again - it will now show your updated Fleet Contract address.