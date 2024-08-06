---
_schema: default
title: Vault Power Up and Power Down Procedures
nav_title: Power Up and Power Down
nav_section: Using
weight: 2
draft: false
---
Read the following for recommended process and expected behavior when powering the Vault up and down.

Before unplugging your Vault, always safely shut it down by holding the power button down for 3-5 seconds (until the power button light begins to pulse).

Use an <a href="https://www.amazon.com/APC-Battery-Protector-Back-UPS-BE600M1/dp/B01FWAZEIU" target="_blank" rel="noopener"><strong>uninterruptible power supply</strong></a> to power your Vault to guard against unintentional power disruptions. For Vaults that have shipped with a warranty, the warranty is only valid if the Vault is powered with an uninterruptible power supply.

#### **Power Up**

Your Vault will startup when a power supply is attached and the power button is pushed.

During the startup process (ranges from 30 to 120 seconds), the system LEDs should behave as follows:

* **Power Button LED:** Immediately turns blue and stays solid blue for the duration.
* **Power LED:** Immediately turns red and stays solid red for the duration.
* **Activity LED:** Immediately turns on, blinks a few times, then blinks intermittently during startup, and then turns off when the system has fully initialized. Thereafter, when the system is active for any reason, the activity LED will blink on intermittently and then return to off when inactive.
* **Harddrive LED:** Immediately turns blue when powered on, blinks intermittently rapidly during startup, and then turns solid blue when the system has fully initialized. Thereafter, during file reading or writing activity, the Harddrive LED will blink off intermittently and return to solid blue when inactive.

If the system does not fully start after 120 seconds, please see the <a href="https://vaults.docs.diode.io/docs/troubleshooting/vault-troubleshooting/" target="_blank" rel="noopener"><strong>Vault Troubleshooting</strong></a> article.

#### **Power Down**

Your Vault will safely shutdown when the power button is held down for more than three seconds.

After the power button is held down for more than three seconds, the system LEDs should behave as follows:

* **Power Button LED:** It will begin to pulse slowly at first, and then more quickly 10 times, and then will turn off with the other LEDs.
* **Power LED:** It will blink off and then back on and then will turn off with the other LEDs.
* **Activity LED:** It will immediately begin intermittent blinking as the system prepares for shutdown, and then will blink periodically 10 times before turning off with the other LEDs.
* **Harddrive LED:** It will blink briefly as the system prepares for shutdown, and then will turn off with the other LEDs.

Once all LEDs have turned off, it is safe to remove the power supply from your Vault.

If the LEDs do not fully turn off after pushing the the power button for over five seconds, please see the <a href="https://vaults.docs.diode.io/docs/troubleshooting/vault-troubleshooting/" target="_blank" rel="noopener"><strong>Vault Troubleshooting</strong></a> article.

&nbsp;

&nbsp;