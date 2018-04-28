#
# bluetooth-raspberrypi
#

pkgname=bluetooth-raspberrypi
pkgver=1
pkgrel=1
pkgdesc="Bluetooth support for Raspberry Pi"
arch=('any')
license=('GPL')
depends=('firmware-raspberrypi' 'bluez-utils')
options=('!strip')
source=('bluetooth-raspberrypi.service'
        'bluetooth-raspberrypi.conf'
        '61-amba-tty-alias.rules')
md5sums=('26b66448b7e7a7987f55edf5333fb340'
         '80ee98fd2dfec67abeeb8e602f226a15'
         '9406dbec74def6d99605b5bbab2a6ed5')

package() {
  cd "${srcdir}"

  install -d "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -d "${pkgdir}/usr/lib/udev/rules.d"

  install -m 0644 bluetooth-raspberrypi.service "${pkgdir}/usr/lib/systemd/system"
  install -m 0644 bluetooth-raspberrypi.conf "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -m 0644 61-amba-tty-alias.rules "${pkgdir}/usr/lib/udev/rules.d"
}
