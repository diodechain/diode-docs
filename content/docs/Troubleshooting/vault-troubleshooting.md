---
_schema: default
title: Vault Troubleshooting
nav_title: Vault Troubleshooting
nav_section: Troubleshooting
weight: 1000
draft: false
---
Please see the topics below for common problems and potential solutions:

### **Vault not joining Zone**

For a Vault to accept an invite to a Zone, the invitation MUST be sent by the person whose Username was paired with the Vault.

For Vault <a href="https://vaults.docs.diode.io/docs/vault-model-numbers/" target="_blank" rel="noopener"><strong>models 2312-NT and earlier</strong></a>, your Vault has be pre-configured to be paired to your Diode Collab Username. For these Vaults, please contact Diode Support who may be able to help provide information on the Username that is paired to your Vault.

### **Vault not Online**

If your Vault is not showing up as "green" (online) in your Zone, check the following:

* Confirm the Vault has successfully <a href="https://vaults.docs.diode.io/docs/using/vault-power-up-and-power-down-procedures/" target="_blank" rel="noopener"><strong>powered up</strong></a>
* Confirm the Ethernet router/switch is connected and the router/switch has access to the Internet
* Confirm the Local Area Network can provide, and has provided, a DHCP IP address to the Vault
* Confirm the Vault is actually part of your Zone - you can click the gear icon in your Zone, and go to the Team Members page - that page should list your Vault's Username.

### **Vault not Starting Up**

If the Vault is not <a href="https://vaults.docs.diode.io/docs/using/vault-power-up-and-power-down-procedures/" target="_blank" rel="noopener"><strong>fully starting up</strong></a>, check the following:

* SD Card is not present or is not fully seated. Please check that the SD Card shipped with your Vault is fully inserted in the SC Card slot.
* Harddrive is corrupted. If your Vault has been powered down unsafely, it is possible that the system harddrive can be corrupted. You can try disconnecting the Harddrive Bridge from the back of the unit and try to start up again. It will take around two minutes to startup without the Harddrive Bridge, and will not be able to access any of your Zones, but you should be able to tell that the system has otherwise started up because a &gt;3 second press of the power button will safely shut the system down.

### **Vault not Safely Powering Down**

If the Vault is not <a href="https://vaults.docs.diode.io/docs/using/vault-power-up-and-power-down-procedures/" target="_blank" rel="noopener"><strong>safely powering down</strong></a>, check the following:

* System not fully started. Be sure to wait at least 120 seconds after powering up the Vault to shut it back down again.
* Power LED blinks forever. If there is a problem in the startup for the system, the safe power down function may not work correctly. In this situation, the Power LED will blink forever, and the rest of the LEDs will not power off. This is likely due to a corrupted Harddrive or other hardware problem. Please contact Diode Support.