# Packages installation
### [vim](https://wiki.archlinux.org/index.php/vim)
Text editor
```
  # pacman -S gvim
```
### [screenfetch](https://github.com/KittyKatt/screenFetch)
Bash Screenshot Information Tool
```
  # pacman -S screenfetch
```
### [chrome/chromium](https://wiki.archlinux.org/index.php/chromium)
Web browser
Install `chrome` or lightweight `chromium`
```
  # pacman -S google-chrome
  # pacman -S chromium
```
# [i3](https://wiki.archlinux.org/index.php/i3) Configuration
i3 window manager
### Installation
`i3` package installation and `xinit` for then manualy start i3
```
  # pacman -S i3 xorg-xinit
```
### [Start i3](https://wiki.archlinux.org/index.php/Xinit#Autostart_X_at_login~)
Start `i3` using `xinit`
If `.xinitrc` is present in a user's home directory, startx and xinit execute it
Copy one to home direstory
```
  # cp /etc/X11/xinit/xinitrc ~/.xinitrc
```
Edit it to execute `i3`
```
 # nano ~/.xinitrc
---------------------------------

exec i3
```
Autostart at login
If the file does not exist, copy a skeleton version from `/etc/skel/.bash_profile`
```
  # nano ~/.bash_profile
--------------------------------------
if [[ ! $DISPLAY && $XDG_VTNR -eq 1 ]]; then
  exec startx
fi
```
# [LightDM](https://wiki.archlinux.org/index.php/LightDM#Installation) Configuration
Display/login manager
### Installation
`i3` package installation and `xinit` for then manualy start i3
```
  # pacman -S lightdm
```
Dependencies
```
   # pacman -S xorg-server lightdm-gtk-greeter
```
### Configuration
You can set the default greeter by changing the `[Seat:*]` section of the LightDM configuration file
```
  # /etc/lightdm/lightdm.conf
---------------------------------------------------------
[Seat:*]
...
greeter-session=lightdm-yourgreeter-greeter
...
```
Enable `lightdm.service` so LightDM will be started at boot
```
  # sudo systemctl enable lightdm.service
```
Greeter config file `/etc/lightdm/lightdm-gtk-greeter.conf`
```
  # nano /etc/lightdm/lightdm-gtk-greeter.conf
```
LightDM config file `/etc/lightdm/lightdm-gtk-greeter.conf`
```
  # nano /etc/lightdm/lightdm.conf
```
