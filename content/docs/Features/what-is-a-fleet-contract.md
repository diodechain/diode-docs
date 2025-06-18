---
_schema: default
title: Fleet Contract
nav_title: Fleet Contract
nav_section: Features
weight: 107
draft: false
---
All Clients using the Diode Network must be listed in a Fleet Contract in order to be able to communicate. Sometimes a Fleet Contract is also referred to as a Perimeter.

A Fleet Contract sponsors or underwrites your device's communications. Every time a device communicates with the Diode Network, it must provide the Fleet Contract by which its communication is sponsored. A device can belong to many different Fleet Contracts, but each communication session must specify only one Fleet Contract that it would like to use for that session.

In the context of the Diode Network, a Fleet Contract is a decentralized <a href="https://en.wikipedia.org/wiki/Smart_contract" target="_blank" rel="noopener"><strong>smart contract</strong></a> that stores and manages the identities of clients (public keys) that it is sponsoring for communication. The Fleet Contracts provide a number of functions to facilitate secure communications, including client registration, client deregistration, protected or private connections, and other capabilities.

Diode Network nodes provide secure bandwidth in return for rewards from the Fleet Contract.  Monthly rewards are based on 1% of the staked tokens in the relevant Fleet Contract.  The higher the rewards, the more eager nodes will be to service them.  Therefore, more stake will usually result in higher Quality of Service (QoS).  If you have no stake in the Fleet Contract, then it is unlikely that an infrastructure node will want to handle your traffic because it will not get rewarded for doing so.

For commercial use of the Diode Network, it is important that you have your own Fleet Contract so that your device cannot be de-listed from someone else's Fleet Contract, thereby disabling device communications. However, for development purposes, Diode provides a "Diode Developer Fleet Contract" at address 0x6000000000000000000000000000000000000000 that can be used by anyone for testing and non-commercial use.

If you are using the Diode Client and have not explicitly set your Fleet Contract, it will default to using the Diode Developer Fleet Contract. To see what Fleet Contract your Client is using, use: `diode config`or go to the <a href="https://diode.io/prenet/#/" target="_blank" rel="noopener"><strong>Diode Network Explorer</strong></a> and search for your Client address - the account details page will display the Fleet Contract it belongs to.

To create your own Fleet Contract, use the Diode Collab's Network feature or use the <a href="https://diode.io/prenet/#/fleets" target="_blank" rel="noopener"><strong>Diode Network Explorer Fleets page</strong></a> (must have [**MetaMask installed**](https://network.docs.diode.io/docs/faq/configure-metamask/)).

Once you've created your Fleet Contract, you can <a href="https://network.docs.diode.io/docs/faq/change-my-fleet-perimeter/" target="_blank" rel="noopener"><strong>configure your devices to use it.</strong></a>