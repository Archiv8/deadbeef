#!/bin/bash

# Created from original package by Fabio 'Lolix' Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix, Lukas Fleischer <lfleischer@archlinux.org> and Alexey Yakovenko <waker@users.sourceforge.net>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to.shellcheckrc file located in
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors
# [Fixed]: Build Failure

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

pkgname=deadbeef
pkgver=1.9.2
pkgrel=3
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
  "flac"
  "gtk3"
  "jansson"
  "libcddb"
  "libcdio"
  "libdispatch"
  "libmad"
  "libsamplerate"
  "libvorbis"
  "libzip"
  "mpg123"
  "opusfile"
  "wavpack"
)
makedepends=(
  # Official Arch Linux repositories
  "clang"
  "curl"
  "imlib2"
  "intltool"
  "libpulse"
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
  "fa4298fb3a89b3891c2f0403b2c66e20f64206101ad44f53be5208a69b33d3de3e0ced329cf090c17a1a3c4f7b28920baf5f8c964df2b6bdea6095465d0a02d9"
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
