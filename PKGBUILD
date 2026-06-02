# Maintainer: callmetango

pkgname=sonic-login-manager
pkgver=6.6.5.4
pkgrel=2
arch=(x86_64)
pkgdesc='Sonic Login Manager'
url='https://github.com/Sonic-DE/sonic-login-manager'
license=(GPL-2.0-or-later)
depends=(
         glibc
         kcmutils
         kconfig
         kdbusaddons
         ki18n
         kpackage
         kservice
         libelogind
         libstdc++
         libxau
         pam
         qt6-5compat
         qt6-base
         qt6-declarative
         sh
         sonic-frameworks-auth
         sonic-frameworks-core-addons
         sonic-frameworks-io
         sonic-frameworks-quick-ui
         sonic-frameworks-windowsystem
         sonic-interface-libraries
         sonic-screen-library
         sonic-workspace
)
makedepends=(extra-cmake-modules
             qt6-tools)
groups=(sonicde)
source=("$pkgname-$pkgver.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('df96b2b4874fa3dc5166458da2277f3503940e2b4271a20970e1dfed375decce')

build() {
  cmake -B build -S $pkgname-$pkgver \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DDBUS_CONFIG_FILENAME=sonicde_org.freedesktop.DisplayManager.conf \
    -DSPLIT_BUILD=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
  rm -rf "$pkgdir"/etc/dinit.d
  rm -rf "$pkgdir"/etc/init.d
  rm -rf "$pkgdir"/etc/runit
  rm -rf "$pkgdir"/etc/s6
}
