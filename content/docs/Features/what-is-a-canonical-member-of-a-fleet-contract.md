---
_schema: default
title: What is a Canonical Member of a Fleet Contract?
nav_title: Canonical Member of a Fleet Contract
nav_section: Features
weight: 5
draft: false
---
A Canonical Member of a Fleet Contract is a Client Identity that has been added, via a transaction on the Diode Network, to the Fleet Contract.

Since Fleet Contracts are by default private (you cannot get a public listing of members), the <a href="https://diode.io/prenet/#/fleets" target="_blank" rel="noopener"><strong>Diode Network Explorer</strong></a> will "stage" a Client Identity in the Device ID list when one is added in order to test if the Client is already a part of it. If it is not, it will be staged and a separate transaction is required to make the new ID a persistent, "Canonical", Member.