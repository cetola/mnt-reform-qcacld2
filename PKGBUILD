# Maintainer: Stephano Cetola <stephanoc@gmail.com>

pkgname=mnt-reform-qcacld2
pkgver=6.18.12
pkgrel=1
_kernver="${pkgver}-mnt-reform"
pkgdesc="MNT Reform qcacld2 WLAN kernel module + firmware (arm64)"
arch=('aarch64')
url="https://github.com/cetola/mnt-build"
license=('GPL2')
depends=("linux-mnt-reform=${pkgver}-${pkgrel}")
backup=('etc/modprobe.d/reform-qcacld2.conf')
source=(
  "wlan-${pkgver}-${pkgrel}-mnt.tar.gz::https://github.com/cetola/mnt-build/releases/download/${pkgver}-${pkgrel}-mnt-reform/wlan-${pkgver}-${pkgrel}-mnt.tar.gz"
)
sha256sums=('SKIP')

options=(!strip !docs !emptydirs)

package() {
  cd "$srcdir"

  install -Dm644 wlan.ko \
    "$pkgdir/usr/lib/modules/${_kernver}/extra/wlan.ko"

  install -dm755 "$pkgdir/usr/lib/firmware/qcacld2"
  install -Dm644 usr/lib/firmware/qcacld2/* \
    "$pkgdir/usr/lib/firmware/qcacld2/"
  # Also install to the directory where the driver looks
  # Not sure why this happens on Arch and not Debian
  install -dm755 "$pkgdir/usr/lib/firmware"
  install -Dm644 usr/lib/firmware/qcacld2/* \
    "$pkgdir/usr/lib/firmware/"

  install -dm755 "$pkgdir/usr/lib/firmware/wlan/qcacld2"
  install -Dm644 usr/lib/firmware/wlan/qcacld2/* \
    "$pkgdir/usr/lib/firmware/wlan/qcacld2/"
  # Also install to the directory where the driver looks
  # Not sure why this happens on Arch and not Debian
  install -Dm644 usr/lib/firmware/wlan/qcacld2/* \
    "$pkgdir/usr/lib/firmware/wlan/"

  install -Dm644 etc/modprobe.d/reform-qcacld2.conf \
    "$pkgdir/etc/modprobe.d/reform-qcacld2.conf"
}
