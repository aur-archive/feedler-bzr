# Maintainer: Alucryd <alucryd at gmail dot com>
# Contributor: Ner0 <darkelfdarkelf666@yahoo.co.uk>

pkgname=feedler-bzr
pkgver=329
pkgrel=1
pkgdesc="RSS feeds reader from Pantheon"
arch=('i686' 'x86_64')
url="https://launchpad.net/feedler"
license=('GPL3')
depends=('libwebkit3' 'gtk3' 'sqlheavy' 'libsoup' 'libunity' 'libxml2' 'libnotify' 'granite-bzr' 'dconf' 'libdbusmenu-gtk3' 'contractor-bzr')
makedepends=('bzr' 'vala' 'cmake')
install=${pkgname%-*}.install
source=("bzr+lp:${pkgname%-*}")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}"/${pkgname%-*}

  bzr revno
}

build() {
  cd "${srcdir}"/${pkgname%-*}

#  sed -i '/this.store.remove (folder_iter)/d' src/ui/sidebar.vala
#  sed -i '/this.store.remove (channel_iter)/d' src/ui/sidebar.vala

  if [[ -d build ]]; then
    rm -rf build
  fi
  mkdir build && cd build

  cmake .. -DCMAKE_INSTALL_PREFIX=/usr -DGSETTINGS_COMPILE=OFF
  make
}

package() {
  cd "${srcdir}"/${pkgname%-*}/build

  make GCONF_DISABLE_MAKEFILE_SCHEMA_INSTALL=1 DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
