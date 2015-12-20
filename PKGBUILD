# $Id: PKGBUILD 92705 2013-06-12 16:03:23Z lcarlier $
# Maintainer: Thomas Bächler <thomas@archlinux.org>

_pkgbasename=attr
pkgname=lib32-$_pkgbasename
pkgver=2.4.47
pkgrel=1
pkgdesc="Extended attribute support library for ACL support (32-bit)"
arch=(x86_64)
url="http://savannah.nongnu.org/projects/attr"
license=('LGPL')
depends=('lib32-glibc' $_pkgbasename) 
makedepends=('gcc-multilib' 'gettext')
options=('!libtool')
source=(http://download.savannah.gnu.org/releases/attr/attr-${pkgver}.src.tar.gz)
sha256sums=('25772f653ac5b2e3ceeb89df50e4688891e21f723c460636548971652af0a859')

build() {
  cd ${srcdir}/attr-${pkgver} 

  export CC="gcc -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  export INSTALL_USER=root INSTALL_GROUP=root
  ./configure --prefix=/usr --libdir=/usr/lib32 --libexecdir=/usr/lib32
  make 
}

package() {
  cd ${srcdir}/attr-${pkgver} 

  make DIST_ROOT="${pkgdir}" install-lib install-dev

  # tidy up
  rm -f "$pkgdir"/usr/lib32/libattr.a
  chmod 0755 "$pkgdir"/usr/lib32/libattr.so.*.*.*

  rm -rf "${pkgdir}"/usr/{bin,include,share}
}
