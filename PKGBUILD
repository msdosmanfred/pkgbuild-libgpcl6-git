# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Guidelines specific to Bazaar, Git, Mercurial and Subversion packages.
# Other VCS sources are not natively supported by makepkg yet.

# Maintainer: Alexander Höfer <hoefer9(AT)gmail.com>
pkgname=libgpcl6-git
pkgver=ghostpdl.r11571.fc796c374
pkgrel=1
pkgdesc="GhostPCL library for use with 86Box's PCL printing feature"
arch=('x86_64')
url="https://www.ghostscript.com/"
license=('AGPL-3.0-or-later')
depends=('freetype2' 'libxft' 'ghostscript')
makedepends=('git' 'base-devel') # 'bzr', 'git', 'mercurial' or 'subversion'
provides=("libgpcl6")
source=("${pkgname}::git+https://github.com/ArtifexSoftware/ghostpdl.git")
sha256sums=('SKIP')

# Please refer to the 'USING VCS SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	cd $srcdir/$pkgname
	git describe --long --abbrev=7 | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
	cd $srcdir/$pkgname
	./autogen.sh --prefix=/usr
}

build() {
	cd $srcdir/$pkgname
	make so-only
}

check() {
	cd $srcdir/$pkgname
	make -k check
}

package() {
	cd $srcdir/$pkgname
	make DESTDIR="$pkgdir/" install-so-gpcl6
}
