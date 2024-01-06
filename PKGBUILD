# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Fox archlinux@foxfromabyss.dev
# Contributor: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Contributor: Truocolo <truocolo@aol.com>

_project=telegram
_Pkg=td
_pkg="${_Pkg}lib"
_pkgbase="lib${_Pkg}"
_pkgname="${_project}-${_pkg}"
pkgname="${_pkgname}-git"
pkgver=1.8.23
pkgrel=1
pkgdesc='Cross-platform library for building Telegram clients'
arch=(
  'i686'
  'x86_64'
  'armv7h'
  'arm'
  'powerpc'
  'aarch64'
  'pentium4'
)
url="https://core.${_project}.org/${_pkg}"
license=(
  'Boost')
depends=(
  'openssl'
  'zlib')
makedepends=(
  'make'
  'cmake'
  'gperf'
  'git'
)
provides=(
  "${_pkgname}=${pkgver}"
  "${_pkgbase}=${pkgver}"
)
conflicts=(
  "${_pkgname}"
  "${_pkgbase}"
)
_http="https://github.com"
_ns="${_pkg}"
_url="${_http}/${_ns}/${_Pkg}"
_local="file://${HOME}/${_Pkg}"
source=(
  # "git+${_url}.git"
  "git+${_local}"
)
sha256sums=(
  'SKIP'
)

pkgver() {
  grep \
    -oP \
    '(?<=TDLib VERSION )\S+' \
    "${_Pkg}/CMakeLists.txt"
}

build() {
  mkdir \
    -p \
    "${_Pkg}/build"
  cd \
    "${_Pkg}/build"
  cmake \
    -DCMAKE_INSTALL_PREFIX="${pkgdir}/usr" \
    -DCMAKE_BUILD_TYPE=Release \
    ..
  cmake \
    --build \
      .
}

package() {
  cd \
    "${_Pkg}/build"
  mkdir \
    -p \
    ${pkgdir}/usr
  cmake \
    --build \
      . \
      --target \
        install
}

# vim:set sw=2 sts=-1 et:
