pkgname=zim
pkgver=0.65
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
            'texlive-bin: Insert Equation plugin'
            'scrot: insert screen capture')
install=zim.install
source=(http://www.zim-wiki.org/downloads/${pkgname}-${pkgver}.tar.gz)
sha512sums=('dee652087d3d986b80353e9087abe363392354f40db11f8819d0b3f3c6f133c08c66c651a92ed77c1656f1135998ac02622eca08ac2e28c8fb3149a724a0f7fb')

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
