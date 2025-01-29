---
_schema: default
title: Working with blockchain names
nav_title: Working with blockchain names
nav_section: Using
weight: 5
draft: false
---
BNS names are "blockchain name system" names (akak blockchain names).  You can register one or more addresses under a name, and every name has an owner.  The Diode CLI can be used to [register](https://cli.docs.diode.io/docs/using/working-with-blockchain-names/#register-name), [update](https://cli.docs.diode.io/docs/using/working-with-blockchain-names/#update-name), [lookup](https://cli.docs.diode.io/docs/using/working-with-blockchain-names/#lookup-name), inspect, [unregister](https://cli.docs.diode.io/docs/using/working-with-blockchain-names/#unregister-name), and [transfer](https://cli.docs.diode.io/docs/using/working-with-blockchain-names/#transfer-name) ownership of a blockchain name on the Diode Network.

Diode Collab can also register and manage BNS names - in Diode Collab, they are called "Domains".

Please node that the Diode CLI has partial support for Moonbeam BNS names, but some functionality may be limited.

The Diode CLI command to manage BNS names is:

> bns

invoked as:

> diode bns &lt;command&gt;

Read below for details!

### register name

> diode bns -register &lt;name&gt;=&lt;address(es)&gt;

Example - register one address to a name:

> diode bns -register mynewname=0x123229542c4afe8cd39da33f81bf698d57d3cb2a

Example - register two addresses to a name:

> diode bns -register mynewname=0x123229542c4afe8cd39da33f81bf698d57d3cb2a,0xa8721a541c4a2e8cd39d433f81af698d57d1ca33

### update name

To update a BNS name, your Diode CLI's address must be the owner of the name already.  If it is not, you must transfer ownership of the name to your CLI's address.

> diode bns -register &lt;name&gt;=&lt;updated address(es)&gt;

Example - update  a name with a single address:

> diode bns -register myoldname=0x123229542c4afe8cd39da33f81bf698d57d3cb2a

Example - update a name with two addresses:

> diode bns -register myoldname=0x123229542c4afe8cd39da33f81bf698d57d3cb2a,0xa8721a541c4a2e8cd39d433f81af698d57d1ca33

### lookup name

To lookup which addresses are registered under a name use "lookup".

> diode bns -lookup &lt;name&gt;

This will produce a list of "Lookup result" lines listing one address registered to the name per line.

### unregister name

If you no longer want to own a name, use "unregister".

> diode bns -unregister &lt;name&gt;

This will release the name and someone else will be able to register it.

### transfer name

If you want to give someone else the name, use "transfer".

> diode bns -transfer &lt;name&gt;=&lt;new owner&gt;

This will transfer ownership of the name to the new owner address.