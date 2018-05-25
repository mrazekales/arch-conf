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

![](https://techfuzz.net/wp-content/uploads/2017/07/Manjaro-Linux-Bootable-Rufus.png)

# Boot up USB stick with Manjaro
#### 1. Check if BIOS (delete) is in UEFI mode and Secure boot is disabled
#### 2. Plug in USB stick and restart computer to boot options (F11)
#### 3. Select USB stick in boot options

# Installation
#### 1. 
#### 2. 
#### 3. 




### [Keyboard layouts](https://wiki.manjaro.org/index.php?title=Openbox:_Switch_languages_using_the_keyboard_and_xxkb)
Edit `/etc/X11/xorg.conf.d/00-keyboard.conf` file
```
 $ localectl --no-convert set-x11-keymap us,cz pc105 ,mrazekales grp:alt_shift_toggle
```
  This set `us` layout as default and `cz` as secondary, change with alt+shift
  For win+space type `win_space_toggle` insted of `alt_shift_toggle`


http://docs.slackware.com/howtos:window_managers:keyboard_layout_in_i3
