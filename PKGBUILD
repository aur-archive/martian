# Contributor: Jonathan Liu <net147@hotmail.com>

pkgname=martian
pkgver=20080625
pkgrel=17
pkgdesc="Alternative driver for the Agere Systems PCI WinModem."
arch=('i686')
url="http://martian.barrelsoutofbond.org/"
license=("GPL" "custom:Agere Systems WinModem License")
depends=('kernel26>=2.6.39' 'kernel26<2.6.40' 'martian-utils')
makedepends=('kernel26-headers>=2.6.39' 'kernel26-headers<2.6.40')
replaces=('ltmodem')
options=(!strip)
install=martian.install 
source=(http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-${pkgver}.tar.gz
        kernel-2.6.39.patch)
_kernver=2.6.39-ARCH
options=(!strip)
         
build() { 
  cd $startdir/src/martian-full-$pkgver
  patch -Np0 -i ../kernel-2.6.39.patch
  make KERNEL_DIR=/usr/src/linux-${_kernver} all
}

package() { 
  install -D -m644 $startdir/src/martian-full-$pkgver/kmodule/martian_dev.ko $startdir/pkg/lib/modules/${_kernver}/kernel/drivers/net/martian_dev.ko
  install -D -m644 $startdir/src/martian-full-$pkgver/modem/ASWMLICENSE $startdir/pkg/usr/share/licenses/$pkgname/LICENSE
  # gzip -9 modules
  find "$pkgdir" -name '*.ko' -exec gzip -9 {} \;
}  
md5sums=('7ecbf7d294c620b5382eb54e28d8bbbb'
         '7c09e190b4c7f21c996d12804677a904')
