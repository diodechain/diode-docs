---
_schema: default
title: How Do I Stake My DIODE Tokens for Mining?
nav_title: How Do I Stake My DIODE Tokens for Mining?
nav_section: FAQ
weight: 20029
draft: false
---
You can use the console to add stake for your miner. The following example will stake 5 Diode, if available in your balance.

To test if the transaction will work:

`Shell.call_from(Diode.miner, Diode.registry_address, "MinerStake", [], [], value: Shell.ether(5))`

To submit the transaction:

`Shell.submit_from(Diode.miner, Diode.registry_address, "MinerStake", [], [], value: Shell.ether(5))`