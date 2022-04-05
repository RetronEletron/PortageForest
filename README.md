# VoidOfPortage

## If you have an issue that happens with my gentoo builds, provided FROM this repository, that does -not- happen on official gentoo, please DO NOT open a bug report on Gentoo Forums or Gentoo bugs. Instead, contact me on Discord about the issue:

https://discord.gg/test

## Table of contents
- [Overview](#overview)
- [Tested Desktop Environments](#Tested-Desktop-Environments)
- [Notes](#notes)
- [Installation](#installation)


## Overview
This is a project providing gentoo stage4's as of the definition by the official gentoo wiki although it tweaks that a bit and is not only a basic tarball which provides a bootable system it's a complete tarball giving new users a desktop expierence like ubuntu etc.

## Tested Desktop Environments

Currently, We have tested:

Cinnamon (Works Perfectly)

KDE (Works Perfectly on X11 but Wayland is buggy)

TDE (Works perfectly from temporary usage)

Pantheon (Works fine from the stable branch although testing seems broken)

Deepin (Entirely broken not able to get installed unless heavy modifications to the ebuilds or complete new ones)

LXQT (Works perfectly)

LXDE (Works Perfectly)

Unity7 (Works perfectly from the stable branch testing was not tested)

XFCE 4 (Works perfectly)

Budgie From SarahMiaOverlay (Works perfectly but look at her gitlab for packages that may be useful to you)

GNOME 41 (Works great on both X11 and Wayland GNOME 42 not tested)

UKUI (Works great although may be a bit slow at some bits)

## Notes
- Vulkan Support is enabled
- X support is enabled
- All stage4's will be in the stable branch 
- There will be only openRC and Systemd support only.
- Only x86 and x64 support (No Other architecture supported)
- Base system only installed (For GNOME for example it would be only gnome-light and the base gentoo system and no additional packages)
- Only dosfstools btrfs-progs and e2fsprogs are installed by default. For More File System support visit https://wiki.gentoo.org/wiki/Filesystem 
- Only Support for AMD GPU's by default if you want to change support to nvidia etc go change the VIDEO_CARDS line in /etc/portage/make.conf

## Installation

1. Download a release from the [Releases](https://github.com/RetronEletron/VoidOfPortage/releases) page (Make Sure the Portable Live Media has 3-4gb of free space for safety).
2. Create a `/mnt/gentoo` directory if it does not exist by doing `sudo mkdir /mnt/gentoo`. (In a Live Portage Media)
3. Mount your root partition (Must be at least 15gb in size) to `/mnt/gentoo` by doing `sudo mount /dev/sdXY /mnt/gentoo`
4. Uncompress the file to `/mnt/gentoo` by doing `sudo tar -xJpf file.tar.xz -C /mnt/gentoo` 
5. Run `wget -nc https://raw.githubusercontent.com/RetronEletron/VoidOfPortage/main/gentoo-chroot && chmod 755 gentoo-chroot && sudo ./gentoo-chroot /mnt/gentoo`
6. Mount your EFI partition to /boot/efi by `mount /dev/sdXY /boot/efi` and if it does not exist run `mkdir /boot/efi`
7. Edit fstab by running `nano /etc/fstab` and make sure it has the root and EFI partition in it at least.
8. 
