# Maintainer: aereaux <aidan@jmad.org>
_pkgname=meli
pkgname=${_pkgname}-git
pkgver=pre.alpha.0.3.2.r5.gcd761b3
pkgrel=2
pkgdesc="Experimental terminal mail client aiming for configurability and extensibility with sane defaults."
arch=("x86_64")
url="https://meli.delivery/"
license=('GPL3')
depends=()
makedepends=("git" "rust")
optdepends=()
provides=("$_pkgname")
conflicts=("$_pkgname")
source=("git+https://git.meli.delivery/meli/meli.git")
md5sums=("SKIP")

pkgver() {
  cd "$_pkgname"

  git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd "$_pkgname"

  make
}

# TODO: Right now the makefile does not have a check target
#check() {
#  cd "$_pkgname"
#
#  cargo test --release --locked
#}

package() {
  cd "$_pkgname"

  make PREFIX=/usr DESTDIR="$pkgdir/" install
}
