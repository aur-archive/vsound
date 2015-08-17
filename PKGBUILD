# Maintainer: None (dropped from [community])
# Contributor: Jeff Mickey <j@codemac.net>
# Contributor: Giovanni Scafora <giovanni@archlinux.org>
# Contributor: Braulio Barros de Oliveira <brauliobo@gmail.com>
# Contributor: Gerardo Exequiel Pozzi <vmlinuz386@yahoo.com.ar>

pkgname=vsound
pkgver=0.6
pkgrel=4
pkgdesc="A virtual audio loopback cable"
url="http://www.vsound.org"
license=('LGPL')
arch=('i686' 'x86_64')
depends=('sox')
options=('!libtool')
source=(http://www.vsound.org/${pkgname}-${pkgver}.tar.gz)
md5sums=('0460c93ecab58d7864dd6d245a2dea18')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  sed 's#86 )#86 | x86_64 )#g' -i acendian.m4
  echo "ACLOCAL_AMFLAGS = -I ." >> Makefile.am
  autoreconf -f -i
  ./configure --prefix=/usr \
              --disable-static \
              --enable-shared
  make || return 1
  make DESTDIR=${pkgdir} install
}
