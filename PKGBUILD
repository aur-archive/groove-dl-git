
# Maintainer: archtux <antonio dot arias99999 at gmail dot com>

pkgname=groove-dl-git
pkgver=56.f0b0538
pkgrel=1
pkgdesc="A Grooveshark song downloader in Python"
arch=('any')
url="https://github.com/jacktheripper51/groove-dl"
license=('GPL3')
depends=('python2-objectlistview' 'wxpython')
makedepends=('git')
source=('git+https://github.com/jacktheripper51/groove-dl.git'
         groovedl
         groove-dl.desktop)
md5sums=('SKIP'
         '608e03463d3847418b878ee1e39c7f69'
         '980007f3991f57e4546cf4310c011d3a')

prepare() {
  cd $srcdir/groove-dl/python

  # Fix gui.py
  sed -i '/MessageBox/d' gui.py
}

package() {
  cd $srcdir/groove-dl

  install -dm755 $pkgdir/usr/share/groove-dl
  cp python/* $pkgdir/usr/share/groove-dl

  # Desktop icon
  install -Dm644 misc/groove.ico $pkgdir/usr/share/pixmaps/groove.ico
  cd $srcdir
  install -Dm644 groove-dl.desktop $pkgdir/usr/share/applications/groove-dl.desktop  

  # Start file
  install -Dm755 groovedl $pkgdir/usr/bin/groove-dl
}

pkgver() {
  cd $srcdir/groove-dl
  echo $(git rev-list --count master).$(git rev-parse --short master)
}