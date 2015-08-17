# Contributor: xRemaLx <anton.komolov@gmail.com>

pkgname='perl-extutils-config'
_pkgname='ExtUtils-Config'
pkgver=0.007
pkgrel=1
pkgdesc="ExtUtils::Config - A wrapper for perl's configuration"
arch=(any)
license=('perl')
url="http://search.cpan.org/dist/ExtUtils-Config/"
options=(!emptydirs)

depends=('perl>=5.10.1' 'perl-data-dumper')
makedepends=('perl')

provides=("extutils-config=${pkgver}" "ExtUtils::Config=${pkgver}" "perl-extutils-config=${pkgver}")

source=("http://search.cpan.org/CPAN/authors/id/L/LE/LEONT/${_pkgname}-${pkgver}.tar.gz")
md5sums=('2829c0dfa8a7e51b3f582efbee4bb128')
sha512sums=('168facb55560ad562bf1e4ca59dd0cee119e0059a8ac7d62283b7074078f73aabd5cc8c217754492a1e0bae61456b9ed9480f9710fbddd3865e5eddaf746052f')

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'"     \
      PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
      MODULEBUILDRC=/dev/null

    cd "${srcdir}/${_pkgname}-${pkgver}"
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  make install
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}

# vim:set ts=2 sw=2 et:
