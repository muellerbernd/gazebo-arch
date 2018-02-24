# Contributor: Mykola Dolhyi <0xb000@gmail.com>
pkgname=ignition-math
pkgver=4.0.0
pkgrel=1
pkgdesc="Math classes and functions for robot applications"
arch=('i686' 'x86_64')
url="http://ignitionrobotics.org/"
license=('Apache')
groups=('development')
depends=('gcc-libs')
makedepends=('ignition-cmake')
optdepends=()
conflicts=()
source=("https://bitbucket.org/ignitionrobotics/ign-math/get/${pkgname}4_${pkgver}.tar.bz2")
sha256sums=('dd24b8d3540f726999f5d6ba9a13a077a5b172e840847491b8e529c53302288a')

_dir="ignitionrobotics-ign-math-054f8a99081f"

build() {
  cd "$srcdir/$_dir"

  mkdir -p build
  cd build

  # Configure build
  cmake .. -DCMAKE_BUILD_TYPE="Release" \
           -DCMAKE_INSTALL_PREFIX="/usr" \
           -DCMAKE_INSTALL_LIBDIR="lib" \
           -DBUILD_TESTING:BOOL=False

  # Compile
  make
}

check() {
  cd "$srcdir/$_dir/build"

  cmake .. -DCMAKE_BUILD_TYPE="Release" \
           -DCMAKE_INSTALL_PREFIX="/usr" \
           -DCMAKE_INSTALL_LIBDIR="lib" \
           -DBUILD_TESTING:BOOL=True

  make
  make test
}

package() {
  cd "$srcdir/$_dir/build"
  make DESTDIR="$pkgdir/" install
}
