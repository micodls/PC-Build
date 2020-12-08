# Hackintosh

## Hardware
* Asus Strix z490-i
* Intel i5-10600K
* Sapphire Nitro+ rx5700XT

## Software

* Bootloader: OpenCore 0.6.4-DEBUG
* OS: macOS Catalina 10.15.7 (19H15)

## Initial EFI and Installation

The installation guide in the [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/) are quite clear and easy, so there will be no detailed installation tutorials here. Give it some patience and you can build your own EFI.

### Tools
* [gibMacOS](https://github.com/corpnewt/gibMacOS)
* [MountEFI](https://github.com/corpnewt/MountEFI)
* [ProperTree](https://github.com/corpnewt/ProperTree)
* [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)
* [Sanity Checker](https://opencore.slowgeek.com/)

### BIOS

Version: 0607

#### Disable

* Fast Boot
* VT-d
* Launch CSM
* Software Guard Extensions (SGX)
* CFG Lock (no option in BIOS, Asus Z490 motherboards are factory unlocked. The `AppleCpuPmCfgLock` and `AppleXcpmCfgLock` quirks are not necessary)

#### Enable

* VT-x (no option in BIOS, it's enabled by default)
* Above 4G Decoding
* XHCI Hand-off
* Hyper-Threading
* OS type: Other OS or OS type: Windows UEFI Mode (if secure boot is disabled)
* OS type: Windows UEFI Mode (Clear Secure Boot Keys or choose `Other` type)
* DVMT Pre-Allocated: 64MB
* SATA Mode Selection: AHCI

## Post Install

### Screenshots
### Tools
* [neofetch]()
* [hackintool]()

### Audio

* Hardware: Realtek ALCS122A

### Before Fixes

### Tools
* [gfxutil]()
* [FakePCIID kexts]()

#### Fixes

##### Choppy audio
1. Insert result of gfxutil -f HDEF in config.plist
2. Update config.plist -> DeviceProperties -> Add
PciRoot(0x0) | Dictionary
layout-id | Number | 7 (or try other layout ids)

##### Intel HDMI Audio not showing
1. Insert FakePCIID.kext and FakePCIID_Intel_HDMI_Audio.kext in your kexts folder. Update config.plist (cmd + R)
2. Update config.plist -> DeviceProperties -> Add
PciRoot(0x0) | Dictionary
device-id | Data | <709D0000>

#### After Fixes

#### Issues
1. Only 1 audio output port is working (Front Panel connector)
2. Audio input not yet tested

### DRM

#### Before Fixes

* Hardware accelaration works out of the box
* FairPlay 1.x works
* FairPlay 2.x/3.x works
* FairPlay 4.x - not tested

#### Tools
* [VDADecoderChecker]()
* [VideoProc]()
* [Google Chrome]()

#### Fixes
1. None

#### Issues
1. iGPU showing in videoproc instead of dGPU


### iGPU

* Hardware: Intel UHD Graphics 630

### Before Fixes

### Tools

#### Fixes

##### iGPU not showing in hackintool
1. Update config.plist -> DeviceProperties -> Add
PciRoot(0x0) | Dictionary
device-id | Data | <9B3E0000>

##### Intel HDMI Audio
1. Insert FakePCIID.kext and FakePCIID_Intel_HDMI_Audio.kext in your kexts folder. Update config.plist (cmd + R)
2. Update config.plist -> DeviceProperties -> Add
PciRoot(0x0) | Dictionary
device-id | Data | <709D0000>

#### After Fixes


### dGPU

* Hardware: Sapphire Nitro+ rx5700XT
* Works out of the box

### Before Fixes

### Tools
* [RadeonBoost kexts]() - not working

#### Fixes

#### After Fixes

#### Benchmarks
Cinebench


Geekbench

### Wi-Fi

* Hardware: BCM
* Works out of the box
* No kexts needed

### Before Fixes

### Tools

#### Fixes

#### After Fixes


### Bluetooth

* Hardware: BCM

### Before Fixes

### Tools

#### Fixes

##### Can't search devices/Can't toggle on or off
1. USB Mapping needed

#### After Fixes
### Ethernet

* Hardware: Intel I225-V 2.5Gbit

### Before Fixes

### Tools

#### Fixes

##### Not showing in network preferences
1. Download FakePCIID.kext and FakePCIID_Intel_I225-V.kext in your kexts folder. Update config.plist (cmd + R)
2. Change config.plist -> DeviceProperties -> Add
PciRoot(0x0)/Pci(0x1C,0x1)/Pci(0x0,0x0) | Dictionary to PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0) | Dictionary
3. Update config.plist -> DeviceProperties -> Add
PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0) | Dictionary
device-id | Data | <F2150000>

#### After Fixes

#### Issues
1. Not tested with ethernet cable

iService - not yet tested
Power Management - oob
Sleep/Wake - oob
## Credits

* [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
* [Hackintosh-ROG-STRIX-Z490I](https://github.com/jergoo/Hackintosh-ROG-STRIX-Z490I)