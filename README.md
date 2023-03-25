# SIMPLE DNSMASQ ADBLOCK SCRIPT
This is a simple init.d script for OpenWRT devices I made for myself to block ads 
by routing (using firewall rules) all unwanted DNS traffic (ports 53, 853 and 5353) to a loopback address.

- Automatically creates firewall rules and sets up any external configuration.
- Handles personal blocklists.
- Only handles dnsmasq-based blocklist files, so there's no unnecessary parsing.
  - The script, by default, downloads notracking's blocklist, but any blocklist can work if it has the following format: *address=/.../...*

## DEPENDENCIES
```
curl
ca-certificates
libustream-mbedtls 
```

## HOW TO
Download the init.d script and place it inside the /etc/init.d/ folder.

```curl https://raw.githubusercontent.com/1898Angelo/openwrt-dnsmasq-adblock/main/blocklist_update > /etc/init.d/blocklist_update```

Call the *start* command on the script and if everything is working correctly, you can add the same line to /etc/rc.local
to autostart the script on each reboot.

 ```/etc/init.d/blocklist_update start```
 
 ### ... UPDATE THE BLOCKLIST
 Simply call the *start* command or, if the autostart line was added to rc.local, reboot the router.
 
 ### ... BLOCK PERSONAL/OTHER DOMAINS
 Add any domain to /etc/__personalblocklist/DOMAINS; one per line.
 ```
reddit.com
twitter.com
...
 ```
 ### ... USE ANOTHER DNSMASQ-BASED DOMAINS BLOCKLIST
 Point the $BLOCKLIST_URL variable to any other blocklist.

 ## SOURCES
 NoTracking's Blocklist: https://github.com/notracking/hosts-blocklists
 
