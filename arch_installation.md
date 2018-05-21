# ARCH Linux installation 

### 1. Update the system clock
```bash
  # timedatectl set-ntp true
```
See `timedatectl status`
```bash
  # timedatectl status
```
### 2. Partition the disks 
Using `cfdisk`
```bash
  cfdisk -z /dev/sda
```
Select `gpt` for UEFI or 2TB or more disks, otherwise select`dos` 
Create only one partition, select
  `[ New ]` > select full size > `[ Primary ]`
  Create main martition bootable `[ Bootable ]`
  Write settings `[ Write ]` > type `yes`
### 3. 
```bash
  
```
### 4. 
```bash
  
```
