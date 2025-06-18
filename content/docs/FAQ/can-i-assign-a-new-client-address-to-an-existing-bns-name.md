---
_schema: default
title: Can I assign a new client address to an existing BNS name?
nav_title: Can I assign a new client address to an existing BNS name?
nav_section: FAQ
weight: 20003
draft: false
---
Yes you can. If you use <a href="https://network.docs.diode.io/docs/using/reserve-a-domain-name/" target="_blank" rel="noopener"><strong>MetaMask to manage the BNS name</strong></a>, you can go to the <a href="https://diode.io/prenet/#/dns" target="_blank" rel="noopener"><strong>Diode Network Explorer's BNS page</strong></a> and simply enter a new Client Address / ID in the box provided under the BNS name. You must be <a href="https://network.docs.diode.io/docs/faq/configure-metamask/" target="_blank" rel="noopener"><strong>authenticated with MetaMask</strong></a> and connected to the account that owns the BNS name.

You can use the Diode Client to do this without MetaMask per:

`diode bns -register <name>=<new_address>`

In order to run this command, the Diode Client running the command must be the original owner of the BNS name.