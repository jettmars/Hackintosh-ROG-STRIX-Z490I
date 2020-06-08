# Hackintosh-ROG-STRIX-Z490I

This repository is about hackintosh on Asus ROG STRIZX Z490I. I know very little about hackintosh things, all I have done is follow the **[OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/)**. The basic installation has finished, I'm still working on it since some hardwares is not working and the user experience is not perfect yet.

I don't know how to do a complete functional test, if someone is interested in this project, your're welcome.

## Software

* Bootloader: OpenCore 0.5.9
* OS: macOS Catalina 10.15.5 (19F96 / 2020-05-26)

## Hardware

* Motherboard: Asus ROG STRIX Z490-I
    * Ethernet: Intel I225-V 2.5Gbit
    * WiFi/BT: Intel AX201NGW
    * Audio: Realtek ALCS1220A
* CPU: Intel i7-10700k
* GPU: AMD Radeon VII / Intel UHD630
* RAM: Corsair Vengeance LPX DDR4 3200 32GB
* Drive: Samsung 970 EVO Plus

## What's working

- [x] **iGPU Intel UHD630**, HDMI display output is ok, I'm not sure if the audio output is working since my monitor has no speakers.
- [ ] **dGPU AMD Radeon VII**, natively supported, my card is still on the way.
- [ ] **Audio ALCS1220A**, I'v tried every layout-id in the AppleALC Codec list, still not work.
- [x] **Ethernet Intel I225-V**, thanks for **SchmockLord's** work, details in [issue#8](https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-Gigabyte-Z490-Vision-D/issues/8).
- [ ] **Wifi/BT**, I tried replace the onboard card with a BCM94352Z card, it can be pluged in but not work even in Windows, thanks for the CNVI thing😓. So I bought a m.2 B+M-Key adapter with BCM94360CS, still on the way, if it work I had to give up a m.2 SSD.
- [x] **USB**, usb is working, I've done nothing and I don't know what should I test for detail.

## EFI

### ACPI

Compiled by following the [ACPI Guide](https://dortania.github.io/Getting-Started-With-ACPI/)

* SSDT-AWAC
* SSDT-EC-USBX
* SSDT-PLUG
* SSDT-SBUS-MCHC

### Kexts

* VirtualSMC.kext `1.1.4`
* SMCProcessor.kext `1.1.4`
* SMCSuperIO.kext `1.1.4`
* Lilu.kext `1.4.5`
* WhateverGreen.kext `1.4.0`
* AppleALC.kext `1.5.0`
* IntelMausi.kext `1.0.3`
* NVMeFix.kext `1.0.2`
* FakePCIID.kext & FakePCIID_intel_I225-V.kext

## Credits

* [OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/)
* [SchmockLord's build on Gigabyte Z490-D](https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-Gigabyte-Z490-Vision-D)
