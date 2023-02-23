# Maintainer: Rustmilian <######[@]######[.]me>

pkgname=kjobwidgets-git
pkgver=5.240.0_r467.g8f49632
pkgrel=1
pkgdesc='Widgets for tracking KJob instances'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(kcoreaddons-git kwidgetsaddons-git)
makedepends=(git extra-cmake-modules-git qt6-tools clang python-pyqt6 doxygen sip4)
optdepends=('python-pyqt6: for the Python bindings')
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(kf6-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DQT_MAJOR_VERSION=6 \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
