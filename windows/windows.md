# Windows 10

## Bootable USB Installer via macOS
---
* Prerequisites
  1. Download Windows 10 ISO [here](https://www.microsoft.com/en-us/software-download/windows10ISO)

* Steps
  1. Plug a USB drive into your Mac.
  2. Reformat USB drive via Disk Utilility.
  3. Mount `Windows 10 ISO`.
  4. Run the following in terminal:
      ```
      $ diskutil list
      $ diskutil eraseDisk MS-DOS "WINDOWS10" MBR /dev/diskN
      $ rsync -avh --progress --exclude=sources/install.wim /Volumes/CCCOMA_X64FRE_EN-US_DV9/ /Volumes/WINDOWS10
      $ brew install wimlib
      $ wimlib-imagex split /Volumes/CCCOMA_X64FRE_EN-US_DV9/sources/install.wim /Volumes/WINDOWS10/sources/install.swm 4000
      ```

## Installation
---
* Prerequisites
  1. Hackintosh is already installed in the SATA SSD drive

* Steps
  1. Physically disconnect SATA SSD drive where hackintosh is installed.
  2. Boot with Windows 10 bootable USB.
  3. BIOS Settings: `Default`
  4. Run `Windows Update` and restart if necessary.
  5. Install Broadcom drivers
     1. Wi-Fi
        1. Download and extract [Broadcom-FORCED-10x64-BCM43x_7.77.119.0-drp.zip](./drivers/Broadcom-FORCED-10x64-BCM43x_7.77.119.0-drp.zip)
        2. Right click on `Device Manager` -> `Other Devices` -> `Network Interface`.
        3. Choose `Update Drivers` -> `Browse my computer for drivers` and then find `bcmwl63.inf` in the deepest folder.
        4. After this, you will see `Wi-Fi 2` in your Wi-Fi options. This means that Broadcom Wi-Fi driver has been successfully installed.
        5. Optional: Disable the built in Intel Wi-Fi by right clicking on `Device Manager` -> `Connectivity` -> `Intel Wi-Fi`. After this, only one Wi-Fi should be seen in the Wi-Fi options.
        6. Restart.
     2. Bluetooth
        1. Download and extract [BCM943602CS.zip](./drivers/BCM943602CS.zip)
        2. Disable the built in Intel Bluetooth by righ clicking on `Device Manager` -> `Bluetooth` -> `Intel Bluetooth`. This causes conflict with the Broadcom bluetooth.
        3. Right click on `Device Manager` -> `Blueooth USB Host Controller` -> `Uninstall device`.
        4. Run the installer as admin found in `BCM943602CS` -> `Bluetooth Driver 2` -> `DPInst.exe`.
        5. Try connecting your bluetooth devices.
        6. Restart.
  6. Install ASUS Armoury Crate. You should see your Motherboard and ARGB devices. Restart afterwards.
  7. Install Radeon Software. Restart afterwards.
  8. Install latest ASUS Audio Drivers. Restart afterwards.

## Post Install
---
1. Change BIOS options back for hackintosh
  * Fast Boot: Disabled
  * Multi monitor mode: Enabled
2. Boot Priority
  * Windows first then macOS second to avoid conflicts.
  * NOTE: DO NOT BOOT INTO WINDOWS USING OC BOOTPICKER. THIS WILL CAUSE WINDOWS TO USE HACKINTOSH SMBIOS. Use F8 on start up to choose OS.

## Issues
* Both SSD's show as windows/bluescreen
  1. assign name for macos efi
  2. mount macos efi
  3. download total commander
  4. rename bootmgw to bootmgw-orig

## Credits
---
* https://www.youtube.com/watch?v=6wEOin8PclQ