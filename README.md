# myArch 
This repository provides scripts for installing base Arch Linux system, Desktop Environment and some configurations for Xiaomi Notebook Pro. 

**Use at your own risk.**

**Scripts:**
* base_installer - basic Arch system installer
* desktop_installer - desktop environment and configuration installer
* xiaomi_ntb_pro_setup - some setup for Xiaomi Pro notebook

### base_install script

1. Boot with [Arch live ISO](https://www.archlinux.org/download/)
2. Install `git` and `clone` script repository
```bash
$ pacman -Sy git
$ git clone git://github.com/mrazekales/myarch-installer.git
```
3. Run `bas_install` stcript
```bash
$ cd myarch-installer
$ sh arch_install 
```

### desktop_install script

1. Boot Installed Arch and login as root
2. Clone script repository
```bash
$ git clone git://github.com/mrazekales/myarch-installer.git
```
3. Run Script
```bash
$ sh desktop_install
```

### xiaomi_ntb_pro_setup script
1. Boot Installed Arch and login as root
2. Clone script repository
```bash
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



**Desktop Environments/WindowManagers:**   Gnome, i3

**Display Managers:**  LightDM, ly

**File Managers**: pcmanFM, Thunar, Nautilus, Ranger(terminal)

**Web Browser**: chromium, chromw, firefox

**Terminals**: termite, xterm, tilix

**Text Editors**: gedit, vscode, vim

**GUI Package manager**: pamac, octopi

**Other apps:** htop, lxapperance, nitrogen


