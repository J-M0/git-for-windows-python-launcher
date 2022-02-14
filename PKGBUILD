# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Your Name <youremail@domain.com>
pkgname=pylauncher
pkgver=3.10.2
pkgrel=1
epoch=
pkgdesc=""
arch=(i686 x86_64)
url=""
license=('GPL')
groups=()
depends=()
makedepends=(quilt)
checkdepends=()
optdepends=()
provides=('python' 'python2' 'python3')
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("https://raw.githubusercontent.com/python/cpython/v${pkgver}/PC/launcher.c")
noextract=()
sha256sums=('89723bd559837fbfa4bde5477aa5fc66b8b5adafdba6bd741178910396df19f3')
validpgpkeys=()

prepare() {
	cd "$srcdir"
	ln -s ../patches
	quilt push -a
}

build() {
	cd "$srcdir"
    defines=-D_CONSOLE
    if [[ $CARCH = x86_64 ]]; then
        defines="-D_M_X64 $defines"
    fi
	gcc -municode $defines -o python launcher.c -lversion -lshlwapi
}

# check() {
# 	cd "$pkgname-$pkgver"
# 	make -k check
# }

package() {
	cd "$srcdir"
	install -Dm 0755 python.exe "$pkgdir/usr/bin/python.exe"
}
