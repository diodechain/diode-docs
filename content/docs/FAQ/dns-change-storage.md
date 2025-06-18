---
_schema: default
title: Is every DNS change stored into the Blockchain forever?
nav_title: Is every DNS change stored into the Blockchain forever?
nav_section: FAQ
weight: 20011
draft: false
---
This question came from some comments from [**Hacker News**](https://news.ycombinator.com/item?id=20764104#20764865): “So every DNS change is stored into the blockchain, forever? Will you have to download terabytes and terabytes of the blockchain in order to serve as a node? Why is that kind of audit history necessary?”

You don’t necessarily need to store DNS changes into the blockchain. The blockchain will only keep the current state and would prune the changes. According to Diode’s blog posts, 20kb of storage is all it needs with BlockQuick, the newly developed light-client protocol. The point is less about storing the audit history, but more about preventing Man-in-the-Middle attacks and solving the timestamp-certificate chicken-egg problem.