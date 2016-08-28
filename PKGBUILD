# Maintainer Justin Gross <jgross dot biz at gmail dot com>
# Upstream URL: svn://dev.exiv2.org/svn/trunk

pkgname=exiv2-svn
pkgver=0.26.0
pkgrel=1
pkgdesc="A command line utility to manage image metadata."
arch=("x86_64")
url="http://dev.exiv2.org/projects/exiv2/repository"
license=("GPL")
options=('!makeflags')
depends=('expat' 'gcc-libs' 'zlib')
makedepends=('expat' 'gcc-libs' 'zlib' 'gettext' 'subversion' 'make')
replaces=('exiv2')


build() {
  mkdir -p $startdir/src/$pkgname
  cd $startdir/src/$pkgname
  svn checkout svn://dev.exiv2.org/svn/trunk
  cd trunk
  make config
  ./configure --prefix=/usr \
    --enable-mime \
    --enable-extras \
    --enable-dst-correction
  make
}

package() {
  cd ${pkgname}/trunk
  make DESTDIR="$pkgdir" install
}
