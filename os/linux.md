# Ubuntu
---

## Creating a bootable USB installer via macOS

### Prerequisites
1. Download Ubuntu ISO [here](https://ubuntu.com/download/desktop)
2. Download and install balenaEtcher [here](https://www.balena.io/etcher/)

### Steps
1. Plug a USB drive into your Mac.
2. Open balenaEtcher. User interface is straightforward.
3. **Select image**. Find the Ubuntu ISO you just downloaded.
4. **Select drive**. Choose your USB drive. Click **Flash**.
5. This process takes several minutes or longer, depending on the size of your selected ISO image.

### Resetting flashed USB
1. Open terminal and note down the identifier of USB drive. For this example, the identifier is `/dev/disk2`.
```
  $ diskutil list
  /dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *251.0 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                 Apple_APFS Container disk1         250.8 GB   disk0s2

/dev/disk1 (synthesized):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      APFS Container Scheme -                      +250.8 GB   disk1
                                 Physical Store disk0s2
   1:                APFS Volume Macintosh HD            212.6 GB   disk1s1
   2:                APFS Volume Preboot                 46.8 MB    disk1s2
   3:                APFS Volume Recovery                510.5 MB   disk1s3
   4:                APFS Volume VM                      2.1 GB     disk1s4

/dev/disk2 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *61.5 GB    disk2
   1:                 DOS_FAT_32 UNTITLED                61.5 GB    disk2s1
```
2. Use this command to reset your USB drive. Replace `N` by the corresponding disk number. For this case, it will be `/dev/disk2`
```
$ diskutil eraseDisk FAT32 UNTITLED MBRFormat /dev/diskN
```


# References
---
* https://medium.com/studevs/create-bootable-usb-media-in-ubuntu-using-balenaetcher-53f4b4010111
* https://github.com/balena-io/etcher/blob/master/docs/USER-DOCUMENTATION.md#recovering-broken-drives