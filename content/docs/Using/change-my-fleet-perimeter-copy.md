---
_schema: default
title: Host a Diode Server (Point of Presence) Node
nav_title: Host a Diode Server
nav_section: Using
weight: 3
draft: false
---
Anyone can run a Diode Server node (a Diode Point of Presence) and help expand the reach of the Diode Network. Here are some reasons why you may want to host your own Diode Server node:

1\. You want to help others connect E2EE in your region

If even a single Diode Server node is running in a region, it can route the E2EE traffic to other end points in the region, or to end points in other regions. Adding a node in a new or congested region can make connecting using Diode more performant for endpoints in that area.

2\. To further isolate your own endpoint traffic

Every Diode client can be configured to prefer/require certain server node routes. If you host your own node, you can also configure your clients to use your "in-house" node. This can give your application the same smart contract perimeter governance and global routing, but can also have better speed, routing privacy, economic benefits, and enterprise integrations.

3\. To collect "traffic tickets"

All traffic in the Diode Network is metered, and "traffic tickets" are issued by the Diode Server node who handled the traffic and are signed by the endpoints who requested the traffic. These tickets are automatically submitted to the network by each node at the end of the month in return for tokens. The tokens the network issues are automatically added to the node's wallet and can be transferred at any time by the owner.

4\. For learning and fun!

Getting going with a Diode Server node is an interesting and practical way to get into blockchain and to learn about one of the world's leading communications technologies.

### **To get started**

If you have experience running an Ethereum or EVM compatible node, jump right in and download and run the node from our github:

* <a href="https://github.com/diodechain/diode_server/blob/master/README.md" target="_blank" rel="noopener"><strong>Diode Server Github Repo</strong></a>

If you want something more "contained", checkout the docker project our integration partner, <a href="https://derateknoloji.com/" target="_blank" rel="noopener"><strong>Dera Technologies</strong></a>, maintains for running a node on <a href="https://akash.network/" target="_blank" rel="noopener"><strong>Akash</strong></a> (and other environments!):

* <a href="https://github.com/DeraTechDesign/Diode_Server_Docker" target="_blank" rel="noopener"><strong>Diode Server Docker</strong></a>

The project can use validator snapshots to accelerate the process of joining the network as a full node - join our [**Telegram channel**](https://t.me/diode_chain) to discuss

<a href="https://contactdiode.paperform.co/" target="_blank" rel="noopener"><strong>Contact us</strong></a> if you want to learn about how Diode (or one of our partners) can host a private managed node on your behalf!