# Maintainer: peace4all <markspost at rocketmail dot com>

pkgname=blender2.62-bin
pkgver=2.62
pkgrel=1
pkgdesc="Blender 2.62, for those that require an older version of 2.6, for plugins etc. (binary version)"
arch=('i686' 'x86_64')
url="http://blender.org/"
license=('GPL')
depends=('libgl' 'libx11' 'libxau' 'libxcb' 'libxdamage' 'libxdmcp' 'libxext' 'libxfixes' 'libxi' 'libxxf86vm' 'python' 'sdl' 'zlib')
provides=('blender')
conflicts=('blender' 'blender2.4-bin')
install=blender.install
options=('!strip')

#source and md5sums sorted below for 32 and 64 bit installations
source=("http://download.blender.org/release/Blender2.62/blender-2.62-linux-glibc27-i686.tar.bz2" "blender.desktop")
md5sums=('93348a4cb3e77ebf5f6e6e8dcf88a9d2'
         'c8da55103a25e8baa8a7cd4a7579b23d')
 if test "$CARCH" == x86_64; then
source=("http://download.blender.org/release/Blender2.62/blender-2.62-linux-glibc27-x86_64.tar.bz2" "blender.desktop")
md5sums=('3258f4c9d800a824a835c58f59934508'
          'c8da55103a25e8baa8a7cd4a7579b23d')
 fi


build() {
  mkdir -p $pkgdir/usr/{share/blender,share/icons/hicolor,/share/doc/blender,bin}
  case ${CARCH} in
    i686)
      cd $srcdir/blender-$pkgver-linux-glibc27-i686
      ;;
    x86_64)
      cd $srcdir/blender-$pkgver-linux-glibc27-x86_64
      ;;
  esac
  
  #copy application files
  cp -r 2.62 $pkgdir/usr/share/blender
  cp -r icons/* $pkgdir/usr/share/icons/hicolor
  cp blender $pkgdir/usr/share/blender
  cp blenderplayer $pkgdir/usr/share/blender

  #copy docs
  cp GPL-license.txt $pkgdir/usr/share/doc/blender
  cp Python-license.txt $pkgdir/usr/share/doc/blender
  cp copyright.txt $pkgdir/usr/share/doc/blender
  cp readme.html $pkgdir/usr/share/doc/blender

  #create links to bin files
  ln -s /usr/share/blender/blender $pkgdir/usr/bin/blender
  ln -s /usr/share/blender/blenderplayer $pkgdir/usr/bin/blenderplayer

  # desktop file from blender 2.62
  install -Dm644 $srcdir/blender.desktop $pkgdir/usr/share/applications/blender.desktop
}
