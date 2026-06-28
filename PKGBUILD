# Maintainer: screamingatmypc <aur at hailsatan dot xyz>
# Forked by: hiraethecho <wyz2016zxc at outlook dot com>

pkgname=ninve
pkgdesc="A text user interface written in Rust to losslessly trim videos. Uses mpv to allow visual seeking."
pkgver=0.1.22
pkgrel=1
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url="https://github.com/hiraethecho/ninve"
license=('MIT')
makedepends=('cargo')
depends=('ffmpeg' 'mpv')
provides=('ninve')
conflicts=('ninve')

source=(
    "$pkgname-$pkgver.tar.gz::https://github.com/hiraethecho/ninve/archive/refs/tags/v$pkgver.tar.gz"
    "LICENSE::$url/raw/v$pkgver/LICENSE"
)
sha256sums=('SKIP' 'SKIP')

prepare() {
    cd "$pkgname-$pkgver"
    export RUSTUP_TOOLCHAIN=stable
    cargo fetch --locked --target "$(rustc -vV | sed -n 's/host: //p')"
}

build() {
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cd "$pkgname-$pkgver"
    cargo build --frozen --release --all-features
}

package() {
    cd "$pkgname-$pkgver"
    install -Dm0755 -t "$pkgdir/usr/bin/" "target/release/$pkgname"
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
