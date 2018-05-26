# Create UEFI bootable USB
#### 1. Download [minimal or normal ISO](https://manjaro.org/community-editions/)
#### 2. Download [Rufus](https://rufus.akeo.ie/)
#### 3. Create bootable USB stick
* Select device
* Partition scheme: GPT
* Filesystem: FAT32
* Cluster size: Default
* Select ISO
* **Start** - and select `Write in DD Image mode`

# Boot up USB stick with Manjaro
#### 1. Check if BIOS (delete) is in UEFI mode and Secure boot is disabled
#### 2. Plug in USB stick and restart computer to boot options (F11)
#### 3. Select USB stick in boot options
#### 4. Choose `Boot: Manjarox.86_64_i3`
- In this menu you can setup drivers and keyboard language
- Manjaro live iso will start.

# Installation
#### 1. Lanunch installer in Manjaro welcome window
#### 2. Partitioning
I do not want to create swap partition, so select "Manual partitioning"
* Create GPT table
* Create EFI partition 
  - size: 300M
  - mount `/boot/EFI`
  - select `esi`
* Create root partition
  - size: rest of the disk
  - mount `/`
  - select `root`
#### 3. Install and restart 

# Create Swap File insted of Swap Partition
#### Create Swap File
Empty 4G swapfile
```
  # fallocate -l 4G /swapfile
```
Set rights to the swapfile
```
  # chmod 600 /swapfile
```
After creating the correctly sized file, format it to swap
```
  # mkswap /swapfile
```
Activate the swap file:
```
  # swapon /swapfile
```
Edit `fstab` to add an entry for the swap file
```
  # nano /etc/fstab
-------------------------------------------------
  /swapfile none swap defaults 0 0
```
#### Remove Swap File
To remove a swap file, it must be turned off first and then can be removed
```
  # swapoff -a
  # rm -f /swapfile
```
Finally remove the relevant entry from `/etc/fstab`



