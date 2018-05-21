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
### 5. Setting up Arch repository mirrorlist
Make backup
```
  # cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.backup
```
Sort backup
```
  # sed -i 's/^#Server/Server/' /etc/pacman.d/mirrorlist.backup
  # rankmirrors -n 6 /etc/pacman.d/mirrorlist.backup > /etc/pacman.d/mirrorlist
```
### 6. Installing the Arch base files
This command will install base Arch linux system
```
  # pacstrap /mnt base 
```
Other options are `base-devel` for developer packages or parameter `-i` afte pacstrap
### 7. 
```
  # 
```
