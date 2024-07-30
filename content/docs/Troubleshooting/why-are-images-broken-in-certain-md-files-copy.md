---
_schema: default
title: >-
  Why Don't I See My Miner Stake - How Long Will it Take For My Stake to Be
  Shown?
nav_title: Why Don't I See My Miner Stake?
nav_section: FAQ
weight: 502
draft: false
---
After running the <a href="https://support.diode.io/article/i44aeyjrzs" target="_blank" rel="noopener"><strong>console commands</strong></a> to stake Diode to my miner, my DIOs are gone but my staked DIOs are still 0 (checked with `Shell.get_miner_stake(me) `) - what is going on?

The Diode Network enforces a waiting time of 175200 blocks (roughly one month) as a safeguard against "hit and run" attacks on the network.

However, you can confirm you are mining via the shell `Stats.get(:hashrate)` - if you are successfully mining, the hashrate should be bigger than 0.