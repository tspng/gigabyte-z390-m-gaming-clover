# Clover Bootloader for Gigabyte Z390 M Gaming Build

For macOS Mojave Version 10.14.6 only.

## Hardware

- Gigabyte Z390 M Gaming, rev. 1.0, Bios F7
- Intel i7-8700k
- Gigabyte RX VEGA 56 GAMING OC 8G
- Corsair Vengeance LPX 32GB (2x16GB) 3200MHz

## BIOS Settings

1. Load optimized defaults
2. Chipset -> Internal Graphics: **Enabled**
3. M.I.T -> Advanced Memory Settings -> Extreme Memory Profile: **Profile1**

Adjust boot sequence and fan settings to your liking.


## Clover

ProductName: iMacPro1,1

TODO: Test 

rest *tbd...*

### iGPU acceleration

* remove WhateverGreen.kext
* Add clover ACPI patches 
    * GFX0 -> IGPU
    * HECI -> IMEI

### TODO

Not working:

* Sound (Realtek ALC892)
* Shutdown (it just reboots)
* Intel Power Gadget doesn't show iGPU?

Working:

* Sleep
* iGPU hardware acceleration
