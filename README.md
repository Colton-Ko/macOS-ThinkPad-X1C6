# macOS-ThinkPad-X1C6

### Introduction

> This repository provides some necessary resources to install a copy of macOS on ThinkPad X1 Carbon 6th. There is no guarantee of success, therefore you are expected to find extra resources to meet your needs, and be responsible for any consequences. **For Machine Type 20KH Only**

### Objective

- Gather resources for a successful macOS installation on ThinkPad X1 Carbon 6th
- To prevent myself from forgetting how to instal macOS on ThinkPad X1 Carbon 6th
- To share the resources for others who might want to do the same thing

### Contents

1. English
   1. Hardware Specifications
   2. UEFI Setup Configuration
   3. Software Overview
      1. Guide Compatibility
      2. Features
   4. General installation procedure
   5. More to know
   6. Credits

### Hardware Specifications

| Item                        | Description                                                 |
| --------------------------- | ----------------------------------------------------------- |
| Processor                   | Intel Core i7-8550U                                         |
| Graphics                    | Intel UHD Graphics 620                                      |
| Memory                      | Onboard 16GB LPDDR3 2133MHz                                 |
| Audio Codec                 | Realtek ALC 285 (ALC3286)                                   |
| WWAN                        | Sierra Wireless EM7455 (Qualcomm Snapdragon X7 LTE-A Modem) |
| WLAN/ Bluetooth             | Dell DW1560                                                 |
| Media Card Reader           | Realtek USB3.0 Card Reader                                  |
| Built-in Display Resolution | 2560x1440 (2K)                                              |
| UEFI Firmware Version       | 1.41 (N23ET66W)                                             |
| Storage                     | Samsung 970 EVO Plus NVMe PCIe 3.0 x4 M.2. SSD              |



### UEFI Setup Configuration

**Only listing values that matters. Feel free to configure other values to suit your needs.**

| Item                         | Value    | Remarks                                           |
| ---------------------------- | -------- | ------------------------------------------------- |
| Secure Boot                  | Disabled | Unable to boot macOS if enabled                   |
| Thunderbolt 3 BIOS Assistant | Disabled | No Thunderbolt 3 if enabled                       |
| Wake on LAN                  | Disabled | Only 100M Ethernet if enabled                     |
| Boot mode                    | Both     | Enable UEFI Boot mode, you can leave CSM mode on. |



### Software Overview

#### Compatibility

- 10.14.x (macOS Mojave)
- 10.15 (macOS Catalina)

#### Features

| Feature                              | Status | Dependency                                                   |                                                              |
| :----------------------------------- | ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| macOS Mojave 10.14.6                 | ✅      | `VirtualSMC.kext`, `Lilu.kext`,Clover Bootloader             | v2.5k R5093                                                  |
| App Store                            | ✅      | Apple ID                                                     | -                                                            |
| iMessage/ FaceTime                   | ✅      | Whitelisted Apple ID, Valid SMBIOS                           | [Guide](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/) |
| iCloud                               | ✅      | Apple ID                                                     | -                                                            |
| Siri                                 | ✅      | Apple ID, Working audio recorder                             | Needs `AppleALC`                                             |
| iTunes Video Playback                | ✅      | `WhateverGreen.kext`, Apple ID (*Optional*)                  | -                                                            |
| Continuty                            | ✅      | `BT4LEContiunityFixup.kext`, Working Blutetooth and WiFi setup | -                                                            |
| AirDrop                              | ✅      | `BT4LEContiunityFixup.kext`, Working Blutetooth and WiFi setup | -                                                            |
|                                      |        |                                                              | Not tested                                                   |
| Bluetooth                            | ✅      | `BrcmFirmwareRepo.kext`, `BrcmPatchRAM2.kext`, `BrcmBluetoothInjector.kext` | -                                                            |
| TrackPoint                           | ✅      | Patched `VoodooPS2Controller.kext`                           | -                                                            |
| TrackPad                             | ✅      | `VoodooPS2Controller.kext`                                   | -                                                            |
| Built-in Keyboard                    | ✅      | `VoodooPS2Controller.kext`                                   | -                                                            |
| Battery Percentage Indication        | ✅      | Patched `DSDT.aml`                                           | Use [MaciASL](https://bitbucket.org/RehabMan/os-x-maciasl-patchmatic/downloads/) |
| Sleep                                | ❌      | -                                                            | Disabled                                                     |
| Hibernation                          | ❌      | -                                                            | Disabled                                                     |
| CPU Power Management (SpeedShift)    | ✅      | `XCPM`                                                       | -                                                            |
| IGPU Power Management                | ✅      | `XCPM`                                                       | -                                                            |
| Filesystem (APFS/HFS+)               | ✅      | Use SATA M.2. SSD or a Compatiable PCIe SSD                  | No NVMe Power Management                                     |
| PCIe Ethernet                        | ✅      | `IntelMausiEthernet.kext`                                    | -                                                            |
| AirPort Extreme (Wi-Fi)              | ✅      | Swapping Intel WLAN card to Dell DW1560                      | -                                                            |
| Sierra Wireless EM7455               | ❌      | `Legacy_Sierra_QMI.kext`                                     | No internet                                                  |
| Audio Recording                      | ✅      | `AppleALC.kext` with Layout ID = 11                          | -                                                            |
| Audio Playback                       | ✅      | `AppleALC.kext` with Layout ID = 11                          | -                                                            |
| Full Graphics Accleration (QE/CI)    | ✅      | `WhateverGreen.kext`                                         | -                                                            |
| Micro SD Card Reader                 | ✅      | Patched `AppleUSBCardReader.kext`                            | -                                                            |
| USB 3.1                              | ✅      | `USBInjectAll.kext` , `SSDT-UAIC.aml`                        | -                                                            |
| Thunderbolt 3 Dock (Port Replicator) | ✅      | `SSDT-TB3.aml`, `IOElectrify.kext`                           | -                                                            |
| Thunderbolt 3 Hotplug                | ✅      | `IOElectrify.kext`                                           | -                                                            |
|                                      | ✅      | ThinkPad Thunderbolt 3 Dock (40AC), `AppleRTL815XComposite109.kext` , `AppleRTL815XEthernet109.kext` | [Item page](https://support.lenovo.com/au/en/solutions/acc100356) |
| HiDPI *(Optional)*                   | ⚠️      | Shell Script from xzhih [Click Here](https://github.com/xzhih/one-key-hidpi) | May have werid scaling issues after wake up                  |



### General installation procedure

##### STEP 1: Create Installation Media

###### Checklist

- A working computer with macOS (or Mac OS X 10.7 or later)

- A working USB drive with 16GB or more capacity

- *Internet connection* (Not required if you already have the installer)

- A copy of macOS installation medium
  - For macOS Mojave click [here](http://dosdude1.com/mojave/) to get the application to download a copy of macOS Mojave installer.
  - For macOS Catalina click [here](http://dosdude1.com/catalina/) to get the application to download a copy of macOS Catalina installer.
  - Download macOS Catalina from the App Store

###### Procedure

1. Follow the gudie [here](https://support.apple.com/en-us/HT201372)
2. Copy boot files to the USB such that it is bootable on ThinkPad
   1. Mount EFI System partition using `diskutil`
      1. Check the identifier for the EFI System partition of the USB using `diskutil list`
      2. Mount it, e.g. `diskutil mount disk3s1`
      3. You should see a new `EFI` volume appeared in Finder, that is the EFI System partition of the USB.
   2. Copy boot files
      1. Go to the `EFI` folder of this repository
      2. Copy the entire `EFI` Folder to the root of the EFI System partition of the USB.
      3. You have copied the boot files.
   3. Finished. Move on to step 2.

##### STEP 2: Boot into installer

###### Checklist

- A working ThinkPad X1 Carbon 6th Type 20KH
  - **Permission to change boot order**
- A properly created macOS installer in a bootable USB (That you might have created in step 1)

###### Procedure

1. Plug in the USB Installer into the USB 3.0 Type A port of the ThinkPad.
2. Press F12 on your ThinkPad while it boots
3. Select your USB in the boot menu using arrow keys and press `Enter` to boot.
4. You should see a boot menu screen, select an item named 'Install macOS (version name) 'and press `Enter`
   1. `Install macOS Catalina` for macOS Catalina
   2. `Install macOS Mojave` for macOS Mojave
5. You should see long text running in a black background for some time, this is normal.
6. You should see macOS Installer menu, move on to step 3.

##### STEP 3: Partition your disks

###### Checklist

- A working ThinkPad X1 Carbon 6th Type 20KH
  - **Booted to macOS Installer**
- A properly created macOS installer in a bootable USB (That you might have created in step 1)

###### Procedure

1. Open Disk Utility
2. Partition your disks according to your wish and your needs
3. Format the partitions with `APFS` (Apple File System)
4. You have partitioned your disks. Move on to step 4.

##### STEP 4: Begin installation

###### Checklist

- A working ThinkPad X1 Carbon 6th Type 20KH
  - **Booted to macOS Installer**
  - **Created approproiate partitions for macOS installations**
- A properly created macOS installer in a bootable USB (That you might have created in step 1)

###### Procedure

1. Click Install macOS
2. Select the partition that you have created as the destination
3. Click install, the installation will start

###### Remarks

1. Your computer will restart for a few times
2. When the ThinkPad is restarted, repeat Step 2 to continue the installation
3. When the installation is completed, move on to Step 5.

##### STEP 5: Setup macOS

###### Checklist

- A working ThinkPad X1 Carbon 6th Type 20KH
  - **Installed a fresh copy of macOS**
- A properly created macOS installer in a bootable USB (That you might have created in step 1)

###### Procedure

1. Follow on-screen instructions to setup your macOS installation.
2. You should see macOS Desktop when you have finished, move on step 6.

##### STEP 6: Post Install Tweaks

###### Checklist

- Post installation materials
  - Located in `post` folder in this repository
- A working ThinkPad X1 Carbon 6th Type 20KH
  - **Installed macOS**

###### Procedure

1. Install required kernel extensions `kexts`
   1. Get the required materials
      1. Download and Open the `Kext` folder inside `post` folder in this repository
         - `post/Kext`
      2. Download kextbeast
         - Download [here](https://www.tonymacx86.com/resources/kextbeast-2-0-2.399/)
   2. Install the `kexts`
      1. Drag and drop all `kext` files from `post/kext` to your desktop
      2. Open Kextbeast
      3. Select `/Library/Extensions` as the package to install
      4. Click install and wait until a big green tick appeared on screen
      5. You have successfully installed the required kexts
   3. Copy boot files
      1. Mount EFI System partition using `diskutil`
         1. Check the identifier for the EFI System partition of the installation disk using `diskutil list`
         2. Mount it, e.g.`diskutil mount disk0s1`
         3. You should see a new `EFI` volume appeared in Finder, that is the EFI System partition of the installation drive.
      2. Copy boot files
         1. Go to the `EFI` folder of this repository
         2. Copy the entire `EFI` Folder to the root of the EFI System partition of the installation drive.
         3. Configure SMBIOS using the guide here: [Link](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/)
            1. System Model should be MacBookPro14,1
         4. You have copied the boot files.

### 

### More to know

- You may need to patch your DSDT
  - Follow guide here: [Link to Tonymacx86](https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/)
  - Patch files: [Link to tylerngyuen's Github repo](https://github.com/tylernguyen/x1c6-hackintosh)
- If iMessages or FaceTime does not work, here's what you can do
  - Follow gudie here: [Link to Tonymacx86](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/)
- You may want to improve the battery life
  - Follow guide here to enable native CPU/ GPU Power Management: [Link to Tonymacx86](https://www.tonymacx86.com/threads/guide-native-power-management-for-laptops.175801/)
  - Also note that there are currently no NVMe power managemenet for Hackintosh, use M.2. SATA if you care about battery life.
- If you have a ThinkPad Thunderbolt 3 Dock (Type 40AC) as I do
  - Download the requried software for working Ethernet
    - Link here: [Click me](https://gist.github.com/MadLittleMods/3005bb13f7e7178e1eaa9f054cc547b0)
- If you have other other suggestions
  - Talk on Github

### Useful utilities

- [Hackintool](https://www.tonymacx86.com/threads/release-hackintool-v2-8-0.254559/)
- [Kext Updater](https://www.insanelymac.com/forum/topic/334222-kext-updater-keep-your-kexts-fresh-with-only-one-click/)
- [Kext Beast](https://www.tonymacx86.com/resources/kextbeast-2-0-2.399/)
- [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/)
- [MaciASL](https://bitbucket.org/RehabMan/os-x-maciasl-patchmatic/downloads/)

### Credits

- Rehabman for most of the resources and guides
- Tonymacx86 as a discussion platform and hosts most resources
- P1LGRIM an iDiot's guide for iMessage
- tylerngyuen for ACPI patch files
- The darkvoid for macOS-IOElectrify, Link: [macOS-IOElectrify](https://github.com/the-darkvoid/macOS-IOElectrify)
- noobsplanet for Internal SD Card reader patch, Link: [Internal SD Card reader patch](https://noobsplanet.com/index.php?threads/fix-internal-external-card-reader-hackintosh-guide.32/)
- MadLittleMods for Ethernet on ThinkPad Thunderbolt 3 dock
- acidanthera for AppleALC, Link: [AppleALC](https://github.com/acidanthera/AppleALC)
- acidanthera for Lilu, Link: [Lilu](https://github.com/acidanthera/Lilu)
- acidanthera for WhateverGreen, Link: [WhateverGreen](https://github.com/acidanthera/WhateverGreen)
- xzhih for one-key-hidpi, Link: [one-key-hidpi](https://github.com/xzhih/one-key-hidpi)
- headkaze for Hackintool
- Sascha77 for Kext Updater
- MacMan for Kext Beast
- Mackie100 for Clover Configurator
- All contributors in the hackintosh community

Last update: 2019-10-16