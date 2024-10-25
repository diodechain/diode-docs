---
_schema: default
title: Using Diode CLI in Shell Scripts
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
### **tl;dr**

```
$ diode config 2>&1 | awk '/<address>/ { print $(NF) }'
0x55c8ee625db628b493b1d084afe25e962a570cdf
```

If you want to use the [**Diode CLI**](https://cli.docs.diode.io/docs/using/developers-network-cli-start-here/) in shell scripts be aware that most `[INFO]` output is written to **stderr** which by default is not catched by pipes. So if you want to use Diode CLI output in your script you might want to redirect **stderr** to **stdout**

### **For example extracting the client id:**

By default the `diode config` command shows all configuration values and exits:

```
$ diode config
[INFO] Diode Client version : v0.4.13 07 Oct 2020
[INFO] Client address       : 0x55c8ee625db628b493b1d084afe25e962a570cdf
[INFO] Fleet address        : 0x979d4824fefd8910c6db45ac45e956678fb04ed0
[INFO] <KEY>                : <VALUE>
[INFO] fleet                : 0x979d4824fefd8910c6db45ac45e956678fb04ed0
[INFO] last_update_at       : 0x5f847c04
[INFO] lvbh3                : 0x0000017b2dde638c7cb0e4df1f9dd5074bec640e41e230e8cabd58943fbe4853
[INFO] lvbn3                : 0x0d5b92
[INFO] <address>            : 0x55c8ee625db628b493b1d084afe25e962a570cdf
[INFO] private              : <********************************>
```

To extract from this only the local client address we first have to pipe the output to **stderr** and then filter only the address field value. We're using two operations here:

1. `2>&1` is a bash expression that redirects stderr to stdout
2. awk is a filter program and allows us to select a row and a field. In this case we're using the special constant NF (number of fields) as we want the last field in the &lt;address&gt; row:

```
$ diode config 2>&1 | awk '/<address>/ { print $(NF) }'
0x55c8ee625db628b493b1d084afe25e962a570cdf
```

Happy hacking!

---

&nbsp;