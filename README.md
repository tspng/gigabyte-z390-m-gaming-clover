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

### Not working

* Intel Power Gadget doesn't show iGPU?
* Some boot ACPI errors

        ACPI Error: Method parse/execution failed [\_TZ.TZ10._STA] (Node ffffff8051c25ba0), AE_AML_UINITIALIZED_LOCAL (20160938/psparse-632)
        ACPI Error: Method execution failed [\_TZ.TZ10._STA] (Node ffffff8051c25ba0), AE_AML_UINITIALIZED_LOCAL (20160938/uteval-183)

* Shutdown (it just reboots)


### Working

* Sound (Realtek ALC892)
* Sleep
* iGPU hardware acceleration

## Notes

* Do not use [OsxAptioFix2Drv-free2000](https://www.reddit.com/r/hackintosh/comments/cfjyla/i_unleashed_a_plague_upon_you_guys_and_i_am_sorry/)!