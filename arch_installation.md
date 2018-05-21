# ARCH Linux installation 

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
