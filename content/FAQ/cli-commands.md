---
_schema: default
title: Diode CLI Commands
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
### **Overview**

If you have the Diode Client installed, in a terminal window, you can type `diode` to get a list of commands and `diode <command> --help` to get detailed help via the command line.

```
Name
  diode - Diode network command line interface

SYNOPSYS
  diode [-allowlists=] [-api=false] [-apiaddr=localho...]
        [-bind=] [-blocklists=] [-blockprofile=] [-blockprofilerate=1]
        [-configpath=] [-cpuprofile=] [-dbpath=/Users/...] [-debug=false]
        [-diodeaddrs=] [-e2etimeout=15s] [-fleet=] [-logdatetime=false]
        [-logfilepath=] [-memprofile=] [-metrics=false] [-mutexprofile=]
        [-mutexprofilerate=1] [-pprofport=0] [-retrytimes=3] [-retrywait=1s]
        [-rlimit_nofile=0] [-timeout=5s] [-update=true] COMMAND <args>

COMMANDS
  bns          Register/Update name service on diode blockchain.
  config       Manage variables in the local config store.
  fetch       Fetch is the command to make http GET/POST/DELETE/PUT/OPTION request through diode network.
  gateway      Enable a public gateway server as is used by the "diode.link" website
  publish      Publish ports of the local device to the Diode Network.
  reset        Initialize a new account and a new fleet contract in the network. WARNING deletes current credentials!
  socksd       Enable a socks proxy for use with browsers and other apps.
  time         Lookup the current time from the blockchain consensus.
  token        Transfer DIODEs to the given address on diode blockchain.
  update       Force updating the diode client version.
  version      Print the diode client version.

Run 'diode COMMAND --help' for more information on a command.
```

### **diode bns**

```
Name
  diode bns -  Register/Update name service on diode blockchain.

SYNOPSYS
  diode bns <args>

ARGS
  -account string
    	Display the account information of a given BNS name
  -force
    	Force re-registration in case of registration, even if the name is already registered.
  -lookup string
    	Lookup a given BNS name.
  -register string
    	Register a new BNS name with <name>=<address>.
  -transfer string
    	Transfer an existing BNS name with <name>=<new_owner>.
  -unregister string
    	Free a new BNS name with <name>.
EXAMPLE
  diode bns -register hello-world=0x......
```

### **diode config**

```
Name
  diode config -  Manage variables in the local config store.

SYNOPSYS
  diode config <args>

ARGS
  -delete value
    	deletes the given variable from the config
  -list
    	list all stored config keys
  -set value
    	sets the given variable in the config
  -unsafe
    	display private keys (disabled by default)
EXAMPLE
  diode config -delete lvbn2 -delete lvbn
```

### **diode fetch**

```
Name
  diode fetch - Fetch is the command to make http GET/POST/DELETE/PUT/OPTION request through diode network.

SYNOPSYS
  diode fetch <args>

ARGS
  -data string
    	The http body that will be transfered.
  -header value
    	The http header that will be transfered.
  -method string
    	The http method (GET/POST/DELETE/PUT/OPTION). (default "GET")
  -output string
    	The output file that keep response body.
  -url string
    	The http request URL.
  -verbose
    	Print more information about the connection.
EXAMPLE
 diode fetch -method post -data "{'username': 'test', password: '123456', 'csrf': 'abcdefg'} -header 'content-type:application/json'"
```

### **diode gateway**

```
Name
  diode gateway -  Enable a public gateway server as is used by the "diode.link" website

SYNOPSYS
  diode gateway <args>

ARGS
  -additional_ports string
    	httpsd secure server ports
  -allow_redirect
    	allow redirect all http transmission to httpsd
  -certpath string
    	Pem format of certificate file path of httpsd secure server (default "./priv/cert.pem")
  -edge_acme
    	allow to use ACME generate certificates automatically
  -edge_acme_email string
    	ACME email configuration
  -fallback string
    	how to resolve web2 addresses (default "localhost")
  -httpd_host string
    	host of httpd server listening to (default "127.0.0.1")
  -httpd_port int
    	port of httpd server listening to (default 80)
  -httpsd_host string
    	host of httpsd server listening to (default "127.0.0.1")
  -httpsd_port int
    	port of httpsd server listening to (default 443)
  -privpath string
    	Pem format of private key file path of httpsd secure server (default "./priv/priv.pem")
  -proxy_host string
    	host of socksd proxy server (default "127.0.0.1")
  -proxy_port int
    	port of socksd proxy server (default 1080)
  -secure
    	enable httpsd server
  -socksd
    	enable socksd proxy server
EXAMPLE
  diode gateway -httpd_port 8080 -httpsd_port 443 -secure -certpath ./cert.pem -privpath ./priv.pem
```

### **diode publish**

```
Name
  diode publish -  Publish ports of the local device to the Diode Network.

SYNOPSYS
  diode publish <args>

ARGS
  -http
    	enable http static file server
  -http_dir string
    	the root directory of http static file server
  -http_host string
    	the host of http static file server (default "127.0.0.1")
  -http_port int
    	the port of http static file server (default 8080)
  -indexed
    	enable directory indexing in http static file server
  -private value
    	expose ports to private users, so that user could connect to
  -protected value
    	expose ports to protected users (in fleet contract), so that user could connect to
  -proxy_host string
    	host of socksd proxy server (default "127.0.0.1")
  -proxy_port int
    	port of socksd proxy server (default 1080)
  -public value
    	expose ports to public users, so that user could connect to
  -socksd
    	enable socksd proxy server
EXAMPLE
  diode publish -public 80:80 -public 8080:8080 -protected 3000:3000 -protected 3001:3001 -private 22:22,0x......,0x...... -private 33:33,0x......,0x......
```

### **diode reset**

```
Name
  diode reset -  Initialize a new account and a new fleet contract in the network. WARNING deletes current credentials!

SYNOPSYS
  diode reset <args>

ARGS
  -experimental
    	send transactions of fleet deployment and device allowlist at seme time
EXAMPLE
  diode reset
```

### **diode socksd**

```
Name
  diode socksd -  Enable a socks proxy for use with browsers and other apps.

SYNOPSYS
  diode socksd <args>

ARGS
  -fallback string
    	how to resolve web2 addresses (default "localhost")
  -socksd_host string
    	host of socks server listening to (default "127.0.0.1")
  -socksd_port int
    	port of socks server listening to (default 1080)
EXAMPLE
  diode socksd -socksd_port 8082 -socksd_host 127.0.0.1
```

### **diode time**

```
Name
  diode time -  Lookup the current time from the blockchain consensus.

SYNOPSYS
  diode time <args>

ARGS
  Empty
EXAMPLE
  diode time
```

### **diode token**

```
Name
  diode token -  Transfer DIODEs to the given address on diode blockchain.

SYNOPSYS
  diode token <args>

ARGS
  -balance
    	Just check the balance and quit.
  -data string
    	Data that will be submitted with the transaction.
  -gas string
    	Transfer gas paid to diode miner. (default "21000")
  -gasprice string
    	Transfer gas price paid to diode miner.
  -to string
    	The address or BNS name that DIODEs will be transfered to.
  -value string
    	Amount of DIODEs to be transfered.
EXAMPLE
  diode token -to 0x...... -value 1millidiode -gasprice 10gwei
```

### **diode update**

```
Name
  diode update -  Force updating the diode client version.

SYNOPSYS
  diode update <args>

ARGS
  Empty
EXAMPLE
  diode update
```

### **diode version**

```
Name
  diode version -  Print the diode client version.

SYNOPSYS
  diode version <args>

ARGS
  Empty
EXAMPLE
  diode version
```

&nbsp;

---

&nbsp;