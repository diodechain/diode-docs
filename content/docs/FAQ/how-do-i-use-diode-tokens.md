---
_schema: default
title: How Do I Use DIODE Tokens?
nav_title: How Do I Use DIODE Tokens?
nav_section: FAQ
weight: 20024
draft: false
---
You can use the DIODE token to Stake Fleet Contracts or Miners on the Diode Network.

**<u>Fleet Contracts</u>**

All communication on the Diode Network must be sponsored by a [**Fleet Contract**](https://network.docs.diode.io/docs/faq/what-is-a-fleet-contract/) (entities communicating must be listed in a Fleet Contract). The Fleet Contract has a Stake associated with it - this Stake is an amount of DIODE that is locked for one epoch (approx. one month), and provides a pool of value that determines how much Relays, that have transacted traffic on behalf of the Fleet Contract, are paid at the end of the epoch. Without Stake in the Fleet Contract, it is unlikely the Relays will accept the traffic - or, if they do, that the QoS of the traffic will be very high.

Diode sponsors the Diode Development Fleet Contract (the default contract used for the Diode CLI) and the Diode App Fleet Contract (the default contract used for the Diode application). Other applications can also use the Diode Development Fleet Contract for non-commercial development purposes.

If you are an application provider, you will need to ultimately create your own Fleet Contract to sponsor the bandwidth required by your application. If desired, Diode can provide a Fleet Contract management service (which can either use your tokens or can sponsor tokens on your behalf). Otherwise, application sponsors will have to create and manage their own Fleet Contract. The Diode application's Enterprise tier has a management UI built-in to allow application sponsors to create their own Fleet Contracts.

**<u>Miners</u>**

To mine blocks on the Diode L1 Network, Miners use <a href="https://diode.io/mining/proof-of-stakework-a-community-vision-19168/" target="_blank" rel="noopener"><strong>Proof of StakeWork</strong></a> . Therefore, DIODE must be staked by the Miner to have a reasonable chance of mining a block. The more DIODE staked, the stronger the Miner's proof power.

---

&nbsp;