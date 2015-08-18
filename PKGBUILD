# $Id: PKGBUILD 84372 2013-02-17 10:00:15Z lcarlier $
# Maintainer: Laurent Carlier <lordheavym@gmail.com>
# Contributor: Jesse Jaara <gmail.com: jesse.jaara>

pkgname=xvba-video-open
pkgver=0.8.0
pkgrel=2
pkgdesc="OSS version of xvba-video lib to enable hw video acceleration on AMD's HD series of GFX cards"
arch=('i686' 'x86_64')
url="http://www.splitted-desktop.com/~gbeauchesne/xvba-video/"
license=('GPL2')
depends=('catalyst-utils' 'libva')
makedepends=('mesa')
options=(!libtool)
source=(ftp://ftp.archlinux.org/other/community/xvba-video-open/xvba-video-${pkgver}.tar.gz
        http://developer.amd.com/wordpress/media/2012/10/xvba-sdk-0.74-404001.tar.gz
        xvba-video-h264-level51.patch
        xvba-video-0.8.0-glx-fix.patch
        fix-build-with-glext.h-version-85.patch)
md5sums=('d9ddec2e7f02c1fa533773918e88e311'
         'b8f56bc55aa70cb19dd12857fdc184cc'
         'bce1de0a8b274049568453a53e8fce6a'
         '5dc283eab46418eeef8e8be7c028a2ba')

build() {
  cd "${srcdir}/xvba-video-${pkgver}"

  # patch from opensuse (thanks vi0l0!)
  patch -Np1 -i ../xvba-video-h264-level51.patch
  patch -Np1 -i ../xvba-video-0.8.0-glx-fix.patch
  
  patch -Np1 -i ../fix-build-with-glext.h-version-85.patch

  export CPPFLAGS="${CPPFLAGS} -I${srcdir}/include"
  
  ./configure --disable-debug --enable-libxvba-dlopen --prefix=/usr
  make PYTHON=python2
}

package() {
  cd "${srcdir}/xvba-video-${pkgver}"

  make DESTDIR="${pkgdir}" install
}
md5sums=('d9ddec2e7f02c1fa533773918e88e311'
         'b8f56bc55aa70cb19dd12857fdc184cc'
         'bce1de0a8b274049568453a53e8fce6a'
         '5dc283eab46418eeef8e8be7c028a2ba'
         '69e8a9027affbaf7066e35bc97b3a984')
