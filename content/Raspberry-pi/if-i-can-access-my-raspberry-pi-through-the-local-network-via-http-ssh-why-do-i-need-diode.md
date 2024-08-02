---
_schema: default
title: >-
  If I Can Access My Raspberry Pi Through The Local Network via HTTP/SSH, Why Do
  I Need Diode?
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
SSH: If you’re not local, Diode is the only choice. (SSH is not using PKI) \\ Usually nobody is checking the remote key - so Diode is better since you don’t have to.

HTTPS: Even if you’re local, there are security issues when using a self-signed certificate to accessing your Pi.