---
_schema: default
title: Are my communications via the Diode Network encrypted?
nav_title: Are my communications encrypted?
nav_section: FAQ
weight: 20007
draft: false
---
While all sorts of communication can be accomplished at a low level with the Diode Network (encrypted and non-encrypted), Diode Collab, Diode CLI, and other applications Diode deploys use 256bit end-to-end encryption - specifically the elliptic curve [**secp256k1**](https://www.secg.org/sec2-v2.pdf) domain parameter for Diode Network server connections and E2E connections.

The [**Diode CLI**](https://cli.docs.diode.io/docs/features/cli-commands/)  has E2E encryption turned on by default, but can be controlled via the "-e2e=&lt;true/false&gt;" parameter.

<a href="https://network.docs.diode.io/docs/troubleshooting/inconsistency-issues-when-using-open-ssl/" target="_blank" rel="noopener"><strong>Related OpenSSL FAQ entry</strong></a>

&nbsp;