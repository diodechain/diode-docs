---
_schema: default
title: Did You Experience Any “inconsistency issues” When Using OpenSSL?
nav_title: “Inconsistency Issues” When Using OpenSSL?
nav_section: FAQ
weight: 20033
draft: false
---
<br>This question refers to the fact that the functions in OpenSSL could be different depending on different use cases (e.g. the function interface parameters could be different).

When choosing a secure communication channel, we looked at RLPx and TLS (OpenSSL). We decided to use OpenSSL, but forced it into using Secp256k1 to ensure both sides authenticate with their Eth wallet keys. But this means we are forcing OpenSSL to only accept Secp256k1 and self-signed certificates (self signed using the wallet key).

OpenSSL does support Secp256k1. However, not all TLS libraries and clients support Secp256k1 at this time. So this can lead to connection issues when not using OpenSSL. We will be researching other libraries such as ARMmbed, wolfSSL, and SChannel for that matter.