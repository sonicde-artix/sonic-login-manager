# Maintainer: callmetango

pkgname=sonic-login-manager
pkgver=6.6.5.3
pkgrel=1
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
sha256sums=('e88db02268f5e4a0f2221f269f0e4491b18affbabd75c58d9a04390a35f701d4')

build() {
  cmake -B build -S $pkgname-$pkgver \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DDBUS_CONFIG_FILENAME=sonicde_org.freedesktop.DisplayManager.conf \
    -DSPLIT_BUILD=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
  rm -rf "$pkgdir"/etc
}
