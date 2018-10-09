# Maintainer: Edmunt Pienkowsky <roed@onet.eu>

pkgname='bluetooth-raspberrypi'
pkgver=6
pkgrel=2
pkgdesc='Bluetooth support for Raspberry Pi'
conflicts=('pi-bluetooth')
arch=('any')
license=('GPL')
url='http://wiki.archlinux.org/index.php/bluetooth'
depends=('firmware-raspberrypi>=4' 'linux-raspberrypi>=4.14.59')
makedepends=('dtc')
options=('!strip')
source=('bcmbt-overlay.dts')
md5sums=('3f77840571a6ff5974b5d954e9b3c265')

build(){
  cd "${srcdir}"

  dtc -I dts -O dtb bcmbt-overlay.dts -o bcmbt.dtbo
}

package(){
  install -d "${pkgdir}/usr/lib/firmware/updates/brcm"
  install -d "${pkgdir}/boot/overlays"

  install -m 0644 "${srcdir}/bcmbt.dtbo" "${pkgdir}/boot/overlays/bcmbt.dtbo"

  # workaround for Raspberry Pi 3B+
  ln -s BCM4345C0.hcd "${pkgdir}/usr/lib/firmware/updates/brcm/BCM.hcd"
}
