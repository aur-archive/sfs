# $Id: PKGBUILD 9951 2008-08-21 02:40:36Z eric $
# Maintainer: Jason Chu <jason@archlinux.org>
# Contributor: Jason Chu <jason@archlinux.org>
# You need an sfs user and group to build this package
pkgname=sfs
pkgver=0.7.2
pkgrel=1
pkgdesc="The Secure FileSystem: a secure replacement for nfs"
arch=('i686')
url="http://www.fs.net"
license=()
depends=(gcc gmp nfs-utils)
makedepends=()
conflicts=()
replaces=()
backup=()
install=sfs.install
source=(http://www.fs.net/sfswww/dist/$pkgname-$pkgver.tar.gz sfs.patch sfscd sfssd)
md5sums=('1fb559f144c4d367ef01e93beb1dea1e' 'a59092316309468c0f25d69deee0b757'\
         '94a1e5dbb3f5b923731583c495012bac' '1249b5325c8494c0f6d5413b67ea4082')

build() {
  cd $startdir/src/$pkgname-$pkgver
  patch -N -p1 < ../sfs.patch
  ./configure --prefix=/usr
  make || return 1
  make DESTDIR=$startdir/pkg install

  chmod g-s $startdir/pkg/usr/lib/sfs-0.7.2/suidconnect
  chgrp root $startdir/pkg/usr/lib/sfs-0.7.2/suidconnect

  mkdir -p $startdir/pkg/etc/rc.d
  cp $startdir/src/sfscd $startdir/pkg/etc/rc.d
  cp $startdir/src/sfssd $startdir/pkg/etc/rc.d
}
