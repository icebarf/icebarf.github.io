---
title: "Documentation: Troubleshooting errors during dGPU passthrough"
date: 2025-07-29T02:55:26+05:30
draft: false
---

All of this information is mostly in context to libvirtd, virt manager, windows dgpu passthrough

## Networking

Issue: Could not start the network or whatever with dnscrypt-proxy installed on the system for DoH.

Solution:
```
  <dns enable="no"/>
```
Put this in Edit -> Connection Details -> Virtual Networks -> `network_name` (in sidebar) -> XML

Restart `libvirtd.service`.

Also, will need to setup Custom DNS in windows or whatever OS in VM after installing Ethernet drivers if doing NAT.

## XML Editing

Some changes that I edited into the XML configuration, after clicking apply—would straight up vanish.

The reason is because that these changes are validated and then reversed back to a valid config (previous state) if
they are not valid. I couldn't even edit the domain's xml schema because of some weird versioning issue.

When in doubt, just do `sudo virsh edit <domain>`. The domain is actually the vm's name.

## No mouse pointer after installing virtio guest tools

The mouse pointer is there but the display driver from the virtio guest tools somehow interferes with the thing.
My current solution was to connect an external display to my laptop and so i got output there. Then I disabled the
virtio display device from Windows Device Manager and used the external display to setup everything like IDD, IVSHMEM
and looking glass.

Then with the looking glass display setup, i just disconnected the external display since I didn't need it.

Alternative: setup the ivshmem stuff and looking glass stuff beforehand (download setups on linux and add them somehow to vm)
have a working looking glass setup and then install **virtio guest tools**, and then disable that device.

## Weird graphical issues after closing VM and switching back to host

Currently it is weird and I haven't figured out a solution, I sometimes have to restart my pc to fix it.

The drivers are probably to blame.

Current testing reveals that it happened like 1/8 times so far.