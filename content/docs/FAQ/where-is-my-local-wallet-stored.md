---
_schema: default
title: Where is My Local Wallet Stored?
nav_title: Where is My Local Wallet Stored?
nav_section: FAQ
weight: 20005
draft: false
---
Diode client applications use a local "wallet" to store credentials that enable their trustless interaction with the Diode Network. The location of the wallet files are shown below.

Note that interactions with the <a href="https://diode.io/prenet/#/" target="_blank" rel="noopener"><strong>Diode Network Explorer</strong></a> authenticate via [**MetaMask**](https://cli.docs.diode.io/docs/faq/configure-metamask/).

### **Diode CLI**

**Linux** - /home/&lt;yourname&gt;/.config/diode/private.db

**Windows** - C:\\Users\\&lt;yourname&gt;\\AppData\\Roaming\\diode\\private.db

**MacOS** - /Users/&lt;yourname&gt;/Library/Application Support/diode/private.db

You can <a href="https://cli.docs.diode.io/docs/faq/how-do-i-use-a-different-wallet-for-the-diode-cli/" target="_blank" rel="noopener"><strong>specify a custom location for your wallet</strong></a> with the -dbpath argument.

### **Diode App (Diode Drive)**

**Linux** - /home/&lt;yourname&gt;/.config/ddrive/ddrive.sq3

**Windows** - C:\\Users\\&lt;yourname&gt;\\.config\\ddrive\\ddrive.sq3

**MacOS** - /Users/&lt;yourname&gt;/.config/ddrive/ddrive.sq3

You can <a href="https://app.docs.diode.io/docs/admin/change-profile-directory/" target="_blank" rel="noopener"><strong>specify a custom location for your wallet</strong></a> by replacing the folder "ddrive" with a file "ddrive" pointing to the new profile path.

---

&nbsp;