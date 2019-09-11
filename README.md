# macOS-ThinkPad-X1C6

### Introduction

> This repository provides some necessary resources to install a copy of macOS on ThinkPad X1 Carbon 6th. There is no guarantee of success, therefore you are expected to find extra resources to meet your needs, and be responsible for any consequences. **For Machine Type 20KH Only**

### Sample Hardware Specifications

| Item                        | Description                                                 |
| --------------------------- | ----------------------------------------------------------- |
| Processor                   | Intel Core i7-8550U                                         |
| Graphics                    | Intel UHD Graphics 620                                      |
| Memory                      | Onboard 16GB LPDDR3 2133MHz                                 |
| Audio Codec                 | Realtek ALC 285                                             |
| WWAN                        | Sierra Wireless EM7455 (Qualcomm Snapdragon X7 LTE-A Modem) |
| WLAN/ Bluetooth             | Dell DW1560                                                 |
| Media Card Reader           | Realtek USB3.0 Card Reader                                  |
| Built-in Display Resolution | 2560x1440 (2K)                                              |

### Software Overview

#### Features

| Feature                              | Status | Dependency                                       |
| :----------------------------------- | ------ | ------------------------------------------------ |
| macOS Mojave 10.14.6                 | ✅      | `VirtualSMC.kext`, `Lilu.kext`,Clover Bootloader |
| App Store                            | ✅      | Apple ID                                         |
| iMessage/ FaceTime                   | ✅      | Whitelisted Apple ID, Valid SMBIOS               |
| iCloud                               | ✅      | Apple ID                                         |
| Siri                                 | ✅      | Apple ID                                         |
| iTunes Video Playback                | ✅      | `WhateverGreen.kext`                             |
| Continuty                            | ✅      | `BT4LEContiunityFixup.kext`                      |
| AirDrop                              | ✅      | `BT4LEContiunityFixup.kext`                      |
| Bluetooth                            | ✅      | `BrcmFirmwareRepo.kext`, `BrcmPatchRAM2.kext`    |
| TrackPoint                           | ✅      | Patched `VoodooPS2Controller.kext`               |
| TrackPad                             | ✅      | `VoodooPS2Controller.kext`                       |
| Built-in Keyboard                    | ✅      | `VoodooPS2Controller.kext`                       |
| Battery Percentage Indication        | ✅      | Patched `DSDT.aml`                               |
| Sleep                                | ⚠️      | -                                                |
| Hibernation                          | ❌      | -                                                |
| CPU Power Management (SpeedShift)    | ✅      | `CPUFriend.kext`,`CPUFriendDataProvider.kext`    |
| IGPU Power Management                | ❌      | -                                                |
| Filesystem (APFS/HFS+)               | ✅      | Use SATA M.2. SSD or a Compatiable PCIe SSD      |
| Ethernet                             | ✅      | `IntelMausiEthernet.kext`                        |
| AirPort Extreme (Wi-Fi)              | ✅      | Swapping Intel WLAN card to Dell DW1560          |
| Sierra Wireless EM7455               | ❌      | `Legacy_Sierra_QMI.kext`                         |
| Audio Recording                      | ✅      | `AppleALC.kext` with Layout ID = 11              |
| Audio Playback                       | ✅      | `AppleALC.kext` with Layout ID = 11              |
| Full Graphics Accleration (QE/CI)    | ✅      | `WhateverGreen.kext`                             |
| Micro SD Card Reader                 | ✅      | Patched `AppleUSBCardReader.kext`                |
| USB 3.1                              | ✅      | `USBInjectAll.kext` , `SSDT-UAIC.aml`            |
| Thunderbolt 3 Dock (Port Replicator) | ⚠️      | `SSDT-TB3.aml`                                   |

