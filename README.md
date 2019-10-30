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

- *Apfs* disk partitions: using `ApfsDriverLoader-64.efi`
- Brightness control: Thanks to [WhatEverGreen](https://github.com/acidanthera/WhateverGreen) kext
- Audio on speakers: using [AppleALC](https://github.com/acidanthera/AppleALC) kext
- Graphical acceleration (QE/CI): thanks to [WhatEverGreen](https://github.com/acidanthera/WhateverGreen) kext
- Audio Jack connector
- SD card reader

## Bugs

- The trackpad buttons don't work. Trackpad speed is too slow
- Type-C only works as a charging port
- USB next to Ethernet doesn't work
- Fingerprint reader doesn't work

## Setup

### BIOS Settings

The bios must be properly configured prior to installing MacOS.

In `Security` menu, set the following settings:

- `Memory Protection > Execution Prevention`: **Enabled**
- `Virtualization > Intel VT`: **Disabled** (Can be enabled later)
- `Virtualization > Intel VT-d`: **Disabled** (Can be enabled later)
- `Secure Boot > Secure Boot`: **Disabled**
- `Anti-Theft > Current Setting`: **Disabled**
- `Anti-Theft > Computrace > Current Setting`: **Disabled**

In `Startup` menu, set the following options:

- `UEFI/Legacy Boot`: **UEFI Only**
- `CSM Support`: **Yes**

Now you can go through the install. 

### Bootable USB Drive

The guide [how to create a Catalina USB Installer Drive](https://hackintosher.com/guides/how-to-make-a-macos-10-15-catalina-flash-drive-installer/) explains how to create a USB flash drive to install MacOs on your T470s.

### Copy EFI Folder to USB

Copy the content of the `EFI` folder provided here on your USB flash drive `EFI` partition. The EFI partition is usually hidden. Use [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/) to mount the EFI partition of your flash drive on your mac (it appears as a disk on the desktop once done).

### Install macOS

Install macOS by booting on the USB key. It takes about 30min. The computer will restart multiple times. Make sure to select `Install macOS ...` each time. Once installed, choose to boot from local drive in Clover boot menu.

### What's next?

To finish the setup, you need to:

- **Copy EFI** folder from USB flash drive to local drive `EFI` partition (like you did for the USB drive). It will make the local drive bootable (so you can get ride of the USB drive now)

You're almost done! Reboot and enjoy macOS on your Thinkpad T470s.

## Miscellaneous

### SSD Enable Trim

If you Sata ssd hasn't trim enabled, run the following command from the *Terminal* to enable it:

```
sudo trimforce enable
```

### Touchpad / Trackpoint Kext

The trackpoint / Touchpad driver used here is the one from [tluck on Insanelymac](https://www.insanelymac.com/forum/topic/315451-guide-lenovo-t460-macos-with-clover/).

**Improving scrolling responsiveness**

Turn off 'inertia' at system-pref/accessibility/mouse & trackpad/trackpad options.

Insstall [Smart Scroll](https://www.marcmoini.com/sx_fr.html). under 'Scroll Wheel+' - Turn up 'Range for a single tick' to max. (this gives the appearance that scrolling becomes more sensitive)
Then you can adjust the speed and inertia under the same tab.

**Fix Stuttering**

To solve the jittery mouse, increase the speed with [BetterTouchTool](https://folivora.ai/) to about '8'. The touchpad feels almost the same as on my MacBook now, but the scrolling is still slow and awful. I will solve it somehow!

Special thanks to **Romeo Blues** for these tweaks. Those definitely improve how the touchpad feels!

### HiDPI

For FHD (1920x1080) panels, I recommend to install [One Key HiDPI](https://github.com/xzhih/one-key-hidpi).

### iMessage / iCloud / FaceTime

Make sure to following [this guide](https://hackintosher.com/guides/quick-fixes-facetime-icloud-imessage-hackintosh-not-working/) to configure iMessage, iCloud and Facetime properly. 

## Changelog

[Available here](changelog.md)
