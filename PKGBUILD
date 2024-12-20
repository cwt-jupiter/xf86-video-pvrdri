# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>

pkgname="xf86-video-pvrdri"
pkgver=14.d7aea15
pkgrel=2
pkgdesc="DDX for KMS devices accelerated by PowerVR GPUs (Mesa DRI drivers)"
arch=('riscv64')
url="https://github.com/Icenowy/xf86-video-pvrdri"
license=('MIT')
depends=('xorg-server' 'mesa' 'libdrm' 'libepoxy')
makedepends=('git' 'make' 'meson' 'xorg-server-devel')
source=("git+${url}"
        'spacemit.conf')
b2sums=('SKIP'
        'ee06cc3bf26f755b3e036a576e6e4e1ae21ea37ea5a6657b052da03fee3e5da564b94276e21b92be6519ad53c0855373398e752a2faa770bd57959e218df0527')

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
  install -Dm644 ${srcdir}/spacemit.conf ${pkgdir}/etc/X11/xorg.conf.d/spacemit.conf
  install -Dm644 ${srcdir}/${pkgname}/COPYING ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
}
