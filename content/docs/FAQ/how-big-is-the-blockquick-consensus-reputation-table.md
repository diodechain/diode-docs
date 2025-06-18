---
_schema: default
title: How big is the BlockQuick consensus reputation table?
nav_title: How big is the BlockQuick consensus reputation table?
nav_section: FAQ
weight: 20015
draft: false
---
The BlockQuick consensus reputation table is not designed to keep the whole history of the blockchain. Instead, the reputation table is based on the last 100 block headers. Block headers are much smaller than the whole block and only requiring 100 of them means that even very small devices can store and process them.

&nbsp;