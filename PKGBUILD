# $Id: PKGBUILD 78723 2012-10-23 10:10:22Z spupykin $
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer: Geoffroy Carrier <geoffroy.carrier@aur.archlinux.org>
# Contributor: lp76 <l.peduto@gmail.com>

pkgname=tasks
pkgver=3.3.90
pkgrel=1
pkgdesc="A simple to do list application that uses libecal"
arch=(i686 x86_64)
url="http://pimlico-project.org/tasks.html"
license=('GPL')
depends=('evolution-data-server>=3.6.0' 'xdg-utils' 'gtk3')
makedepends=('intltool')
install=tasks.install
source=(http://ftp.gnome.org/pub/GNOME/sources/tasks/3.3/tasks-$pkgver.tar.xz
	build-fix.patch)
md5sums=('1dc59c25378ef391ac2cdb49a1b117ef'
         '93ae1f98e7fe9721156b46c1cebb2c2c')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  unset LDFLAGS
  patch -p1 <$srcdir/build-fix.patch
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
  install -d "$pkgdir/usr/share/pixmaps"
  ln -sf "/usr/share/icons/hicolor/48x48/apps/tasks.png" \
      "$pkgdir/usr/share/pixmaps/tasks.png"
}
