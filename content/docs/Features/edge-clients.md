---
_schema: default
title: Edge Clients
nav_title: Edge Clients
nav_section: Features
weight: 101
draft: false
---
Everything (people, devices) using the Diode Network are called “Clients”.  Each Client has an <a href="https://ethereum.github.io/yellowpaper/paper.pdf" target="_blank" rel="noopener">Ethereum public address</a>, which is both its identity and its routing address.

Each address' credentials are secured with private key  - usually held as a self-custody identity "wallet".

The security of each Client is ensured through the same technology that secures self-custody digital assets everywhere.

An example Client address looks like:

> 0x24c483ca62cdd838ce793aa90f269f81b5ae4ea16

Using the <a href="https://network.docs.diode.io/docs/features/what-is-bns/" target="_blank" rel="noopener">Diode BNS</a>, this address can be referenced by a human-readable name.

Diode has a system of "security perimeter" contracts that build up group relationships (aka Access Control Lists) from the basic Client address.  For example, an "Identity" is a multi-signature on-chain wallet that can be managed by a initiator-bootstrapped list of Client addresses.

&nbsp;

&nbsp;

&nbsp;