# myArch Installer
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
