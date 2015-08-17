# Maintainer: Alex Forencich <alex@alexforencich.com>
pkgname=python2-myhdl-hg
pkgver=0.8.18.daf9bec8b50d
pkgrel=1
pkgdesc="a Python-Based Hardware Description Language"
arch=('any')
url="http://www.myhdl.org/"
license=('LGPL')
depends=('python2' 'iverilog')
makedepends=('mercurial')
provides=('python2-myhdl')

_hgroot='https://bitbucket.org/jandecaluwe/myhdl'
_hgname='myhdl'

source=("$_hgname::hg+$_hgroot")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_hgname"
  hg log -r . --template '{latesttag}-{latesttagdistance}-{node|short}\n' | sed -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/$_hgname"
}

package() {
  cd "$srcdir/$_hgname"
  python2 setup.py install --prefix=/usr --root="$pkgdir/" --optimize=1
  
  install -m 0644 -D ./LICENSE.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE.txt
  
  cd $srcdir/$_hgname/cosimulation/icarus
  make
  install -m 0755 -D ./myhdl.vpi $pkgdir/usr/lib/ivl/myhdl.vpi
}

