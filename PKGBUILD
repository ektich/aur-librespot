# Maintainer: Christoph Gysin <christoph.gysin@gmail.com>

pkgname=librespot-git
_pkgname=librespot
pkgver=363.8971d3a
pkgrel=1
epoch=1
pkgdesc="An open source client library for Spotify."
arch=('i686' 'x86_64' 'armv6h' 'armv7h' 'aarch64')
url="https://github.com/plietar/librespot"
license=('MIT')
depends=('libvorbis' 'alsa-lib')
makedepends=('git' 'rust')
provides=('librespot')
conflicts=('librespot')
source=('git+https://github.com/plietar/librespot')
sha256sums=('SKIP')

pkgver()
{
    cd "$_pkgname"
    echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build()
{
    cd "$_pkgname"
    cargo build \
        --no-default-features \
        --features alsa-backend \
        --release
}

package()
{
    install -D -m 755 "$_pkgname"/target/release/librespot \
        "$pkgdir"/usr/bin/librespot
    install -D -m 644 "$_pkgname"/contrib/librespot.service \
        "$pkgdir"/usr/lib/systemd/system/librespot.service
    install -D -m 644 "$_pkgname"/LICENSE \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
