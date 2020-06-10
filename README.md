# Hackintosh-ROG-STRIX-Z490I

This repository is about hackintosh on **Asus ROG STRIZX Z490I**. The basic installation has finished, I'm still working on it since some hardwares are not working and the experience is not perfect yet. If someone is interested in this project, your're welcomed to join me.

**Note:** Anyone has the same board can use the EFI folder directly except the `EFI/OC/config.plist` file, you should generate your own SMBIOS info by following the [Comet Lake Guide](https://dortania.github.io/OpenCore-Desktop-Guide/config.plist/comet-lake.html#platforminfo). Highly recommended reading the whole [OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/) before you start, and try to build step by step yourself.

## Software

* Bootloader: OpenCore 0.5.9
* OS: macOS Catalina 10.15.5 (19F96 / 2020-05-26)

## Hardware

* Motherboard: Asus ROG STRIX Z490-I
    * Ethernet: Intel I225-V 2.5Gbit
    * WiFi/BT: Intel AX201NGW
    * Audio: Realtek ALCS1220A
* CPU: Intel i7-10700/10700k
* GPU: Intel UHD630 / AMD Radeon VII
* RAM: Corsair Vengeance LPX DDR4 3200 32GB
* Drive: Samsung 970 EVO Plus

## What's working

- [x] **iGPU Intel UHD630**, HDMI display output is ok, didn't test audio output since my monitor has no speakers.
- [x] **Ethernet Intel I225-V**, thanks for **SchmockLord**'s repo, details in [issue#8](https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-Gigabyte-Z490-Vision-D/issues/8).
- [x] **Shutdown/Restart**

## TODO

- [ ] **USB**, working for USB flash disk. USB map need to be done.
- [ ] **dGPU AMD Radeon VII**, natively supported, my card is still on the way.
- [ ] **Audio ALCS1220A**, I'v tried every layout-id in the AppleALC Codec list, still not work, I can see the right device in system but no sound output.
- [ ] **Wifi/BT**, I tried replace the onboard card with a m.2 A-Key BCM94352Z card, it can be pluged in but not work even in Windows, thanks for the CNVI thing😓. So I bought a m.2 B+M-Key adapter with Apple Airport Card BCM94360CS, Wifi is working perfect now, but the bluetooth can not be recognized, I'll try to fix USB map later and see. Sadly, I have to give up a m.2 slot for SSD and the ssd heat sink onboard, while now I have two wireless network cards, one for macOS and one for windows✌🏻.
- [ ] Optimizing Power Management
- [ ] Fixing CFG Lock
- [ ] Setting up OpenCore's GUI

## EFI

### SSDTs

Compiled by following the [ACPI Guide](https://dortania.github.io/Getting-Started-With-ACPI/), the `.dls` SSDT files can be found in SSDTS folder. According to the guide, SSDT-PMC is used for NVRAM support, but desktop Z490 boards **DO NOT** need it, so it's not included in ACPI. 

* SSDT-AWAC.aml
* SSDT-EC-USBX.aml
* SSDT-PLUG.aml
* SSDT-SBUS-MCHC.aml

### Kexts

All kexts with version tag are downloaded from original repositories.

* VirtualSMC.kext `1.1.4`
* SMCProcessor.kext `1.1.4`
* SMCSuperIO.kext `1.1.4`
* Lilu.kext `1.4.5`
* WhateverGreen.kext `1.4.0`
* AppleALC.kext `1.5.0`
* IntelMausi.kext `1.0.3`
* NVMeFix.kext `1.0.2`
* FakePCIID.kext & FakePCIID_intel_I225-V.kext

## Installation

I'll add installation details after the work is completely done.

## Credits

* [OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/)
* [SchmockLord's build on Gigabyte Z490-D](https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-Gigabyte-Z490-Vision-D)
* [yilmazca's build on Asus Prime Z490-A](https://github.com/yilmazca/intel-i9-10900K-Asus-prime-Z490A-hackintosh)
