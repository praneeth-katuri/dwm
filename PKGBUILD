pkgname=dwm
pkgver=6.5
pkgrel=1
pkgdesc="My custom build of the Dynamic Window Manager for X"
arch=('x86_64')
url="https://github.com/praneeth-katuri/dwm"
license=('MIT')
OPTIONS=(zipman !debug)
depends=('libx11' 'libxft' 'libxinerama' 'imlib2' 'freetype2')
makedepends=('git' 'make')
source=("git+https://github.com/praneeth-katuri/dwm.git#branch=main")
sha256sums=('SKIP')

prepare() {
    cd "${srcdir}/${pkgname}"
    cp config.def.h config.h
}

build() {
    cd "${srcdir}/${pkgname}"
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
    cd "${srcdir}/${pkgname}"
    make PREFIX=/usr DESTDIR="$pkgdir" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
    install -Dm644 dwm.desktop "$pkgdir/usr/share/xsessions/dwm.desktop"
}
