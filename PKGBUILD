# Contributor: DonVla <donvla@users.sourceforge.net>

pkgname=lash
pkgver=0.6.0~rc2
_relver=0.6.0.594
pkgrel=5
pkgdesc="A session management system for JACK and ALSA"
arch=('i686' 'x86_64')
options=('!libtool')
url="http://lash-audio.org"
license=('GPL')
depends=('dbus-core' 'gtk2' 'jack' 'libxml2' 'python2')
install=$pkgname.install
source=("http://download.savannah.gnu.org/releases/lash/${pkgname}-${pkgver}.tar.bz2" "makefile.patch")
md5sums=('af1dc4f4ceb284b1b0845de4f4c2fe47'
         '24ceb7e3d008c25e1490102983165612')

build() {
  cd "${srcdir}/${pkgname}-${_relver}"
  patch -p0 < "${srcdir}/makefile.patch"

# Python2 fixes
  export PYTHON="python2"
  sed -i "s#env python#&2#" clients/lash_control

  ./configure --prefix=/usr
  make
}

package() {
  cd "${srcdir}/${pkgname}-${_relver}"
  make DESTDIR=${pkgdir} install
}
