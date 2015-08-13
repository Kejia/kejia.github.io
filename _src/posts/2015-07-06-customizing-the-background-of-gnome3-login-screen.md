    Title: customizing the background of gnome3 login screen
    Date: 2015-07-06T23:08:17
    Tags: debian, jessie, gnome, gdm

_gnome conf tools on debian jessie, such as dconf-editor, are not robust at present, and it's not straightforward to customize the background of gnome3 login screen. modifying the default background of gnome3 login screen on debian jessie can be done by editing file */usr/share/gnome-shell/theme/gnome-shell.css*._

<!-- more -->

open file _/usr/share/gnome-shell/theme/gnome-shell.css_ and edit the following block:

```css
#lockDialogGroup {
    background: #2e3436 url(gdm.png);
	background-repeat: no-repeat;
    background-size: cover;
    background-position: center center;
}
```
here, _gdm.png_ is the image for gnome3 login screen, and it should be placed in the directory _/usr/share/gnome-shell/theme_, i.e. the directory containing _gnome-shell.css_.
