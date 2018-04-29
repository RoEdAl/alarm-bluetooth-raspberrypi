# bluetooth-raspberrypi

Arch Linux ARM package enabling integrated Bluetooth on Raspberry Pi 3B/3B+/Zero W.
This is modification of [`pi-bluetooth`](//aur.archlinux.org/packages/pi-bluetooth/) (AUR) package.
The major changes are:

* Use `btattach` instead of deprecated `hciattach` tool.
  `bluetooth-raspberrypi` depends only on standard `firmware-raspberrypi` and `bluez-utils` packages.
* Do not install firmware. Firmware is already included in `firmware-raspberrypi` package.
* Do not auto power-on using `hciattach` and udev rule.
  This method is deprecated - see [here](//wiki.archlinux.org/index.php/bluetooth#Auto_power-on_after_boot) for more information.

## Instalation

* [Build](//wiki.archlinux.org/index.php/Makepkg#Usage) and install this package.
* (Re)enable `bluetooth` service and reboot.

## Kernel messages

Command: `dmesg|grep Bluetooth`

### Raspberry Pi 3 Model B Plus:

````
[    0.000000] OF: fdt: Machine model: Raspberry Pi 3 Model B Plus Rev 1.3
...
[    7.361227] Bluetooth: Core ver 2.22
[    7.362633] Bluetooth: HCI device and connection manager initialized
[    7.363311] Bluetooth: HCI socket layer initialized
[    7.363948] Bluetooth: L2CAP socket layer initialized
[    7.364623] Bluetooth: SCO socket layer initialized
[    7.366781] Bluetooth: Generic Bluetooth SDIO driver ver 0.1
[    7.611635] Bluetooth: HCI UART driver ver 2.3
[    7.612248] Bluetooth: HCI UART protocol H4 registered
[    7.612831] Bluetooth: HCI UART protocol BCSP registered
[    7.613454] Bluetooth: HCI UART protocol LL registered
[    7.614076] Bluetooth: HCI UART protocol ATH3K registered
[    7.614645] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    7.615327] Bluetooth: HCI UART protocol Broadcom registered
[    7.751931] Bluetooth: hci1: BCM: chip id 107
[    7.754438] Bluetooth: hci1: BCM: features 0x2f
[    7.777740] Bluetooth: hci1: BCM4345C0
[    7.778212] Bluetooth: hci1: BCM (003.001.025) build 0000
[    8.252185] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.252253] Bluetooth: BNEP filters: protocol multicast
[    8.252304] Bluetooth: BNEP socket layer initialized
[   13.320384] Bluetooth: hci1: BCM (003.001.025) build 0139
[   13.466702] Bluetooth: RFCOMM TTY layer initialized
[   13.466832] Bluetooth: RFCOMM socket layer initialized
[   13.466937] Bluetooth: RFCOMM ver 1.11
````

### Raspberry Pi 3 Model B

````
[    0.000000] OF: fdt: Machine model: Raspberry Pi 3 Model B Rev 1.2
...
[    7.725604] Bluetooth: Core ver 2.22
[    7.727389] Bluetooth: HCI device and connection manager initialized
[    7.728343] Bluetooth: HCI socket layer initialized
[    7.729234] Bluetooth: L2CAP socket layer initialized
[    7.730161] Bluetooth: SCO socket layer initialized
[    7.757272] Bluetooth: HCI UART driver ver 2.3
[    7.758083] Bluetooth: HCI UART protocol H4 registered
[    7.758782] Bluetooth: HCI UART protocol BCSP registered
[    7.759764] Bluetooth: HCI UART protocol LL registered
[    7.760645] Bluetooth: HCI UART protocol ATH3K registered
[    7.761365] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    7.762281] Bluetooth: HCI UART protocol Broadcom registered
[    7.892120] Bluetooth: hci0: BCM: chip id 94
[    7.895277] Bluetooth: hci0: BCM: features 0x2e
[    7.919215] Bluetooth: hci0: BCM43430A1
[    7.920183] Bluetooth: hci0: BCM43430A1 (001.002.009) build 0000
[    8.284666] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.284737] Bluetooth: BNEP filters: protocol multicast
[    8.284791] Bluetooth: BNEP socket layer initialized
[   11.690212] Bluetooth: hci0: BCM (001.002.009) build 0360
[   11.821038] Bluetooth: RFCOMM TTY layer initialized
[   11.821174] Bluetooth: RFCOMM socket layer initialized
[   11.821284] Bluetooth: RFCOMM ver 1.11
````
