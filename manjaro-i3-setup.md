# Audio setup
Install `Pulseaudio` by command in terminal
```
$ sudo install_pulse
```
If you want remove
```
$ rm_pulse
```



# Programs Installation
Devel package is needed for install packages from `AUR` repository
```
$ sudo pacman -S base-devel
```
#### Programs
 * [Google Chrome](https://wiki.archlinux.org/index.php/Chromium) - default `google-chrome-stable` or lightweight `chromium`
 * [Mozzila ThunderBird](https://wiki.archlinux.org/index.php/thunderbird#Installation) - `thunderbird`
 * [Spotify](https://wiki.archlinux.org/index.php/spotify)- `spotify-stable` If you wish to play local files you will need to install `zenity` and `ffmpeg-compat-54AUR`
 * [Atom](https://wiki.archlinux.org/index.php/atom) - `atom`
 * [Visual Studio Code](https://wiki.archlinux.org/index.php/Visual_Studio_Code) - `visual-studio-code-bin`
 * [InkScape](https://wiki.archlinux.org/index.php/Inkscape) - `inkscape`
 * []() - ``
 * []() - ``
 * []() - ``
```
$ sudo pacman -S google-chrome-stable thunderbird spotify-stable inkscape
```

# [Keyboard Layouts](http://docs.slackware.com/howtos:window_managers:keyboard_layout_in_i3)
### Changing the Keyboard Layout
If you need to switch between different layouts, you can map some keybindings to perform those functions.

Open the i3 config file
```
$ nano ~/.i3/config
```
Add the following
```
exec --no-startup-id "setxkbmap -model pc105 -layout us,cz -option grp:alt_shift_toggle"

or

exec --no-startup-id "setxkbmap -layout us,cz"
exec --no-startup-id "setxkbmap -option grp:alt_shift_toggle"
```
### Displaying the Active Layout in the Panel 
Display active layout with `xkblayout-state` and `i3blocks`
**xkblayout-state**
Installing `xkblayout-state` using `git`
```
$ git clone https://github.com/nonpop/xkblayout-state.git
$ cd xkblayout-state
$ make
```
Copy compiled `xkblayout-state` somwhere in `PATH` for example
```
$ sudo cp xkblayout-state /usr/local/bin/
```
**i3blocks**
```
$ sudo pacman -S i3blocks
```
Copy default conf file 
```
$ sudo cp /etc/i3blocks.conf ~/.i3blocks.conf
```
In `~/.config/i3/config` replace i3status with i3blocks
```
bar {
        status_command i3blocks
        tray_output primary                                               
}
# in case of layout change event - send signal to i3blocks
bindsym ISO_Next_Group exec pkill -RTMIN+1 i3blocks
```
Open `~/.i3blocks.conf` and add 
```
#Language indicator
[language]
#label=LNG
command=xkblayout-state print %s | awk '{print toupper($0)}'
interval=once
signal=1
```
Reboot

# [LightDM]() login manager

LightDM gui manager
```
lightdm-settings
```

#### NumLock ON by default
Install `numlockx`
```
$ sudo pacman -S numlockx 
```
Edit `/etc/lightdm/lightdm.conf` with
```
[Seat:*]
greeter-setup-script=/usr/bin/numlockx on
```
#### Hiding system and services users
To prevent system users from showing-up in the login, install the optional dependency `accountsservice`, or add the user names to `/etc/lightdm/users.conf` under `hidden-users`. The first option has the advantage of not needing to update the list when more users are added or removed.

#### [slick-greeter.conf](https://github.com/linuxmint/slick-greeter)
theme-name=              
themes shoud be in `/usr/share/themes/`
icon-theme-name         
themes shoud be in `/usr/share/icons/`

# [Fancy dualmonitors](https://github.com/meskarune/i3lock-fancy/tree/dualmonitors) Lock Screen - [i3lock](https://github.com/i3/i3lock)
Install dependencies 
```
$ sudo pacman -S i3lock-color-git imagemagick scrot bash awk utils-linux
```
i3 config file `~/.i3/config`

Lock screen when shortcut mod+9 is pressed
```
bindsym $mod+9 exec --no-startup-id script_name
```
Autolock
```
exec --no-startup-id xautolock -time 10 -locker script_name
```



