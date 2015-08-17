# Maintainer: Anselmo L. S. Melo <anselmolsm@gmail.com>

pkgname=qtphonon-git
pkgver=20120620
pkgrel=1
pkgdesc="Qt 5: qtsvg module"
groups=('qt5' 'qt5-addons')
arch=('i686' 'x86_64')
url="https://qt.gitorious.org/qt/qtphonon"
license=('LGPL')
depends=('qtbase-git')
makedepends=('git')
options=('!libtool')
source=()
md5sums=()

_gitroot="git://gitorious.org/qt/qtphonon.git"
_gitname=qtphonon

build() {
	cd "${srcdir}"

	if [ ! -d "${srcdir}/${_gitname}" ]; then
		git clone ${_gitroot} ${_gitname}
	else
		cd ${_gitname} && git pull origin
	fi

	msg "GIT checkout done."

	cd "${srcdir}"
	cp -rf "${_gitname}" "${_gitname}-build"
	cd "${_gitname}-build"

	. /etc/profile.d/qt5.sh
	qmake
}

package() {
	cd "${srcdir}/${_gitname}-build"

	make INSTALL_ROOT="${pkgdir}" install
}
