    Title: customizing grub2 background
    Date: 2015-07-06T22:50:18
    Tags: debian, jessie, grub2

_customizing the background of grub2 on debian jessie is not documented much, and i have done as follows._

<!-- more -->

0. finding out grub2 background resolution

	at grub2 booting menu, type `c` and enter grub2 shell:

	```bash
	$ vbeinfo
	```
	the working resolution is the line marked by asterisk.

0. making your background image

	the image used for the grub2 background must have the same resolution as mentioned above. export the image as _tga_ format.

0. specifying your image as the grub2 background

	editing file _/etc/default/grub_ and adding the following line:

	```text
	GRUB_BACKGROUND="/boot/grub/grub2.tga"
	```
	_/boot/grub/grub2.tga_ is your grub2 background image.

0. updating grub2 conf

	```bash
	$ update-grub2
	```

