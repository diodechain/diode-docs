---
_schema: default
title: Why does BlockQuick use the last 100 blocks only? Why not more or less?
nav_title: Why does BlockQuick use the last 100 blocks only?
nav_section: FAQ
weight: 20014
draft: false
---
The current proof of concept clients are working with consensus table sizes of 100.

What we learned in Ethereum is that small miners are fluctuating a lot, while big miners stay for very long periods. So for the reputation table size, the question is how we can achieve the maximum consensus stability.

Factors influencing the size of the table:

Pro Small

* Smaller tables mean fewer bytes to transport and store
* Large/infinite tables would collect “zombies”

Pro Big

* Larger tables increase the cost of an attack
* Variability vs Stability