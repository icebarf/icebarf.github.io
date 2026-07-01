---
title: "Projects"
date: 2025-05-16T22:52:43+05:30
draft: false
toc: true
tocBorder: true
---

## Resume
- [Software Developer](/documents/resume.pdf)

## Open Source Contributions

1. GNU Emacs (Code Editor)
    - Resolved a critical decompression vulnerability relating to cross-implementation gzip stream boundaries; engineered a robust verification check to ensure seamless compatibility with alternative implementations like pigz.
    - Commit: [46b6d1](https://git.savannah.gnu.org/cgit/emacs.git/commit/?id=46b6d175054e8f6bf7cb45e112048c0cf02bfee9)

2. [slash_tmp](https://codeberg.org/szejmon/slash_tmp) (HTTP Server)
    - Architected core architectural features including an HTTP chunked transfer encoding protocol, preventing high-concurrency server crashes by reducing memory footprint to O(1) relative to file size.
    - Implemented native POSIX/Linux signal handling routines to ensure graceful server shutdowns and daemon-like stability.
    - Enhanced network security and protocol compliance by integrating SSL (HTTPS) support and fixing payload mismatches.

3. TLP (Laptop Power Management Utility)
    - Fixed a critical startup initialization failure by refactoring non-POSIX compliant timeouts into standardized, portable alternatives, enabling reliable execution across non-GNU Linux environments.
    - Commit: [9f3ff4](https://github.com/linrunner/TLP/commit/9f3ff4eacde047e08080849948e87e800f610890)

***

## Personal Projects
- [sinkhole](https://github.com/icebarf/sinkhole) (wip)
    - Designed a monolithic operating system kernel featuring real-time physical memory mapping, dynamic allocation, and custom IDT/GDT initialization.
    - Integrated modern security standards by implementing compiler-level stack-smashing protection mechanisms alongside a minimal C++ runtime layer. Configured low-level serial I/O and BIOS VGA buffer for diagnostics.
- [perfmode](https://github.com/icebarf/perfmode)
    - Built a lightweight Linux CLI system utility interacting directly with ASUS Notebook kernel modules and ACPI platform profiles to regulate hardware fan states and power envelopes.
    - Delivered an early open-source solution providing hardware control for ASUS laptops before official driver software support was introduced, maintaining deep backwards compatibility with legacy third-party drivers.
- [FORTH86](https://github.com/icebarf/FORTH86)
    - Developed a high-performance, Turing-complete FORTH interpreter entirely in bare-metal x86_64 assembly language.
    - Engineered a custom standard library and wrote low-overhead re-implementations of standard C library (libc) routines to optimize execution speed and binary size.
- [silly_packer](https://github.com/icebarf/silly_packer)
    - Developed an optimized texture packing and asset serialization asset pipeline utility that compiles modular graphics into compressed, game-ready texture atlases.
    - Programmed an automated C++ header generator supporting static binary blob embedding and optional API wrappers for fluid integration into production game loops.
- [mister8](https://github.com/icebarf/mister8)
    - Engineered a third-generation CHIP-8 emulator and interpreter utilizing hardware-accelerated graphics and audio playback via the Raylib framework.
    - Validated functional correctness against the industry-standard timendus CHIP-8 test suite to ensure accurate opcode implementation and cross-platform compatibility.
- [c8fontgen](https://github.com/icebarf/c8fontgen)
    - Created a graphical pixel-editor utility optimized for designing custom bitmap fonts for CHIP-8 emulators, providing seamless clipboard integration and structured hexadecimal output parsing.
- [telegram discord bridge](https://github.com/icebarf/tgchannel-discord-bridge)
    - Architected a unidirectional messaging bridge facilitating cross-platform content distribution between Telegram and Discord.
    - Leveraged Python-based automation integrating Discord bot APIs with Telegram user account workflows to enable seamless cross-posting and content aggregation.
- [Homelab](/tech/homelab)
    - Provisioned and maintained a self-hosted cloud infrastructure platform leveraging bare-metal container runtimes (Docker/Podman) and secure network topologies.
    - Configured encrypted reverse-proxy routing via remote FRPS tunnels traversing Oracle Cloud infrastructure to securely expose decentralized communication endpoints (Matrix Homeserver).
    - Deployed high-availability local services including centralized media delivery systems (Jellyfin, *arr stack) and network-level security via BlockyDNS routing.
