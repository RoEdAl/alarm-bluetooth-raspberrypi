# bluetooth-raspberrypi

Arch Linux ARM package enabling integrated Bluetooth on Raspberry Pi 3B/3B+/Zero W.

The idea of this solution is taken from [shenghaoyang/blueEnable_ALARM_non_mainline.md](https://gist.github.com/shenghaoyang/92e6dd65b9f0cc736a419f3e640663c2).
Many thanks to Shenghao Yang.

## Instalation

* [Build](//wiki.archlinux.org/index.php/Makepkg#Usage) and install `bluetooth-raspberrypi` package.
  You can also use [pre-built packages](//github.com/RoEdAl/alarm-bluetooth-raspberrypi/releases):
  ````
  pacman -U https://github.com/RoEdAl/alarm-bluetooth-raspberrypi/releases/download/vx-y/bluetooth-raspberrypi-x-y-any.pkg.tar.xz
  ````
* Remove the attachment of `/dev/ttyAMA0` (`/dev/ttyS0` in mini-UART version) to the console from `/boot/cmdline.txt`.
* Edit `/boot/config.txt` file and add `bcmbt` overlay:
  ````
  dtoverlay=bcmbt
  ````

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

For *Raspberry Pi 3 Model B Plus* kernel tries to load firmware  from `BCM.hcd` instead of `BCM4345C0.hcd`.
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
