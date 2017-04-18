# Maintainer: Mario Finelli <mario at finel dot li>
# Contributor: Arthur Titeica <arthur dot titeica at gmail dot com>

pkgname=ttfautohint
pkgver=1.6
pkgrel=2
pkgdesc="Provides automated hinting process for web fonts."
arch=('i686' 'x86_64')
url="http://www.freetype.org/ttfautohint/"
license=('GPL' 'custom')
depends=('freetype2' 'qt5-base')
optdepends=('texlive-bin: generate docs'
            'pandoc: generate docs'
            'ghc: pandoc filter')
source=(https://download.savannah.gnu.org/releases/freetype/$pkgname-$pkgver.tar.gz{,.sig})
sha256sums=('e41013f710c306538ff5b2f1b4d9a5b24bda031fb73fabcaf02a21b8edd71be5'
            'SKIP')
validpgpkeys=('58E0C111E39F5408C5D3EC76C1A60EACE707FDA5')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  export QMAKE='/usr/bin/qmake'
  export MOC='/usr/bin/moc'
  export UIC='/usr/bin/uic'
  export RCC='/usr/bin/rcc'
  ./configure --prefix=/usr --with-qt=/usr/lib/qt
  make
}

check() {
  cd "$srcdir/$pkgname-$pkgver"
  make -k check
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir/" install

  install -Dm644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/COPYING"
  install -Dm644 FTL.TXT "${pkgdir}/usr/share/licenses/${pkgname}/FTL.TXT"
}
