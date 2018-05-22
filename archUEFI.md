Arch Linux installation UEFI

# Pre-installation 
### Verify the boot mode
If UEFI mode is enabled on an UEFI motherboard, Archiso will boot Arch Linux accordingly via systemd-boot. 
To verify this, list the efivars directory:
```
  # ls /sys/firmware/efi/efivars
```
### Update the system clock
```
  # timedatectl set-ntp true
```
See `timedatectl status`
```
  # timedatectl status
```
### Try ping to internet
```
  # ping archlinux.org
```
# Partition the disks 
### Create partitions
Create EFI partition
```
  # fdisk /dev/sda
--------------------------------------
 * g (to create an empty GPT partition table)
 * n
 * 1
 * enter
 * +300M
 * t
 * 1 (For EFI)
 * w
```
Create root/home partition
```
  # fdisk /dev/sda
--------------------------------------
 * n
 * 2
 * enter
 * enter
 * w
```
### Format the partitions
Format efi partition as fat32 and root/home partition as ext4
```
  # # mkfs.fat -F32 /dev/sda1
  # mkfs.ext4 /dev/sda2 
```
### Mount the file systems
```
  # mount /dev/sda2 /mnt
```
# Installation 
### Setting up Arch repository mirrorlist
Make backup
```
  # cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.backup
```
Sort backup
```
  # sed -i 's/^#Server/Server/' /etc/pacman.d/mirrorlist.backup
  # rankmirrors -n 6 /etc/pacman.d/mirrorlist.backup > /etc/pacman.d/mirrorlist
```
### Installing the Arch base files
This command will install base Arch linux system
```
  # pacstrap -i /mnt base 
```
Other options are `base-devel` for developer packages

# System configuration
### Fstab
Generate `fstab` file
```
  # genfstab -U /mnt >> /mnt/etc/fstab
```
Check it
```
  # nano /mnt/etc/fstab
```
### Chroot
Change root into the new system
```
  # arch-chroot /mnt
```


### Time-zone
Set the time zone
```
  # ln -sf /usr/share/zoneinfo/Europe/Prague /etc/localtime 
```
Run `hwclock` to generate `/etc/adjtime`
```
  # hwclock --systohc
```
### Locale
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
### Hostname
Set computer hostname
```
  # echo myhostname > /etc/hostname
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
### Root password
Create roo password
```
  # passwd
```
# Intel processors
Install `intel-ucode`
```
  # pacman -S intel-ucode
```
Edit the main grub configuration file, if grub installe
```
  # grub-mkconfig -o /boot/grub/grub.cfg
```
# EFI Grub bootloader
#### EFI
Create dir
```
  # mkdir /boot/EFI
```
Mount EFI partition to that directory
```
  # mount /dev/sda1 /boot/EFI
```
### Grub
Install the `grub` package to replace `grub-legacy`
```
  # pacman -S grub
```
Install grub bootloader to disk
```
  # grub-install --target=x86_64-efi --bootloader-id=grub_uefi --recheck
```
```
  # cp /usr/share/locale/en\@quot/LC_MESSAGES/grub.mo /boot/grub/locale/en.mo
```
Generate the main configuration file
```
  # grub-mkconfig -o /boot/grub/grub.cfg
```

# Swap File
### Create Swap File
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
### Remove Swap File
To remove a swap file, it must be turned off first and then can be removed
```
  # swapoff -a
  # rm -f /swapfile
```
Finally remove the relevant entry from `/etc/fstab`

# Users
### Add new user
Add a home user
```
  # useradd -m -g users -G wheel,audio,video,storage,power -s /bin/bash newusername
```
Set a pass for that user:
```
  # passwd newusername
```
### Setting up sudoers
Install `sudo` package
```
  # pacman -S sudo
```
sudoers
```
  # EDITOR=nano visudo
```
Uncomment  `%wheel ALL=(ALL) ALL`
Add `Defaults rootpw`
# Network Set up
Show connections
```
  # ip addr show
```
Use `dhcpcd` client
```
  # dhcpcp enp4s0
```
