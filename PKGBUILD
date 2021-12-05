# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=xdg-desktop-portal-kde-git
pkgver=5.23.80_r408.g218e8c2
pkgrel=1
pkgdesc='A backend implementation for xdg-desktop-portal using Qt/KF5'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(kirigami2-git plasma-framework-git)
makedepends=(extra-cmake-modules-git plasma-wayland-protocols-git)
provides=(xdg-desktop-portal-impl)
groups=(plasma-git)
source=("git+https://invent.kde.org/plasma/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
