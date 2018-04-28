# bluetooth-raspberrypi

Arch Linux ARM package enabling integrated Bluetooth on Raspberry Pi 3B/3B+/Zero W.
This is modification of [`pi-bluetooth`](//aur.archlinux.org/packages/pi-bluetooth/) (AUR) package.

The main differences between `bluetooth-raspberrypi` and `pi-bluetooth` packages are:

* Use `btattach` instead of deprecated `hciattach` tool.
  `bluetooth-raspberrypi` depends only on standard `firmware-raspberrypi` and `bluez-utils` packages.
* Do not install firmware. Firmware is already included in `firmware-raspberrypi` package.
* Do not auto power-on using `hciattach` and udev rule.
  This method is deprecated - see [here](//wiki.archlinux.org/index.php/bluetooth#Auto_power-on_after_boot) for more information.
  
After building and/or installing this package 
just (re)enable *bluetooth* service by `systemctl enable bluetooth` command and reboot.
