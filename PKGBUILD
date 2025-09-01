pkgname=gawk
pkgver=5.3.2
pkgrel=2
pkgdesc="GNU version of awk"
arch=('x86_64')
url="https://www.gnu.org/software/gawk/"
license=('GPL-3.0-or-later')
groups=('base' 'base-devel')
depends=(
    'bash'
    'glibc'
    'mpfr'
)
source=(https://ftp.gnu.org/gnu/${pkgname}/${pkgname}-${pkgver}.tar.xz)
sha256sums=(f8c3486509de705192138b00ef2c00bbbdd0e84c30d5c07d23fc73a9dc4cc9cc)

prepare() {
    cd ${pkgname}-${pkgver}

    sed -i 's/extras//' Makefile.in
}

build() {
    cd ${pkgname}-${pkgver}

    local configure_args=(
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
}

package() {
    cd ${pkgname}-${pkgver}

    make DESTDIR=${pkgdir} install

    ln -sv gawk.1 ${pkgdir}/usr/share/man/man1/awk.1

    install -vdm755 ${pkgdir}/usr/share/doc/${pkgname}-${pkgver}
    cp    -v doc/{awkforai.txt,*.{eps,pdf,jpg}} ${pkgdir}/usr/share/doc/${pkgname}-${pkgver}
}
