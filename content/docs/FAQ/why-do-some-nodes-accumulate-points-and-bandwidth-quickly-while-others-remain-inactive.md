---
_schema: default
title: >-
  Why do some nodes accumulate points and bandwidth quickly, while others remain
  inactive?
nav_title: Why Some Nodes Grow Faster
nav_section: FAQ
weight: 20035
draft: false
---
This difference is due to how the Diode Network selects nodes to route traffic. Key factors include:

* **Same location or IP range:**
  * Nodes hosted in the same datacenter or network may compete with each other, reducing selection chances.
* **Low demand in the region:**
  * Nodes are only used when there's traffic nearby. If your area has low user activity, your node may stay idle.
* **Latency:**
  * Nodes with faster response times are prioritized.

**Pro tip:** Use the Diode CLI to publish content through your node. This helps verify it's reachable and increases its chances of being selected for routing.

Also see:

[Diode CLI](https://cli.docs.diode.io/)

[Diode Forum](https://forum.diode.io/t/my-node-is-running-and-my-dashboard-is-accessible-but-im-not-earning-any-points-why/95)