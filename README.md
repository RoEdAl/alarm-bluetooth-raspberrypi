# bluetooth-raspberrypi

Arch Linux ARM package enabling integrated Bluetooth on Raspberry Pi 3B/3B+/Zero W.
This is modification of [`pi-bluetooth`](//aur.archlinux.org/packages/pi-bluetooth/) (AUR) package.
The main changes are:

* Use `btattach` instead of deprecated `hciattach` tool.
  `bluetooth-raspberrypi` depends only on standard `firmware-raspberrypi` and `bluez-utils` packages.
* Do not install firmware. Firmware is already included in `firmware-raspberrypi` package.
* Do not auto power-on using `hciattach` and udev rule.
  This method is deprecated - see [here](//wiki.archlinux.org/index.php/bluetooth#Auto_power-on_after_boot) for more information.
  
This package doesn't work with [`pi3-miniuart-bt`](//github.com/raspberrypi/firmware/blob/master/boot/overlays/README) device tree overlay.

## Instalation

* [Build](//wiki.archlinux.org/index.php/Makepkg#Usage) and install this package.
* Remove the attachment of `/dev/ttyAMA0` to the console from `/boot/cmdline.txt`.
* (Re)enable [`bluetooth`](//wiki.archlinux.org/index.php/bluetooth) service and **reboot**.

## Kernel messages

### Raspberry Pi 3 Model B Plus

````
[    0.000000] OF: fdt: Machine model: Raspberry Pi 3 Model B Plus Rev 1.3
...
[    7.751931] Bluetooth: hci1: BCM: chip id 107
[    7.754438] Bluetooth: hci1: BCM: features 0x2f
[    7.777740] Bluetooth: hci1: BCM4345C0
[    7.778212] Bluetooth: hci1: BCM (003.001.025) build 0000
[   13.320384] Bluetooth: hci1: BCM (003.001.025) build 0139
````

For *Raspberry Pi 3 Model B Plus* `btattach` tries to load firmware  from `BCM.hcd` instead of `BCM4345C0.hcd`.
As a workaround this package just creates `BCM.hcd` as symlink to `BCM4345C0.hcd`.

### Raspberry Pi 3 Model B

````
[    0.000000] OF: fdt: Machine model: Raspberry Pi 3 Model B Rev 1.2
...
[    7.892120] Bluetooth: hci0: BCM: chip id 94
[    7.895277] Bluetooth: hci0: BCM: features 0x2e
[    7.919215] Bluetooth: hci0: BCM43430A1
[    7.920183] Bluetooth: hci0: BCM43430A1 (001.002.009) build 0000
[   11.690212] Bluetooth: hci0: BCM (001.002.009) build 0360
````

### Raspberry Pi Zero W

````
[    0.000000] OF: fdt: Machine model: Raspberry Pi Zero W Rev 1.1
...
[   12.874297] Bluetooth: hci0: BCM: chip id 94
[   12.877951] Bluetooth: hci0: BCM: features 0x2e
[   12.902263] Bluetooth: hci0: BCM43430A1
[   12.903425] Bluetooth: hci0: BCM43430A1 (001.002.009) build 0000
[   16.772188] Bluetooth: hci0: BCM (001.002.009) build 0360
````
