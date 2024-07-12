# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>
pkgname="th1520-vpu"
pkgver=r3.c700124
pkgrel=1
pkgdesc="TH1520 VPU for Arch Linux"
arch=('riscv64')
url="https://github.com/revyos/th1520-vpu"
license=('proprietary')
depends=('libomxil-bellagio')
makedepends=('git')
options=('!strip')
source=("git+https://github.com/revyos/th1520-vpu.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  cd "$srcdir/$pkgname/addons/lib"
  install -Dm644 modules-load.d/hantro.conf \
    "${pkgdir}/usr/lib/modules-load.d/hantro.conf"
  install -Dm644 udev/rules.d/70-hantro.rules \
    "${pkgdir}/usr/lib/udev/rules.d/70-hantro.rules"

  cd "$srcdir/$pkgname/addons/usr/lib/riscv64-linux-gnu/libomxil-bellagio0"
  install -Dm755 libOMX.hantro.H2.image.encoder.so \
    "${pkgdir}/usr/lib/bellagio/libOMX.hantro.H2.image.encoder.so"
  install -Dm755 libOMX.hantro.H2.video.encoder.so \
    "${pkgdir}/usr/lib/bellagio/libOMX.hantro.H2.video.encoder.so"
  install -Dm755 libOMX.hantro.VC8000D.image.decoder.so \
    "${pkgdir}/usr/lib/bellagio/libOMX.hantro.VC8000D.image.decoder.so"
  install -Dm755 libOMX.hantro.VC8000D.video.decoder.so \
    "${pkgdir}/usr/lib/bellagio/libOMX.hantro.VC8000D.video.decoder.so"
}
