# Maintainer: Maxime Gauduin <alucryd@gmail.com>

pkgname="mpdris2-git"
pkgver=0.4.r21.062fb37
pkgrel=1
pkgdesc="MPRIS2 support for MPD"
arch=('any')
url="https://github.com/eonpatapon/mpDris2"
license=('GPL3')
depends=('python2-dbus' 'python2-gobject2' 'python2-mpd' 'python2-notify')
makedepends=('git' 'intltool')
provides=("${pkgname%-*}")
conflicts=("${pkgname%-*}")
source=("${pkgname%-*}::git+https://github.com/eonpatapon/mpDris2.git")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}"/${pkgname%-*}

  printf "%s" "$(git describe --tags | sed 's/-/.r/; s/-g/./')"
}

prepare() {
  cd "${srcdir}"/${pkgname%-*}

  sed -i 's|^#!.*python$|#!/usr/bin/python2|' $(grep -rl '^#!.*python')
}

build() {
  cd "${srcdir}"/${pkgname%-*}

  ./autogen.sh --prefix=/usr --sysconfdir=/etc
  make
}

package() {
  cd "${srcdir}"/${pkgname%-*}

  make DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
