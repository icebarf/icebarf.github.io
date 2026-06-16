---
title: "Japanese Layout on KDE"
date: 2026-06-16T15:39:54+05:30
draft: false
toc: true
tocBorder: true
---

Since I've had to reinstall my desktop environment several times in the past couple of weeks,
I had no access to a Japanese layout to type with. I'm writing this to document how I setup a
custom fork of mozc with additional dictionaries, and integrating it into KDE along with a few env-vars,
and keybindings

This post will only highlight the things you need to place or setup.

## Keybinding Documentation

- ``Control + ` `` -- Activates IME/Deactivates IME to Direct Input Mode. (Moving from i.e Hiragana or katakana input back to English)
- `Contrl + Escape` -- Hiragana key emulation for Hiragana Input
- `Shift + Escape` -- Katakana key emulation for Katakana Input
- ``Alt + ` `` -- I use this for emulating Hankaku/Zenkaku and Hiragana/Katakana keys. Currently, mapped to the former.

## Installing mozc

I use [merge-ut-dictionaries](https://github.com/utuhiro78/merge-ut-dictionaries) which just builds `mozc`, and then later `fcitx5-mozc`.
You can also install `ibus-mozc` since it provides a `PKGBUILD` for that.

1. `$ git clone --depth 1 https://github.com/utuhiro78/merge-ut-dictionaries.git`
2. `$ cd merge-ut-dictionaries/src/merge`
3. Edit `make.sh`, I enable *all* of the dictionaries, as well generating the latest one as well. (Uncommenting)
4. `# pacman -S python-jaconv`
5. `$ sh make.sh`
6. `$ cd ../../PKGBUILD && cp ../src/merge/mozcdic-ut.txt ./`
7. `$ python3 generate-mozc-archive.py` (You may need to edit version number in this and PKGBUILD if it cannot find the release)
8. `$ makepkg -sip fcitx5-mozc-ut.PKGBUILD`
9. `# pacman -S --asdeps fcitx5-gtk fcitx5-configtool`

## Keyd

Keyd is a keyboard daemon program that allows you to remap keys at a kernel level, bypassing X11/Wayland garbage, resulting
in a quite portable setup.

- `/etc/keyd/default.conf`
```
[ids]
*

[main]
# Maps capslock to escape when pressed and control when held.
capslock = esc

# Remaps the escape key to capslock
esc = capslock

# Japanese stuff
control = layer(control)
leftalt = layer(alt)
shift = layer(shift)

[control]
capslock = hiragana

[shift]
capslock = katakana

[alt]
#` = katakanahiragana
` = zenkakuhankaku
```

## Environment Variables (fish)

- `$HOME/.config/fish/conf.d/env.fish`
```fish
# Input Method
set -gx GTK_IM_MODULE "fcitx"
set -gx QT_IM_MODULE "fcitx"
set -gx XMODIFIERS "@im=fcitx"
set -gx SDL_IM_MODULE "fcitx"
set -gx GLFW_IM_MODULE "fcitx"
```

## Plasma Settings
1. System Settings -> Virtual Keyboard -> Fcitx5

> There is also Fcitx5 Wayland Launcher, as of writing it is experimental and did not work with discord.
> I could have setup discord (chromium) with wayland flags at launch for IMs but then I would have to do it
> for every other electron based app, and instead opted for the default thing.

2. Sytem Settings -> Autostart -> Add New -> Fcitx 5

## `fcitx5-mozc` Configuration

This is configuration for mozc specifically, so it applies to the ibus version as well if you install, just the way to
access it would be different.

1. System Settings -> Input Method.
2. Shows Mozc in the list, click on **Configure** (Settings-like Icon)
3. Then scroll, and click on **Configuration Tool**
4. It should say **MS-IME** for **Keymap Style**, click on **Customize**
5. Click on the `Command` Tab to sort commands alphabetically
6. For `Activate IME` Command and `Direct Input` Mode, Replace `Eisu` with ``Ctrl+` ``
7. For `Deactivate IME` Command and `Precomposition` Mode, Replace `Hankaku/Zenkaku` with ``Ctrl+` ``
8. Click OK and apply all settings.


### Log out of Plasma and Log back in
