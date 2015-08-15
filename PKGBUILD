# Maintainer: NanoArch <nanoarch77@gmail.com>

pkgname=gdm3setup-native-theme
_pkgname=gdm3setup
pkgver=20121224
pkgrel=1
pkgdesc="A GUI to setting GDM3"
arch=(any)
license=('GPL')
url="http://github.com/Nano77/gdm3setup"
source=(https://raw.github.com/Nano77/various/master/src/$_pkgname-$pkgver.tar.xz
        'gdm3setup-native-theme.patch')
depends=('gdm>=3' 'gnome-shell-native-theme' 'python2-lxml' 'python2-dbus')
conflicts=('gdm3setup' 'gdm3setup-vala' 'gdm3setup-vala-native-theme')
provides=('gdm3setup')
sha256sums=('9a2ab75cfeb8a34ecc134f964647d4394f9ed01cfb22058853e1e12c3eb233d8'
            '516ba5cd7615f74bb2a0a3335cfda8898bc746e6f41baa3ad3a43deddeafb2f8')

build() {
  cd ${srcdir}/$_pkgname-$pkgver

  patch -Np1 -i ${srcdir}/gdm3setup-native-theme.patch

  cd ${srcdir}/$_pkgname-$pkgver/po
  ${srcdir}/$_pkgname-$pkgver/po/make-mo

}

package() {
  cd ${srcdir}/$_pkgname-$pkgver
  
  install --mode=755 -D gdm3setup.py ${pkgdir}/usr/bin/gdm3setup.py
  install --mode=755 -D gdm3setup-daemon.py ${pkgdir}/usr/bin/gdm3setup-daemon.py
  install --mode=755 -D start-gdm3setup-daemon ${pkgdir}/usr/bin/start-gdm3setup-daemon
  install --mode=755 -D gdmlogin.py ${pkgdir}/usr/bin/gdmlogin.py
  install --mode=755 -D get_gdm.sh ${pkgdir}/usr/bin/get_gdm.sh
  install --mode=755 -D set_gdm.sh ${pkgdir}/usr/bin/set_gdm.sh
  install -D gdm3setup.desktop ${pkgdir}/usr/share/applications/gdm3setup.desktop
  install -D apps.nano77.gdm3setup.service ${pkgdir}/usr/share/dbus-1/system-services/apps.nano77.gdm3setup.service
  install -D apps.nano77.gdm3setup.service ${pkgdir}/usr/share/dbus-1/services/apps.nano77.gdm3setup.service
  install -D apps.nano77.gdm3setup.conf ${pkgdir}/etc/dbus-1/system.d/apps.nano77.gdm3setup.conf
  install -D apps.nano77.gdm3setup.policy ${pkgdir}/usr/share/polkit-1/actions/apps.nano77.gdm3setup.policy
  install -D gdm3setup.ui ${pkgdir}/usr/share/gdm3setup/ui/gdm3setup.ui
  cp -r locale/ ${pkgdir}/usr/share/locale/
}
