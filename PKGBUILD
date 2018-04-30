# Maintainer: Edmunt Pienkowsky <roed@onet.eu>

pkgname=bluetooth-raspberrypi
pkgver=2
pkgrel=2
pkgdesc='Bluetooth support for Raspberry Pi'
arch=('any')
license=('GPL')
url='http://wiki.archlinux.org/index.php/bluetooth'
depends=('firmware-raspberrypi>=4' 'bluez-utils')
conflicts=('pi-bluetooth')
options=('!strip')
source=('bluetooth-raspberrypi@.service'
        'bluetooth-raspberrypi.conf'
        '61-amba-tty-alias.rules')
md5sums=('690edc48aed27f518128d79a5e24a952'
         '7d32416a03fba468845cf8b22ef96a05'
         '9406dbec74def6d99605b5bbab2a6ed5')

package() {
  cd "${srcdir}"

  install -d "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -d "${pkgdir}/usr/lib/udev/rules.d"
  install -d "${pkgdir}/usr/lib/firmware/updates/brcm"

  install -m 0644 bluetooth-raspberrypi@.service "${pkgdir}/usr/lib/systemd/system"
  install -m 0644 bluetooth-raspberrypi.conf "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -m 0644 61-amba-tty-alias.rules "${pkgdir}/usr/lib/udev/rules.d"

  # workaround for Raspberry Pi 3B+
  ln -s BCM4345C0.hcd "${pkgdir}/usr/lib/firmware/updates/brcm/BCM.hcd"
}
