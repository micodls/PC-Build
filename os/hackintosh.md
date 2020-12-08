# Hackintosh

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

## Credits

* [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
* [Hackintosh-ROG-STRIX-Z490I](https://github.com/jergoo/Hackintosh-ROG-STRIX-Z490I)