---
_schema: default
title: What is the BlockQuick(TM) Consensus Reputation Table?
nav_title: What is the BlockQuick(TM) Consensus Reputation Table?
nav_section: FAQ
weight: 20021
draft: false
---
<br>The [**BlockQuick**](https://network.docs.diode.io/docs/faq/what-is-blockquick-tm/) Consensus Reputation Table (CRT) is a key security policy which BlockQuick adopts when validating a block. The CRT is constructed on each client based on the last known block headers in a given time frame. For instance, in a Proof-of-Work (PoW) system the client will be able to construct the consensus reputation table by reading 100 previous block headers from the last known state of the blockchain. All past block headers of the blockchain can be validated on the client using the parent block checksum alone. Thus, clients are able to fetch these block headers from untrusted nodes as the data can be validated using the existing block header and its contained parent block hash.

To learn more, read our blog post about the <a href="https://diode.io/blockquick/blockquick-consensus-reputation-table-explained-19182/" target="_blank" rel="noopener"><strong>BlockQuick Consensus Reputation Table</strong></a>!