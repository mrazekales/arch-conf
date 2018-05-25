### Keyboard layouts
Edit `/etc/X11/xorg.conf.d/00-keyboard.conf` file
```
 $ localectl --no-convert set-x11-keymap us,cz pc105 ,mrazekales grp:alt_shift_toggle
```
  This set `us` layout as default and `cz` as secondary, change with alt+shift
  For win+space type `win_space_toggle` insted of `alt_shift_toggle`
