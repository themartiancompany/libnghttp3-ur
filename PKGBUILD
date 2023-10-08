# Maintainer: kpcyrd <kpcyrd[at]archlinux[dot]org>

pkgname=libnghttp3
pkgver=0.15.0
pkgrel=1
pkgdesc="HTTP/3 library written in C"
url='https://github.com/ngtcp2/nghttp3'
arch=('x86_64')
license=('MIT')
provides=('libnghttp3.so')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/ngtcp2/nghttp3/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('6a75f5563e58d99e6b98d442111ac677984011c66b8b4f923764712741399027')

prepare() {
  cd nghttp3-${pkgver}
  autoreconf -i
}

build() {
  cd nghttp3-${pkgver}
  ./configure \
    --prefix=/usr
  make
}

check() {
  cd nghttp3-${pkgver}
  make check
}

package() {
  cd nghttp3-${pkgver}/lib
  make DESTDIR="${pkgdir}" install
  install -Dm644 ../COPYING -t "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim: ts=2 sw=2 et: