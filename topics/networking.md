---
title: Networking
search: true
---

# Networking

## ARP

On Linux, the ARP table can be displayed with `arp`. Entries can be deleted with `sudo arp -d <address>`. Use `sudo arp -a` to get system info.

## Routing

- `netplan apply` — apply netplan config
- `ip r(oute) add default via <IP>` — add default gateway
- `ip r(oute) del default via <IP>` — remove default gateway
- `ip r(oute) add <DESTINATION NETWORK ADDRESS>/<DESTINATION NETWORK LENGTH> via <NEXT HOP IP ADDRESS>` — add static route
- `ping [-c <count>] <IP>` — send packets and wait for echo
- `traceroute <IP>` — check route and hops

## netstat

`netstat -tupna` or `ss -stpluna`:

- `-s, --summary` — Print summary statistics. This option does not parse socket lists obtaining summary from various sources. It is useful when amount of sockets is so huge that parsing /proc/net/tcp is painful.
- `-t, --tcp` — Display TCP sockets.
- `-p, --processes` — Show process using socket.
- `-l, --listening` — Display only listening sockets (these are omitted by default).
- `-u, --udp` — Display UDP sockets.
- `-n, --numeric` — Do not try to resolve service names.
- `-a, --all` — Display both listening and non-listening (for TCP this means established connections) sockets.

Can be used with `watch <command>`.

## DNS

- `nslookup` — make DNS queries
-> `server <IP>` — set DNS server
-> `set type=<TYPE>` — set record type (e.g. A)
-> `domain` — query a domain
-> `exit` — leave this prompt
- `dig <domain> [type]` — query the default DNS server

## TShark

- `tshark` — capture network traffic to standard output
- `tshark -r <file>.pcap` — analyze network capture file
- `tshark -r <file>.pcap --export-objects <PROTOCOL>,<DEST-DIR` — export
- `tshark -r <file>.pcap "http.request.method == POST and http.file_data contains password"` — use filters
- `tshark -r <file>.pcap -T json` — specify output format

Use `grep [-B <lines_before>] [-A <lines-after>] "<search>"` as a filter.

