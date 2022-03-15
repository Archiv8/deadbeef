#!/bin/bash

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors
# FixMe: Build Failure

# Maintainer: Fabio "Lolix" Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix
# Contributor: Lukas Fleischer <lfleischer@archlinux.org>
# Contributor: Alexey Yakovenko <waker@users.sourceforge.net>
# Contributor: Ross Clark <contact@artisteducator.com>



pkgname=deadbeef
pkgver=1.8.8
pkgrel=4
pkgdesc="Modular GTK audio player for GNU/Linux"
arch=(x86_64 i686 pentium4 arm armv6h armv7h aarch64)
url="https://deadbeef.sourceforge.io/"
license=(GPL2 LGPL2.1 ZLIB)
depends=(
    # Official Arch Linux repositories
    "alsa-lib"
    "gtk3"
    "jansson"
    "libdispatch"
)
makedepends=(
    # Official Arch Linux repositories
    "clang"
    "curl"
    "faad2"
    "ffmpeg"
    "flac"
    "imlib2"
    "intltool"
    "libcddb"
    "libcdio"
    "libmad"
    "libpulse"
    "libsamplerate"
    "libsndfile"
    "libvorbis"
    "libx11"
    "libzip"
    "mpg123"
    "opusfile"
    "pkgconfig"
    "wavpack"
    "yasm"
    "zlib"
)
optdepends=(
    # Official Arch Linux repositories
    "alsa-oss: for OSS output plugin"
    "cdparanoia: for cd audio plugin"
    "dbus: for notification daemon support (OSD current song notifications)"
    "libice: optional dependency for gtkui session client support"
    "libogg: for ogg vorbis plugin"
    "libsidplay: for SID player plugin"
    "libsm: optional dependency for gtkui session client support"
    "pulseaudio: for PulseAudio output plugin"
)
source=("https://sourceforge.net/projects/deadbeef/files/travis/linux/${pkgver}/deadbeef-${pkgver}.tar.bz2")
sha512sums=("399f0e70eca5e102a9e73ff03199c89c6f28f3e0da96e793316d1af83f00e71f09f6cc81a3fd0b0f0d52fe9e0195a3b9ffb0cf7e7708c3ea7085f33a5ec08b47")

build () {
  cd "${srcdir}/${pkgname}-${pkgver}"
  export CC=clang CXX=clang++
  ./configure --prefix=/usr
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
  install -D COPYING -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
