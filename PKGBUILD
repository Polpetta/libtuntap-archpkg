# Maintainer: Augugrumi <augugrumi@gmail.com>
pkgname=libtuntap-git # '-bzr', '-git', '-hg' or '-svn'
pkgver=libtuntap.0.3.r46.9e9e2d9
pkgrel=1
pkgdesc=" The portable Tun/Tap devices configuration utility"
arch=('x86_64')
url="https://github.com/LaKabane/libtuntap"
license=('ISC')
groups=('linux-tools')
depends=()
makedepends=(git cmake) # 'bzr', 'git', 'mercurial' or 'subversion'
provides=("${pkgname%-VCS}")
conflicts=("${pkgname%-VCS}")
replaces=()
backup=()
options=()
source=("${pkgname%-git}::git://github.com/LaKabane/libtuntap.git")
noextract=()
md5sums=('SKIP')
srcdir=()

pkgver() {
  cd "$srcdir/${pkgname%-git}"
  printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"
}

build() {
  cd "$srcdir/${pkgname%-git}"
  rm -Rf ./build/
  mkdir ./build/
  cd ./build/
  cmake -DCMAKE_INSTALL_PREFIX=/usr/ -DENABLE_CXX=true ..
  make
}

package() {
	cd "$srcdir/${pkgname%-git}/build/"
	make DESTDIR="$pkgdir/" install/strip
}
 
