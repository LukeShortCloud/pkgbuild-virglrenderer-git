# Maintainer: Luke Short <ekultails@gmail.com>
# Forked from: https://github.com/archlinux/svntogit-packages/blob/packages/virglrenderer/trunk/PKGBUILD

pkgname=virglrenderer-git
conflicts=(virglrenderer)
pkgver=0.9.0.r2.b96b9ae7
pkgrel=1
pkgdesc='A virtual 3D GPU library, that allows the guest operating system to use the host GPU to accelerate 3D rendering'
arch=(x86_64)
url='https://virgil3d.github.io/'
license=(MIT)
depends=(libepoxy mesa)
makedepends=(cmake gcc meson ninja pkg-config python)
_commit=67b196292831d5ad1d7e03c86e176c8007dae9b9
source=(https://gitlab.freedesktop.org/virgl/virglrenderer/-/archive/${_commit}/virglrenderer-${_commit}.tar.bz2)
sha256sums=('b96b9ae7f9535030a1f60df88bad0fe44b36e78520d234211d74c4f529324fba')

build() {
  cd virglrenderer-${_commit}
  meson --prefix=/usr -Dvenus-experimental=true build
  ninja -C build
}

package() {
  cd virglrenderer-${_commit}
  DESTDIR="$pkgdir" ninja -C build install
  install -D -m644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}
