---
layout: post
title: "Wireguard"
---

## Wireguard
Wireguard is an alternative to OpenVPN and is opensource & fast. I've been using it with piVPN on raspberry pis to setup vpn networks and really rate it for its ease of use.

There are some excellent docs available at [https://github.com/pirate/wireguard-docs](https://github.com/pirate/wireguard-docs). 

One thing that was of particular interest to me was the ability to route a connection for 90% of your traffic through your main gateway and then particular IPs to go through your vpn tunnel.

This can be achieved by configuring the section: `AllowedIPs` where you can specify a CIDR range e.g 192.0.2.1/24. 

It should also be possible to configure the above through the use of iptables but the above is much easier to setup.

Therefore, using the above, one can setup a tunnel to a remote backup server such that the ip address is always reachable without routing all connections through that host.
