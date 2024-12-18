# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>

pkgname="xf86-video-pvrdri"
pkgver=14.d7aea15
pkgrel=1
pkgdesc="DDX for KMS devices accelerated by PowerVR GPUs (Mesa DRI drivers)"
arch=('riscv64')
url="https://github.com/Icenowy/xf86-video-pvrdri"
license=('MIT')
depends=('xorg-server' 'mesa' 'libdrm' 'libepoxy')
makedepends=('git' 'make' 'meson' 'xorg-server-devel')
source=("git+${url}")
b2sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  echo "$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}
 
build() {
  cd "$srcdir/$pkgname"
  rm -rf build
  arch-meson . build
  meson compile -C build
}

package() {
  cd "$srcdir/$pkgname"
  meson install -C build --destdir "$pkgdir"
  install -Dm644 ${srcdir}/${pkgname}/COPYING ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
}
