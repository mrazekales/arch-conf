
# Programs Installation
Devel package is needed for install packages from `AUR` repository
```
$ sudo pacman -S base-devel
```
#### Programs
 * [Google Chrome](https://wiki.archlinux.org/index.php/Chromium) - default `google-chrome-stable` or lightweight `chromium`
 * [Mozzila ThunderBird](https://wiki.archlinux.org/index.php/thunderbird#Installation) - `thunderbird`
 *  - ``
 *  - ``
```
$ sudo pacman -S google-chrome-stable thunderbird 
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

```
```
