# Maintainer: Luke Short <ekultails@gmail.com>
# Forked from: https://github.com/archlinux/svntogit-packages/blob/packages/virglrenderer/trunk/PKGBUILD

pkgname=virglrenderer-git
conflicts=(virglrenderer)
pkgver=0.9.0.r1.a47c9901
pkgrel=1
pkgdesc='A virtual 3D GPU library, that allows the guest operating system to use the host GPU to accelerate 3D rendering'
arch=(x86_64)
url='https://virgil3d.github.io/'
license=(MIT)
depends=(libepoxy mesa)
makedepends=(cmake gcc meson ninja pkg-config python)
_commit=2cd0803574117cfbf71feb4f6d28f712d8184a8e
source=(https://gitlab.freedesktop.org/virgl/virglrenderer/-/archive/${_commit}/virglrenderer-${_commit}.tar.bz2)
sha256sums=('a47c9901b644c30e85ced1dc13850dca9b2cef9ba5e88b3f73bb491b8303502f')

build() {
  cd virglrenderer-${_commit}
  meson --prefix=/usr build # -Dtests=true
  ninja -C build
}

package() {
  cd virglrenderer-${_commit}
  DESTDIR="$pkgdir" ninja -C build install
  install -D -m644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}
