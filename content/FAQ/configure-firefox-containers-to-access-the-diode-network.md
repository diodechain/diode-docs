---
_schema: default
title: Configure Firefox Containers to Access the Diode Network
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
There are many ways to <a href="https://cli.docs.diode.io/docs/using/access-web3-0-content-run-a-local-gateway/" target="_blank" rel="noopener"><strong>access various resources published to the Diode Network</strong></a>. The method covered in this article uses the official Firefox Container add-on to create a specific container within Firefox that can serve Diode Network content via the local Diode Network Proxy provided by the <a href="https://diode.io/solutions/cli/" target="_blank" rel="noopener"><strong>Diode CLI</strong></a> or the <a href="https://diode.io/solutions/app/" target="_blank" rel="noopener"><strong>Diode App</strong></a>.

#### **Part 1: Configure Firefox**

1\. Install the <a href="https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/" target="_blank" rel="noopener"><strong>Official Firefox Multi-Account Container Add-On</strong></a>

2\. Open the Container Add-On by clicking it's icon (shown below) in the top left of Firefox

![](/uploads/image-7.png)

3\. At the bottom of the Container Add-On pop-up, click "Manage Containers"

![](/uploads/image-8.png)

4\. Click "New Container" at the top, give it a Name, Color, and Icon, then click "OK".

![](/uploads/image-9.png)

5\. Click the name of the container you just created (in my case it will be "Diode Web3").

![](/uploads/image-10.png)

6\. Click "Advanced proxy settings"

![](/uploads/image-11.png)

7\. Click the "Enable" button

![](/uploads/image-12.png)

8\. Click "Allow"

![](/uploads/image-13.png)

9\. Insert `socks://localhost:57861` into the "Advanced proxy settings" field, then click "Apply to Container"

![](/uploads/image-14.png)

10\. If you've done everything correctly, you should see `socks://localhost:57861` shown under the "Advanced proxy settings" section, as shown below.

![](/uploads/image-15.png)

#### **Part 2: Configure your local Diode Network Proxy**

The easiest way to start your local Diode Network Proxy is to simply run the <a href="https://diode.io/solutions/app/" target="_blank" rel="noopener"><strong>Diode App</strong></a>. If you don't have the Diode App yet, you can install it [**here**](https://diode.io/solutions/app/). All you have to do is start the app and keep it running while you are accessing Web3 sites. Once you have installed and started the Diode App, you can proceed to Part 3 of this guide.

<a href="https://diode.io/solutions/app/" target="_blank" rel="noopener"><strong>Download the Diode App</strong></a>

Alternatively, the local Diode Network Proxy can be started using the <a href="https://diode.io/resources/download/" target="_blank" rel="noopener"><strong>Diode CLI</strong></a>. To do that, [**download the Diode CLI**](https://diode.io/resources/download/), open a terminal window, and run: <code>diode socksd -socksd_port 57861<br /></code><br>Keep this terminal window open while accessing Web3 sites.

#### **Part 3: Using the Connection**

1\. Open the Container Add-On by clicking it's icon (shown below) in the top left of Firefox

![](/uploads/image-16.png)

2\. From the container menu, select the container you created in Step 4 of Part 1. In my case, this is "Diode Web3" as shown below. After clicking on the container name, a new tab will open for the container you selected.

![](/uploads/image-17.png)

3\. Inside the new container tab, navigate to a .diode site using this format: `http://site-you-want-to-reach.diode`. Notice that `http` is used and NOT `https`.

Even without https, your connection is still secure via the Diode Network

4\. If the tab loads the desired diode site, then your connection is configured properly!

If it's not working for you, make sure that you followed these steps carefully and that you have the right .diode site address. If you're still having trouble, feel free to reach out by clicking the "Contact" button at the top right of the page.

---

&nbsp;