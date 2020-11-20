# Windows 10
---

## Creating a bootable USB installer via macOS

### Prerequisites
1. Download Windows 10 ISO [here](https://www.microsoft.com/en-us/software-download/windows10ISO)
2. Download and install UNetbootin [here](https://unetbootin.github.io/)

### Steps
1. Plug a USB drive into your Mac.
2. Open terminal and note down the identifier of USB drive. For this example, the identifier is `/dev/disk2`.
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
3. Open UNetbootin. Select **DiskImage** radio button, click "..." to select a bootable ISO image. In this case, find the Windows 10 ISO you just downloaded.
4. Choose **Type** as **USB Drive** and select the device name of your USB drive (From step 2). Click **OK** to start installing to the USB drive.
5. This process takes several minutes or longer, depending on the size of your selected ISO image.

# References
---
* https://www.top-password.com/blog/create-windows-10-bootable-usb-from-iso-on-mac/