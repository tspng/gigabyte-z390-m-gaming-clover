# Clover Bootloader for Gigabyte Z390 M Gaming Build

Tested only with macOS Mojave Version 10.14.6.


## Hardware

- Gigabyte Z390 M Gaming, rev. 1.0, Bios F7
- Intel i7-8700k
- Gigabyte RX VEGA 56 GAMING OC 8G
- Corsair Vengeance LPX 32GB (2x16GB) 3200MHz
- Broadcom BCM94360CD PCIe Adapter for Wi-Fi & Bluetooth 4.0


## BIOS Settings

1. Load optimized defaults
2. Chipset -> Internal Graphics: **Enabled**
3. M.I.T -> Advanced Memory Settings -> Extreme Memory Profile: **Profile1**

Adjust boot sequence and fan settings to your liking.


## Clover

TODO: add some explanation

### What Works

* Sound (Realtek ALC892)
* Sleep
* iGPU hardware acceleration
* Shutdown

### Open Issues

* Intel Power Gadget doesn't show iGPU?
* Lots of ACPI errors (like the following)
    * `ACPI Error: Method parse/execution failed [\_TZ.TZ10._STA] (Node ffffff8051c25ba0), AE_AML_UINITIALIZED_LOCAL (20160938/psparse-632)`
    * `ACPI Error: Method execution failed [\_TZ.TZ10._STA] (Node ffffff8051c25ba0), AE_AML_UINITIALIZED_LOCAL (20160938/uteval-183)`


## Notes

### iGPU acceleration

Initially, there was a bug when opening images with Preview or using QuickLook.
It looks like macOS uses the integrated GPU (iGPU) to render these images and if that's not present, it won't work.
After some testing, I could enable the iGPU with the following settings:

* enable internal graphics in Bios
* remove WhateverGreen.kext
* use `iMacPro1,1`
* use `0x3E920003` (or `AwCSPg==` when hex-swapped and base64 encoded) as `ig-platform-id`
* add clover ACPI patches 
    * GFX0 -> IGPU
    * HECI -> IMEI

### Shutdown fix

At first shutdown didn't work, it always rebooted instead.
The following changes fixed it for me:

* add EmuVariableUefi driver
* use `slide=0` boot arg

### Aptio Fixes

[Do not use OsxAptioFix2Drv-free2000](https://www.reddit.com/r/hackintosh/comments/cfjyla/i_unleashed_a_plague_upon_you_guys_and_i_am_sorry/) which many guides recommend for this motherboard.