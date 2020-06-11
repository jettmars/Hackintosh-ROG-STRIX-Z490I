# Hackintosh-ROG-STRIX-Z490I

This repository is about hackintosh on **Asus ROG STRIZX Z490I**. 

**The project is not completely finished yet**

I'v done the basic installation, still working on it since some hardwares are not working and the experience is not perfect yet. If someone is interested in this project, your're welcomed to join me.

Anyone has the same board can use the EFI folder directly except the `EFI/OC/config.plist` file, you should generate your own SMBIOS info by following the [Comet Lake Guide](https://dortania.github.io/OpenCore-Desktop-Guide/config.plist/comet-lake.html#platforminfo). Highly recommended reading the whole [OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/) before start, and try to build step by step yourself.

## Hardware

* Motherboard: Asus ROG STRIX Z490-I
    * Ethernet: Intel I225-V 2.5Gbit
    * WiFi/BT: Intel AX201NGW
    * Audio: Realtek ALCS1220A
* CPU: Intel i7-10700/10700k
* GPU: Intel UHD630 / AMD Radeon VII
* RAM: Corsair Vengeance LPX DDR4 3200 32GB
* Drive: Samsung 970 EVO Plus

## Software

* Bootloader: OpenCore 0.5.9
* OS: macOS Catalina 10.15.5 (19F96 / 2020-05-26)

## What's working

- [x] Intel UHD630 (iGPU)
- [ ] AMD Radeon VII (dGPU)
- [x] Audio Realtek ALCS1220A
- [x] Intel I225-V 2.5Gb Ethernet
- [ ] Wifi/BT (BCM94360CS)
- [ ] USB
- [ ] Sleep/Wake
- [ ] Reboot/Shutdown


## Details

### GPU

* **iGPU Intel UHD630**, HDMI display output is ok, didn't test audio output since my monitor has no speakers.

* **dGPU AMD Radeon VII**, natively supported in macOS

### Ethernet 

Working with `FakePCIID_Intel_I225-V.kext`, I found this from **SchmockLord**'s repository, after add `FakePCIID.kext` and `FakePCIID_intel_I225-V.kext` to your Kexts folder and config.plist's Kernel path, add device-id `F2150000` to DeviceProperties path, then it works. Details in [Issue 2.5Gbit Ethernet (Intel I225-V) Don't work #8](https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-Gigabyte-Z490-Vision-D/issues/8).

### Wifi/BT

Working by using a m.2 B+M-Key adapter with Apple Airport Card BCM94360CS.

The onboard wireless network card Intel AX201NGW uses m.2 E-Key slot and CNVi protocol. I tried replace it with a m.2 A-Key BCM94352Z card, the slot is compatible but it didn't work even in windows, thanks to the CNVi thing 😓. At last, I used a m.2 B+M-Key adapter with Apple Airport Card BCM94360CS, Wifi/BT is working perfect now. Sadly, I have to give up a m.2 slot for SSD and the onboard ssd heat sink, while now I have two wireless network cards, one for macOS and one for windows.

The bluetooth can not be recognized by default, because it uses an onboard internal USB2.0 port for power supply. So USB map should be fixed first.

### USB

### Audio

At the beginning I'v tried every layout-id in the AppleALC Codec list that ALCS1220A support, device info is correct in system but no sound output.

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
* FakePCIID.kext (from RehabMan)
* FakePCIID_Intel_HDMI_Audio.kext (from RehabMan)
* FakePCIID_intel_I225-V.kext (from SchmockLord)

## Credits

* [OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/)
* [SchmockLord's build on Gigabyte Z490-D](https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-Gigabyte-Z490-Vision-D)
* [yilmazca's build on Asus Prime Z490-A](https://github.com/yilmazca/intel-i9-10900K-Asus-prime-Z490A-hackintosh)
