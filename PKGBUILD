# Maintainer: Charles Bos <charlesbos1 AT gmail>

pkgname=libqtdbusmock-bzr
_bzrname=libqtdbusmock
pkgver=33
pkgrel=2
pkgdesc="Qt Bindings for python-dbusmock"
arch=('i686' 'x86_64')
url="https://launchpad.net/libqtdbusmock"
makedepends=('bzr')
depends=('qt5-base' 'valgrind' 'libqtdbustest-bzr' 'gmock' 'gtest')
provides=('libqtdbusmock')
license=('GPL')
source=("$_bzrname::bzr+http://bazaar.launchpad.net/~unity-team/$_bzrname/trunk/"
        'gmock.patch')
md5sums=('SKIP'
         '6e7fae6fbb5315481854b0b3c4a5111f')

pkgver() {
  cd $_bzrname
  bzr revno
}

prepare() {
  cd "$srcdir"/$_bzrname

  # This prevents the build from attempting to rebuild gmock
  patch -p1 -i "${srcdir}/gmock.patch"
}

build() {
  cd "$srcdir"/$_bzrname
  cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_INSTALL_LIBDIR=/usr/lib
  make
}

package() {
  cd "$srcdir"/$_bzrname
  make DESTDIR="$pkgdir" install
}
