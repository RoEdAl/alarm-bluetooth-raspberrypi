# Maintainer: Edmunt Pienkowsky <roed@onet.eu>

pkgbase='bluetooth-raspberrypi'
pkgname=('bluetooth-raspberrypi' 'bluetooth-raspberrypi-miniuart')
pkgver=5
pkgrel=1
arch=('any')
license=('GPL')
url='http://wiki.archlinux.org/index.php/bluetooth'
depends=('firmware-raspberrypi>=4' 'bluez-utils')
options=('!strip')
backup=('etc/conf.d/bluetooth-raspberrypi')
source=('bluetooth-raspberrypi@.service'
        'bluetooth-raspberrypi.conf'
	'bluetooth-raspberrypi-miniuart.conf'
        '61-amba-tty-alias.rules'
        '61-platform-tty-alias.rules'
	'env'
	'env-miniuart')
md5sums=('52764fc4ddb47c7aca30cc8fb29cb61a'
         '7d32416a03fba468845cf8b22ef96a05'
         '711cbd24cbd6f964b2e8778d3aa68ee0'
         '11aa84ae1f76d6c282dcf62c67f4fc02'
         '501fb2ae52b234eb96da142623e8f55b'
         '466306599085a24449ee65da8cb0d145'
         '07c1e97c37ea74980f3c7aba6d22fd60')

_package_common() {
  install -d "${pkgdir}/etc/conf.d"
  install -d "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -d "${pkgdir}/usr/lib/udev/rules.d"
  install -d "${pkgdir}/usr/lib/firmware/updates/brcm"

  install -m 0644 bluetooth-raspberrypi@.service "${pkgdir}/usr/lib/systemd/system"

  # workaround for Raspberry Pi 3B+
  ln -s BCM4345C0.hcd "${pkgdir}/usr/lib/firmware/updates/brcm/BCM.hcd"
}

package_bluetooth-raspberrypi() {
  pkgdesc='Bluetooth support for Raspberry Pi'
  conflicts=('pi-bluetooth')

  cd "${srcdir}"
  _package_common

  install -m 0644 bluetooth-raspberrypi.conf "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d"
  install -m 0644 61-amba-tty-alias.rules "${pkgdir}/usr/lib/udev/rules.d"
  install -m 0644 env "${pkgdir}/etc/conf.d/bluetooth-raspberrypi"
}

package_bluetooth-raspberrypi-miniuart() {
  pkgdesc='Bluetooth support for Raspberry Pi (mini-UART)'
  conflicts=('pi-bluetooth' 'bluetooth-raspberrypi')
  provides=('bluetooth-raspberrypi')
  install='bluetooth-raspberrypi-miniuart.install'

  cd "${srcdir}"
  _package_common

  install -m 0644 bluetooth-raspberrypi-miniuart.conf "${pkgdir}/usr/lib/systemd/system/bluetooth.service.d/bluetooth-raspberrypi.conf"
  install -m 0644 61-platform-tty-alias.rules "${pkgdir}/usr/lib/udev/rules.d"
  install -m 0644 env-miniuart "${pkgdir}/etc/conf.d/bluetooth-raspberrypi"
}
