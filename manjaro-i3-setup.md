
# Programs Installation
Devel package is needed for install packages from `AUR` repository
```
$ sudo pacman -S base-devel
```
#### Programs
 * [Google Chrome](https://wiki.archlinux.org/index.php/Chromium) - default `google-chrome-stable` or lightweight `chromium`
 * [Mozzila ThunderBird](https://wiki.archlinux.org/index.php/thunderbird#Installation) - `thunderbird`
 * [Spotify](https://wiki.archlinux.org/index.php/spotify)- `spotify-stable` If you wish to play local files you will need to install `zenity` and `ffmpeg-compat-54AUR` as well.
 * []() - ``
```
$ sudo pacman -S google-chrome-stable thunderbird spotify-stable
```

# Keyboard Layouts
### Changing the Keyboard Layout
If you need to switch between different layouts, you can map some keybindings to perform those functions.

Open the i3 config file
```
$ nano ~/.i3/config
```
Add the following
```
setxkbmap -layout de,gb
setxkbmap -option 'grp:ctrl_alt_toggle'
```
### Displaying the Active Layout in the Panel
Unfortunately, the current keyboard layout is not build in i3. 
For that reason, you need to write a short script to display the layout in the panel. 

Create somewhere new script
```
$ nano my_script.sh
```
The contents of my_script.sh
```bash
#!/bin/bash

# shell scipt to prepend i3status with more stuff

i3status --config ~/.i3status.conf | while :
do
        read line
        LG=$(setxkbmap -query | awk '/layout/{print $2}') 
        echo "LG: $LG | $line" || exit 1
done
```
Add `status_commandto` bar property
```bash
bar {
    status_command /path/to/your/i3script.sh
}
```


To start customising `i3status`, copy `/etc/i3status.conf` to `~/.i3status.conf` where you can place your changes. 
```
$ sudo cp /etc/i3status.conf ~/.i3status.conf
```
