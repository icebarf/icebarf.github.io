---
title: "Homelab"
date: 2026-02-18T16:18:52+05:30
# draft: true
_build:
  render: "always"
  list: "never"
toc: true
tocBorder: true
---

## Overview

This is an overview for my homelab, vps setup along with documentation for services
I provide myself, my friends and family.
My primary goal in later 2025 shifted to being independent from many services I used
in my daily life. It included having a place to watch media at, file and photo backups,
matrix homeserver, email, a git frontend etc.
I realize that I cannot switch away from everything immediately, or the cost to setup
something like email would be very high, getting it through filters, blocklists and such.
Therefore, I started with things simple to setup and use.

Before I could setup any services, I needed a machine that could act as my server. I needed
consistent internet access, storage and backup power to be reliable.

# Infrastructure

For my homelab, the infrastructure includes—a laptop, two external HDDs,
USB Drive Bay, two VPSes, 200Mbps home network link.

## Hardware

### Server Machine

A used Thinkpad T480 from 2018, relevant specifications:
- CPU: i5-8350U
- RAM: 16GB @2400MHz
- Storage: 512GB SSD
- GPU: Integrated Intel 620
- Ethernet: Intel Ethernet Connection I219-V (upto Gigabit speed)
- WLAN: Intel Dual Band Wireless-AC 8265, Wi-Fi 2x2 802.11ac + Bluetooth 4.1, M.2 card
- WWAN: Missing

### Disks

- WD Blue 1TB
- WD Blue 2TB
- Wav Link 12TB two disk drive bay

### Network

- 200 Mbps Up and Down wireless link (Primary) (behind CG-NAT)

## VPS

Out of security concerns, and also being forced by my ISP, I must proxy my services
through a tunnel using a machine that's exposed to the internet. That's where VPS(s)
come into play.

While Bandwidth is not a large concern for me as most of the time, I will access my
services through my home network. But services like media, and backup from the outside does
require a decent bandwidth and a good amount of volume.
Luckily, Oracle grants us 10TB of outbound volume limits[^1] on Always Free Tier accounts.

While oracle is practically a privacy nightmare, this is the only thing I can afford for free. I take
precautions to transfer everything encrypted via SSL, or the service I am exposing encrypts
its data in a secure manner. Nothing is physically stored on the VPSes and they just behave as
public network machines meant to prevent direct access.

### ARM VPS

This is the main VPS that I use to expose all my services. It has 3 Ampere A1 cores, 19GB RAM, 150GB storage.[^2]
More than enough for my needs.

Software it runs:
- [frp](https://github.com/fatedier/frp) - Tunnel/Reverse proxy program, the main link between my home machine and VPS
- nginx - Reverse proxy that interacts with the frp tunneled services
- [blocky-dns](https://github.com/0xERR0R/blocky) - DNS Proxy (kept independent from home server)
- matrix rtc calling[^3]

### x86 VPS

This is a secondary VPS, it has AMD based Compute VMs with 2 OCPU, 1 GB RAM, 50GB Storage.

Currently, it is used for:
- [uptime-kuma](https://github.com/louislam/uptime-kuma) - Status page and health check for exposed services on the other VPS

## Services

While I planned for many services as stated in [#overview](#overview). I only wish to
state the ones I've setup, working, and are exposed to the internet, in this section. The future plans are in the
[later plans section].

1. [Tuwunel](https://matrix.rdseed.in) - Matrix Homeserver
2. [Jellyfin](https://jellyfin.rdseed.in) - Media Server System
3. [Jellyseerr](https://seer.rdseed.in) - Media Requests Manager
4. [Copyparty](https://party.rdseed.in) - File Server
5. [Blocky DNS](https://dns.rdseed.in) - DNS Proxy


# References
[^1]: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm#freetier_topic_Always_Free_Resources_Outbound_Data_Transfer
[^2]: https://www.oracle.com/in/cloud/free/
[^3]: Setup with livekit, jwt and coturn as external TURN server, see: [tuwunel matrix RTC](https://matrix-construct.github.io/tuwunel/matrix_rtc.html) and [tuwunel TURN guide](https://matrix-construct.github.io/tuwunel/turn.html)