# Lenovo Thinkpad T470s Clover

## Introduction

Thinkpad T470s Hackintosh configuration. This repository contains the following folders:

- `EFI`: put this in your EFI partition in `EFI` folder, including `BOOT`, `CLOVER` & `APPLE` sub-folders

Tested on Catalina, `10.15` & `10.15.1` with the following hardware:

- Intel i5-7200U & i7-7600U
- Intel HD Graphics 620
- 1920x1080 (FHD)
- DDR4 2133 20G (4G x 1, 16G x 1)
- Dell Wireless 1560 (BCM94352z)
- 256GB NVMe SSD (Toshiba)

It's a `95%` working hackintosh, including:

- *Apfs* disk partitions: `ApfsDriverLoader-64.efi`
- Brightness control: [WhatEverGreen](https://github.com/acidanthera/WhateverGreen) kext
- Audio on speakers: [AppleALC](https://github.com/acidanthera/AppleALC) kext
- Graphical acceleration (QE/CI): [WhatEverGreen](https://github.com/acidanthera/WhateverGreen) kext
- Audio Jack connector
- SD card reader
- TrackPoint / Touchpad driver: [VoodooPS2](https://github.com/acidanthera/VoodooPS2).
- Trim enabled

## Bugs

- The trackpad buttons don't work. Trackpad speed is too slow
- Type-C only works as a charging port
- USB next to Ethernet doesn't work
- Fingerprint reader doesn't work

## Setup

### BIOS Settings

The BIOS must be properly configured before installing MacOS.

In `Security` menu, set the following settings:

- `Memory Protection > Execution Prevention`: **Enabled**
- `Virtualization > Intel VT`: **Disabled** (Can be enabled later)
- `Virtualization > Intel VT-d`: **Disabled** (Can be enabled later)
- `Secure Boot > Secure Boot`: **Disabled**
- `Anti-Theft > Current Setting`: **Disabled**
- `Anti-Theft > Computrace > Current Setting`: **Disabled**

In the `Startup` menu, set the following options:

- `UEFI/Legacy Boot`: **UEFI Only**
- `CSM Support`: **Yes**

Now you can go through the install. 

### Bootable USB Drive

The guide [how to create a Catalina USB Installer Drive](https://hackintosher.com/guides/how-to-make-a-macos-10-15-catalina-flash-drive-installer/) explains how to create a USB flash drive to install MacOS on your T470s.

### Copy EFI Folder to USB

Copy the content of the `EFI` folder provided here on your USB flash drive `EFI` partition. The EFI partition is usually hidden. Use the following command: `sudo diskutil mount diskXsX` (where X is the number of the disk and partition with EFI) to mount the EFI partition of your flash drive on your mac (it appears as a disk on the desktop once done).

### Install macOS

Install macOS by booting on the USB key. It takes about 30min. The computer will restart multiple times. Make sure to select `Install macOS ...` each time. Once installed, choose to boot from the local drive in Clover boot menu.

### What's next?

To finish the setup, you need to:

- **Copy EFI** folder from USB flash drive to local drive `EFI` partition (like you did for the USB drive). It will make the local drive bootable (so you can get rid of the USB drive now)

You're almost done! Reboot and enjoy macOS on your Thinkpad T470s.

## Miscellaneous

### Enter the Clover menu

This config has a Clover timeout of 0. In order to enter the Clover menu, after rebooting and passing the BIOS screen, repeatedly press `left` `right`. This will pausing booting and display the menu.

### Auxiliary Software

**Improving scrolling responsiveness**

Turn off 'inertia' in System Preferrences/accessibility/Pointer Control/Trackpad Options.

Install [Smart Scroll](https://www.marcmoini.com/sx_fr.html). under 'Scroll Wheel+' - Turn up 'Range for a single tick' to the max. (this gives the appearance that scrolling becomes more sensitive)
Then you can adjust the speed and inertia under the same tab.

**Fix Stuttering**

To solve the jittery mouse, increase the speed with [BetterTouchTool](https://folivora.ai/) to about '8'. The touchpad feels almost the same as on my MacBook now, but the scrolling is still slow and awful. I will solve it somehow!

## Changelog

[Available here](CHANGELOG.md)
