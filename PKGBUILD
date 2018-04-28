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
md5sums=('8e965b8e57cb70f7ef8a82b431380b94'
         '80ee98fd2dfec67abeeb8e602f226a15'
         '9406dbec74def6d99605b5bbab2a6ed5')

package() {
  cd "${srcdir}"

  install -d "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -d "${pkgdir}/usr/lib/udev/rules.d"
  install -d "${pkgdir}/usr/lib/firmware/updates/brcm"

  install -m 0644 bluetooth-raspberrypi.service "${pkgdir}/usr/lib/systemd/system"
  install -m 0644 bluetooth-raspberrypi.conf "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -m 0644 61-amba-tty-alias.rules "${pkgdir}/usr/lib/udev/rules.d"

  # workaround for Raspberry Pi 3B+
  ln -s BCM4345C0.hcd "${pkgdir}/usr/lib/firmware/updates/brcm/BCM.hcd"
}
