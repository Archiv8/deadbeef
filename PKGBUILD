#!/bin/bash

# Created from the original package by Fabio 'Lolix' Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix, Lukas Fleischer <lfleischer@archlinux.org> and Alexey Yakovenko <waker@users.sourceforge.net>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors
# [FixMe]: Build Failure

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

pkgname=deadbeef
pkgver=1.9.1
pkgrel=1
pkgdesc="Modular GTK audio player for GNU/Linux"
arch=(x86_64 i686 pentium4 arm armv6h armv7h aarch64)
url="https://deadbeef.sourceforge.io/"
license=(
  "GPL2"
  "LGPL2.1"
  "ZLIB"
)
depends=(
  # Official Arch Linux repositories
  "alsa-lib"
  "faad2"
  "ffmpeg4.4"
  "gtk3"
  "jansson"
  "libcddb"
  "libcdio"
  "libdispatch"
  "libmad"
  "mpg123"
  "libvorbis"
  "libzip"
  "opusfile"
  "wavpack"
)
makedepends=(

  # Official Arch Linux repositories
  "clang"
  "curl"
  "flac"
  "imlib2"
  "intltool"
  "libpulse"
  "libsamplerate"
  "libsndfile"
  "libx11"
  "pkgconfig"
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
source=(
  "https://sourceforge.net/projects/deadbeef/files/travis/linux/${pkgver}/deadbeef-${pkgver}.tar.bz2"
)
sha512sums=(
  "2f959fb139078bbde3c1183019545ed3979b3c5dfc051794ea7a5ccf166156acc8d5dface3169ec705059f487d47c9b314c5400770a7572c22fbd0b903eefc5a"
)

export PKG_CONFIG_PATH='/usr/lib/ffmpeg4.4/pkgconfig'

build() {

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
