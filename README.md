# (::) SECTHEMALL
SECTHEMALL is a bash script that distributes and syncs a **blacklist on all your linux server** using iptables.
It can store your logs to the SECTHEMALL cloud and make you able to create **correlation rules** or **graphical reports**.
With SECTHEMALL you can block **Brute Force Attacks, Port Scan, Web Vulnerability Scan**, and more...

## Index
- How it work
  - Read from file
  - Read command output
  - Cloud Correlation Rules
  - Block an IP to all your servers
  - Sync a server blacklist
- Requirements
- Installation

## How it work
![how it work](https://secthemall.com/img/secthemall-client-howitwork.001.jpeg)
secthemall is a bash script that can read a log file, or the output of a command, and set an iptables rule.
For example, it could reads your `/var/log/auth.log` and block an IP address that fails the ssh authentication for more then 6 times,
or it could read the `access.log` of your nginx server and block an IP address that get more then 20 "page not found" errors.

Each blocked IP address (IPv4 or IPv6) is added to an iptables rules chain and blocked (something like iptables -s <ipv4> -j DROP).
All blocked IPs will be sent to your global blacklist on secthemall.com and distributed on all your servers that run the secthemall.sh script.
Imagine that you have 3 linux server: a brute force attack blocked on the server A will be automatically blocked on servers B and C.

You can get a free account on secthemall.com in a few seconds, and start to use the secthemall.sh client.
You can see all your servers events on the secthemall online dashboard, where you can add or remove IP from your global black or white list.
You can also get graphical reports, create correlation rules, get notified by e-mail or telegram when an IP went in blackist, etc...

### How the client work
```sh
# ./secthemall.sh -h
+
+ (::) SECTHEMALL
+
+  --help or -h        Show this help
+  --start             Run client in foreground
+  --background or -b  Run client in background
+  --stop              Stop client
+  --restart           Restart client in background
+
+  --gbladd <ip>       Add <ip> to your Global Blacklist
+  --gbldel <ip>       Delete <ip> to your Global Blacklist
+  --gblshow           Show your Global Blacklist (json)
+  --gwladd <ip>       Add <ip> to your Global Whitelist
+  --gwldel <ip>       Delete <ip> to your Global Whitelist
+  --gwlshow           Show your Global Whitelist (json)
+
+  --lblshow           Show your Local Blacklist (iptables)
+  --lwlshow           Show your Local Whitelist (iptables)
+
+  --getlogs [-q ...]  Get collected logs from your nodes (json)
+


 Example usage:
 ./secthemall.sh --start -b         # this will start the client in background
 ./secthemall.sh --restart          # this will restart the client in background
 ./secthemall.sh --stop             # this will stop the client
 ./secthemall.sh --gbladd 1.2.3.4   # this will add 1.2.3.4 to all your nodes blacklist

```

### First: Authentication

### Using --start --stop --restart
asdasd





## Requirements
Keep in mind that SECTHEMALL is centrally orchestrated, so you need to create a **free** account on secthemall.com but don't worry... 
it takes just few seconds! The registration need only your e-mail address, secthemall.com do the rest.

The first time you run the `secthemall.sh` script, it check if all required components are present.
The secthemall client need:
- openssl
- iptables
- curl
- base64



## Thanks to
thanks to @maxtsepkov for [bash_colors](https://github.com/maxtsepkov/bash_colors)
