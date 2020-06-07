# Hackintosh-ROG-STRIX-Z490I

Still working...

## Software

* Bootloader: OpenCore 0.5.9
* OS: MacOS Catalina 10.15.5 (19F96 / 2020-05-26)

## Hardware

* Motherboard: Asus ROG STRIX Z490-I
    * Ethernet: Intel I225-V 2.5Gbit
    * WiFi/BT: Intel AX201NGW
    * Audio: Realtek ALCS1220A
* CPU: Intel i7-10700k
* GPU: AMD Radeon VII / Intel UHD630
* RAM: Corsair Vengeance LPX DDR4 3200 32GB(16Gx2)
* Drive: Samsung 970 EVO Plus 500G

## EFI

### ACPI

* SSDT-AWAC
* SSDT-EC-USBX
* SSDT-PLUG
* SSDT-SBUS-MCHC

### Kexts

* VirtualSMC.kext `1.1.4`
* SMCProcessor.kext
* SMCSuperIO.kext
* Lilu.kext `1.4.5`
* WhateverGreen.kext `1.4.0
* AppleALC.kext `1.5.0`
* IntelMausi.kext `1.0.3`
* NVMeFix.kext `1.0.2`
* USBInjectAll.kext `0.7.5,opt`
* AppleMCEReporterDisabler.kext `opt`

## Credits

[OpenCore Desktop Guide](https://dortania.github.io/OpenCore-Desktop-Guide/)
[SchmockLord's build on Gigabyte Z490](https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-Gigabyte-Z490-Vision-D)
