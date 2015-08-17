# Maintainer: Serge Zirukin <ftrvxmtrx@gmail.com>

pkgname=ocaml-extunix
pkgver=0.0.5
pkgrel=2
pkgdesc="Thin bindings to various low-level system APIs which are not covered by Unix module"
arch=('i686' 'x86_64')
url=("http://extunix.forge.ocamlcore.org")
# LGPL + linking exception
license=('LGPL')
depends=('ocaml' 'ocaml-findlib')
makedepends=('ocaml' 'ocaml-ounit')
source=(http://forge.ocamlcore.org/frs/download.php/903/ocaml-extunix-${pkgver}.tar.gz
  http://forge.ocamlcore.org/frs/download.php/904/ocaml-extunix-${pkgver}.tar.gz.asc)
md5sums=('574b5adac283b2a4cb13c39684f6695b'
         'd36f327748536a8deda408ab539931d0')
options=(!makeflags !strip)

build () {
  cd "${srcdir}/${pkgname}-${pkgver}"

  ./configure --disable-debug --docdir "$pkgdir/usr/share/doc/$pkgname" || return 1
  make all doc || return 1
}

package () {
  destdir="${pkgdir}$(ocamlfind printconf destdir)"

  cd "${srcdir}/${pkgname}-${pkgver}"

  mkdir -p "${destdir}/stublibs"
  OCAMLFIND_DESTDIR="${destdir}" make install || return 1
}
