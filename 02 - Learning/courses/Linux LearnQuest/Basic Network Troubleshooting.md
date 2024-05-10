---
title: Basic Network Troubleshooting
created: 2023-12-06 08:53
aliases: 
tags:
  - coursera/linux-learn-quest
---
# Basic Network Troubleshooting

## Basic Network Troubleshooting Tools

Tools:
- Ping - see if you can reach another IP address
- Host, Dig, NsLookup - DNS lookup

## Ping

Ping works by sending one or more ICMP(Internet Control Message Protocol) Echo Request packages to a specified destination IP on the network and waits for a reply. When the destination receives the package, it responds with an ICMP echo reply

Example:
```sh
ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.  
--- 192.168.1.102 ping statistics ---  
16 packets transmitted, 0 received, 100% packet loss, time 15354ms
```

Options:
- `-c` - Specify the number of request packages
- `-I` - specify the network interface to use
- `-4` - Use IPv4
- `-6` - Use IPv6

## Host

Query DNS Information

Example:

```sh
host google.com
host 52.25.109.230
host -t ns google.com
```

Options:
- `-v` - verbose output
- `-t` - type of query