pkgname=zim
pkgver=0.66
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
sha512sums=('9693dba8ee6ad915a85ca999674350b278043559ba4adf93c03c8815211ecab451a6e2dceaf62ea7048609eb86f19485f2dd77dbaaf6f2d81f97f6450bf25ca9')

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
