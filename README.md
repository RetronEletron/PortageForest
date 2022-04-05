# VoidOfPortage

## If you have an issue that happens with my gentoo builds, provided FROM this repository, that does -not- happen on official gentoo, please DO NOT open a bug report on Gentoo Forums or Gentoo bugs. Instead, contact me on Discord about the issue:

https://discord.gg/test

## Table of contents
- [Overview](#overview)
- [Tested Desktop Environments](#Tested-Desktop-Environments)
- [Notes](#notes)
- [Installation](#installation)
- [Building](#building)
- [FAQ](#faq)


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
- Zen Kernel only installed.
- intel-microcode is included to include microcode for people who are on Intel CPU's
- Using -O2 by default.

## Installation

1. Download a release from the [Releases](https://github.com/RetronEletron/VoidOfPortage/releases) page (Make Sure the Portable Live Media has 3-4gb of free space for safety).
2. Create a `/mnt/gentoo` directory if it does not exist by doing `sudo mkdir /mnt/gentoo`. (In a Live Portage Media)
3. Mount your root partition (Must be at least 15gb in size) to `/mnt/gentoo` by doing `sudo mount /dev/sdXY /mnt/gentoo`
4. Uncompress the file to `/mnt/gentoo` by doing `sudo tar -xJpf file.tar.xz -C /mnt/gentoo` 
5. Run `wget -nc https://raw.githubusercontent.com/RetronEletron/VoidOfPortage/main/gentoo-chroot && chmod 755 gentoo-chroot && sudo ./gentoo-chroot /mnt/gentoo`
6. Mount your EFI partition to /boot/efi by `mount /dev/sdXY /boot/efi` and if it does not exist run `mkdir /boot/efi`
7. Edit fstab by running `nano /etc/fstab` and make sure it has the root and EFI partition in it at least.
8. Install and configure grub. By default grub is installed but it needs to be installed and configured on your hardware to do this run `grub-install && grub-mkconfig -o /boot/grub/grub.cfg` if you want any modifications to the grub config file edit /etc/default/grub by doing `nano /etc/default/grub`
9. Editing /etc/portage/make.conf. Not Entire required but may be needed if you got a different gpu or want to add your own configurations or change the use flags to your preference (Note this may require huge amount of packages to be rebuilt) to edit /etc/portage/make.conf run `nano /etc/portage/make.conf`
10. Changing your root password. To do this just run `passwd` if your password is too short/unsecure you can edit /etc/security/passwdqc.conf by `nano /etc/security/passwdqc.conf` and change the top line to `min=1,1,1,1,1` than run `passwd` again and it should work.
11. Adding a user (Not Required but recommended). Adding a user is recommended due to having proper perms and not able to accidently break something. As well as some things may not work properly in root. To do this run `useradd -m -G audio,cdrom,floppy,portage,usb,video,wheel -s /bin/bash user && passwd user` Of course replace user with your actual user unless you want your user to be well user.
12. If you wish to enable bluetooth support run `systemctl enable bluetooth && systemctl start bluetooth` For Systemd and For OpenRC run `rc-update add bluetooth default && rc-service bluetooth start`

## Building

To Build your own stage4 first you need:
- A Gentoo system installed
If you don't have it follow https://wiki.gentoo.org/wiki/Handbook:X86 (x86) or https://wiki.gentoo.org/wiki/Handbook:AMD64 (x64)
After your done with that you can mount the root partition to a certain mount point for this example let's do /mnt/gentoo.
And when your done you can run `mksquashfs /path/to/compress output.sfs -b 131072 -comp xz` And your done! A Very basic stage4.

## FAQ
1. Why can't you add Deepin support? Well first of all if you would see the official deepin repository it hadn't been updated in nearly 2 years! (As of this writing) and the ebuilds are extremely unstable only some of them actually compile with my best efforts but most don't dde-kwin etc.
 
2. Why can't you add support for other init systems like runit? Well it is not easy to add support for those which aren't officially supported by gentoo by that i mean has a profile etc and even if i could the expierence would be terrible.

3. Why use the zen kernel? Well the zen kernel fits most users and has FSYNC support for gamers and has the anbox modules binder and ashmem which fit for people who like to use anbox or expierement with something that use those modules.
