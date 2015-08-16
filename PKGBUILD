# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kded
pkgver=4.99.0
pkgrel=1
pkgdesc='KDE Daemon'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/frameworks/kded'
license=('LGPL')
depends=('kservice' 'kinit')
makedepends=('extra-cmake-modules' 'kdoctools')
groups=('kf5')
source=("http://download.kde.org/unstable/frameworks/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('6d10b0ff5a3173b3ebf2c1bd0f6b496e')

prepare() {
  mkdir -p build
}

build() {
  export XDG_DATA_DIRS="/opt/kf5/share:$XDG_DATA_DIRS"

  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
