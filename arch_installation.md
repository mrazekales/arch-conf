# ARCH Linux installation 

## Pre-installation
### 1. Update the system clock
```
  # timedatectl set-ntp true
```
See `timedatectl status`
```
  # timedatectl status
```
### 2. Partition the disks 
Using `cfdisk`
```
  # cfdisk -z /dev/sda
```
Select `dos` 
Create only one partition, select
  `[ New ]` > select full size > `[ Primary ]`
  Create main martition bootable `[ Bootable ]`
  Write settings `[ Write ]` > type `yes`
  Now you can quit `[ Quit ]`
  
### 3. Format the partitions
Make file system
```
  # mkfs.ext4 /dev/sda1
```
### 4. Mount the file systems
```
  # mount /dev/sda1 /mnt
```
## Installation
### 1. Setting up Arch repository mirrorlist
Make backup
```
  # cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.backup
```
Sort backup
```
  # sed -i 's/^#Server/Server/' /etc/pacman.d/mirrorlist.backup
  # rankmirrors -n 6 /etc/pacman.d/mirrorlist.backup > /etc/pacman.d/mirrorlist
```
### 2. Installing the Arch base files
This command will install base Arch linux system
```
  # pacstrap -i /mnt base 
```
Other options are `base-devel` for developer packages

## System configuration
### 1. Fstab
Generate `fstab` file
```
  # genfstab -U /mnt >> /mnt/etc/fstab
```
Check it
```
  # nano /mnt/etc/fstab
```
### 2. Chroot
Change root into the new system
```
  # arch-chroot /mnt
```
### 3. Time-zone
Set the time zone
```
  # ln -sf /usr/share/zoneinfo/Europe/Prague /etc/localtime 
```
Run `hwclock` to generate `/etc/adjtime`
```
  # hwclock --systohc
```
### 4. Locale
Uncomment `en_US.UTF-8` and other needed localizations  `/etc/locale.gen`
```
  # nano /etc/locale.gen
```
Generate Locale
```
  # locale-gen
```
Set it as your language with
```
  # echo LANG=en_US.UTF-8 > /etc/locale.conf
  # export LANG=en_US.UTF-8
```
### 5. Hostname
Set computer hostname
```
  # nano /etc/hostname
---------------------------------
    myhostname
```
Add matching entries to hosts
```
  # nano /etc/hosts
-------------------------------------------------------
   127.0.0.1	  localhost
   ::1		      localhost
   127.0.1.1	  myhostname.localdomain	myhostname
```
If the system has a permanent IP address, it should be used instead of `127.0.1.1`
### 6. Root password
Create roo password
```
  # passwd
```
## Installing Grub bootloader
Install the `grub` package to replace `grub-legacy`
```
  # pacman -S grub
```
Install grub bootloader
```
  # grub-install --target=i386-pc /dev/sdX
```
