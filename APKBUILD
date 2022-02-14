pkgname=glew-wayland
pkgver=2.2.0
pkgrel=1
pkgdesc="A cross-platform C/C++ extension loading library"
url="http://glew.sourceforge.net"
arch="all"
license="GPL-2.0-or-later"
options="!check"  # No test suite.
depends_dev="libxmu-dev libxi-dev mesa-dev glu-dev"
makedepends="$depends_dev"
subpackages="$pkgname-dev"
source="https://downloads.sourceforge.net/glew/glew-$pkgver.tgz"
provides="glew=2.2.0"
replaces="mesa-dev"
builddir="$srcdir/glew-$pkgver"

prepare() {
    default_prepare
    cd $builddir
    sed -i 's,lib64,lib,' config/Makefile.linux
}

build() {
	make STRIP= SYSTEM=linux-egl CFLAGS.EXTRA="-fPIC -DGLEW_EGL" LDFLAGS.GL=" -lEGL -lGL"
}

package() {
	make GLEW_DEST="$pkgdir/usr" SYSTEM=linux-egl install
}
sha512sums="
57453646635609d54f62fb32a080b82b601fd471fcfd26e109f479b3fef6dfbc24b83f4ba62916d07d62cd06d1409ad7aa19bc1cd7cf3639c103c815b8be31d1  glew-2.2.0.tgz
"
