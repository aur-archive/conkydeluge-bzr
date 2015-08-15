# Contributor: kaivalagi <m_buck@hotmail.com>

pkgname=conkydeluge-bzr
pkgver=22
pkgrel=1
pkgdesc="Provides Deluge info, for use in Conky (for Deluge v 1.2.0 onwards)"
arch=('i686' 'x86_64')
url="https://code.launchpad.net/~m-buck/+junk/conkydeluge"
license=('GPL3')
depends=()
makedepends=('bzr')
install=$pkgname.install
source=()
md5sums=()
_bzrbranch=lp:~m-buck/+junk
_bzrmod=conkydeluge

build() {
  cd $srcdir
  msg "Connecting to the server...."
    
  bzr branch $_bzrbranch/$_bzrmod -q -r $pkgver

  msg "BZR checkout done or server timeout"
  msg "Starting make..."

  [ -d ./${_bzrmod}-build ] && rm -rf ./${_bzrmod}-build
  cp -r ./${_bzrmod} ./${_bzrmod}-build
  cd ./${_bzrmod}-build

  python setup.py build || return 1
  python setup.py install --root=$pkgdir || return 1
  install -D -m644 README $pkgdir/usr/share/conkydeluge/README || return 1
}
