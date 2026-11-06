# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=okular
pkgver=26.08.3
pkgrel=4
pkgdesc='Document Viewer'
arch=(x86_64)
url='https://apps.kde.org/okular/'
license=(GPL LGPL FDL)
depends=(discount
         djvulibre
         freetype2
         gcc-libs
         glibc
         plasma-activities
         karchive
         kbookmarks
         kcolorscheme
         kcompletion
         kconfig
         kconfigwidgets
         kcoreaddons
         kcrash
         ki18n
         kio
         kitemviews
         kparts
         kpty
         ktextwidgets
         kwallet
         kwidgetsaddons
         kwindowsystem
         kxmlgui
         libjpeg-turbo
         libkexiv2
         libspectre
         libtiff
         phonon-qt6
         poppler-qt6
         purpose
         qt6-base
         qt6-declarative
         qt6-speech
         qt6-svg
         threadweaver
         zlib)
makedepends=(ebook-tools
             extra-cmake-modules
             kdegraphics-mobipocket
             kdoctools)
optdepends=('ebook-tools: mobi and epub support'
            'kdegraphics-mobipocket: mobi support'
            'unarchiver: Comic Book Archive support (alternative)'
            'unrar: Comic Book Archive support')
groups=(kde-applications
        kde-graphics)

source=(
	https://download.kde.org/stable/release-service/$pkgver/src/$pkgname-$pkgver.tar.xz
	'0001-quit-app-when-last-tab-close.patch'
	'0002-limit-normal-and-aggressive-memory-cache.patch'
    '0001-add-florilegium.patch'
	)

sha256sums=('8db527297b4e6aa17b3063739f8e1a4fe206691428ffc4ff544053e111187412'
            '6d0f2e83e63c9fa31027344725ef3c659d508bc977dcf88099837c6ce2c789f3'
            '622f173b5d7c3b0c0d0a04bca77a4d07a3b5dc6b0d383787ccd19746bc763b5c'
            '5e324d67fb182956d8c7b12be8e3c662be96dfcb93fc7a0a0be66e5e7423e582')
options=(!zipman)

prepare() {
  cd ${srcdir}/$pkgname-$pkgver
  patch -Np1 -i ${srcdir}/0001-quit-app-when-last-tab-close.patch
  patch -Np1 -i ${srcdir}/0002-limit-normal-and-aggressive-memory-cache.patch
  patch -Np1 -i ${srcdir}/0001-add-florilegium.patch
}

build() {
  cmake -B build -S $pkgname-$pkgver \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
