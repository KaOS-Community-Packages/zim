pkgname=zim
pkgver=0.63
pkgrel=1
pkgdesc="A WYSIWYG text editor that aims at bringing the concept of a wiki to the desktop"
arch=('x86_64')
license=('GPL' 'PerlArtistic')
url="http://zim-wiki.org/"
depends=('pygtk' 'ttf-dejavu')
optdepends=('bzr: Version Control plugin'
            'git: Version Control plugin'
            'mercurial: Version Control plugin'
            'gnuplot: Insert Gnuplot plugin'
            'r: Insert GNU R Plot plugin'
            'lilypond: Insert Score plugin'
            'texlive-bin: Insert Equation plugin')
install=zim.install
source=(http://www.zim-wiki.org/downloads/${pkgname}-${pkgver}.tar.gz)
md5sums=('a23d5da4e71483285ce0e17ca92d0206')

build() {
	cd ${srcdir}/${pkgname}-${pkgver}

    # python2 fixes
    for file in zim/inc/xdot.py zim/_version.py; do
        sed -i 's_#!/usr/bin/env python_#!/usr/bin/env python2_' $file
    done

	sed -i 's|\t\tinstall_class.run(self)|&\n\t\treturn None|' setup.py
}

package() {
	cd ${srcdir}/${pkgname}-${pkgver}

	python2 setup.py install --root=${pkgdir} --optimize=1
}
