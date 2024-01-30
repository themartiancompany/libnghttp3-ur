# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: kpcyrd <kpcyrd[at]archlinux[dot]org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

pkgname=libnghttp3
pkgver=1.1.0
pkgrel=1
pkgdesc="HTTP/3 library written in C"
url='https://github.com/ngtcp2/nghttp3'
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'armv7h'
)
license=('MIT')
provides=('libnghttp3.so')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/ngtcp2/nghttp3/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('b3ffb23a90442a0eafe8bfbefbc8b4ffb5179d68a7c0b8a416a34cf04b28d7c5')

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

# vim:set sw=2 sts=-1 et:
