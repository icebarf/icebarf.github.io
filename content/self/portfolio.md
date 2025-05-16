---
title: "Portfolio"
date: 2025-05-16T22:52:43+05:30
draft: false
toc: true
tocBorder: true
---

## Open Source

1. GNU Emacs (Code Editor)
    - Fix bug where extraction of compressed elisp code failed when using pigz
    - Bug caused by inappropraite gzip stream end checking
    - Commit: [46b6d1](https://git.savannah.gnu.org/cgit/emacs.git/commit/?id=46b6d175054e8f6bf7cb45e112048c0cf02bfee9)

2. TLP (Laptop Power Management Utility)
    - Fix startup failure in TLP in certain environments (busybox)
    - Bug caused due to using non-portable options for POSIX utilities
    - Commit: [9f3ff4](https://github.com/linrunner/TLP/commit/9f3ff4eacde047e08080849948e87e800f610890)

***

## Personal Projects
- [sinkhole](https://github.com/icebarf/sinkhole) (wip)
    - Operating System Implementation from scratch
    - Core kernel: C++, x86 assembly | libc: C
    - Future goals: hybrid microkernel with focus on performance
- [perfmode](https://github.com/icebarf/perfmode)
    - A linux CLI tool for ASUS TUF Laptops, controlling fan modes and LEDs.
- [FORTH86](https://github.com/icebarf/FORTH86)
    - FORTH programming language implementation in x86\_64 assembly
    - Builds upon libx86
    - Implementation of forthress (Low Level Programming, Igor Zhirkov)
- [mister8](https://github.com/icebarf/mister8)
    - Third iteration of my chip-8 emulators/interpreters
    - Graphics and audio were implemented using Raylib
    - Tested with the standard timendus’ chip8 test suite
- [c8fontgen](https://github.com/icebarf/c8fontgen)
    - Tiny pixel editor for generating custom chip-8 fonts
    - Supports Light and Dark themes
- [telegram discord bridge](https://github.com/icebarf/telegram-discord-bridge)
    - A unidirectional bridge written using Python
    - Uses a regular discord bot and a telegram user account
    - Intended for cross-posting and scraping
