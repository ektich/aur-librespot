# Maintainer: Christoph Gysin <christoph.gysin@gmail.com>

pkgname=librespot
pkgver=0.1.3
pkgrel=2
pkgdesc="Open Source Spotify client library"
arch=('i686' 'x86_64' 'armv6h' 'armv7h' 'aarch64')
url="https://github.com/librespot-org/librespot"
license=('MIT')
depends=('libvorbis' 'alsa-lib')
makedepends=('rust')
provides=('librespot')
conflicts=('librespot')
source=("https://github.com/librespot-org/librespot/archive/v$pkgver.tar.gz")
sha256sums=('SKIP')

build()
{
    cd "$pkgname-$pkgver"
    cargo build \
        --no-default-features \
        --features alsa-backend \
	--features pulseaudio-backend \
        --release
}

package()
{
    install -D -m 755 "$pkgname-$pkgver"/target/release/librespot \
        "$pkgdir"/usr/bin/librespot
    install -D -m 644 "$pkgname-$pkgver"/contrib/librespot.service \
        "$pkgdir"/usr/lib/systemd/system/librespot.service
    install -D -m 644 "$pkgname-$pkgver"/LICENSE \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
