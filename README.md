# myArch Setup
This repository provides scripts for installing base Arch Linux system, Desktop Environment and some configurations for Xiaomi Notebook Pro
### Install and config base Arch system

1. Boot with [Arch live ISO](https://www.archlinux.org/download/)
2. Clone script repository
```bash
$ pacman -Sy git
$ git clone git://github.com/mrazekales/myarch-installer.git
```
3. Run `arch_install` to install basic Arch linux system
```bash
$ cd myarch-installer
$ sh arch_install 
```

### Install and config Desktop Environment
1. Boot Installed Arch and login as root
2. Clone script repository
```bash
$ pacman -S git
$ git clone git://github.com/mrazekales/myarch-installer.git
```
3. Run Script
```bash
$ sh desktop_install
```

### Xiaomi Notebook Pro Setup
1. Boot Installed Arch and login as root
2. Clone script repository
```bash
$ pacman -S git
$ git clone git://github.com/mrazekales/myarch-installer.git
```
3. Run Script
```bash
$ sh xiaomi_ntb_pro_setup
```

## Reference
1. https://github.com/MatMoul/archfi
2. https://github.com/helmuthdu/aui
3. https://wiki.archlinux.org/index.php/installation_guide
5. https://wiki.archlinux.org/index.php/Xiaomi_Mi_Notebook_Air_13.3_(2018_Global_version)
6. https://www.notebookcheck.net/Xiaomi-Mi-Notebook-Pro-i5-Laptop-Review.262386.0.html



**Window Manager:**   i3

**Display Manager:**  LightDM

**File Manager:**     PcmanFM, Ranger

**Terminal:**         Termite, Xterm

**Text Editor:**      Gedit, vsCode

**Web Browser:**      Chromium

**Gui Package Manager:**  Pamac

**Other apps:** Htop, Lxapperance, Nitrogen


### Display Manager
- LightDM
- SLiM

### File Manager
- PcmanFM
- Thunar
- Nautilus
- Ranger(terminal)

### Terminal
- Termite
- Xterm
- Tilix

### Text Editor
- gedit
- vsCode

### Web Browser
- Chromium
- Chrome

### Package manager GUI
- Pamac
- Octopi

### Other
- Htop
- Lxapperance
- Nitrogen
