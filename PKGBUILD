# Maintainer: Y7n05h <Y7n05h(aT)protonmail--d0t--com>
# Contributor: Lyr <lyr-7d1h@pm.me>

pkgname=sworkstyle-custom-git
_pkgname=sworkstyle
pkgver=1.2.2.r2.g668ed8e
pkgrel=2
pkgdesc="Swayest Workstyle - This tool will rename workspaces to the icons configured. Mainly meant for Sway WM"
arch=("x86_64")
url="https://github.com/frap129/swayest_workstyle"
license=("MIT")
depends=("gcc-libs")
optdepends=("otf-font-awesome")
makedepends=("cargo" "git")
source=("$pkgname::git+$url")
conflicts=(sworkstyle)
sha256sums=('SKIP')

pkgver() {
	cd ${pkgname}
	git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}
prepare() {
	cd ${pkgname}
	cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}
build() {
	cd ${pkgname}
	export RUSTFLAGS="-C target-cpu=native"
	export RUSTUP_TOOLCHAIN=stable
	export CARGO_TARGET_DIR=target
	cargo build --frozen --release
}
check() {
	cd ${pkgname}
	export RUSTUP_TOOLCHAIN=stable
	cargo test --frozen
}

package() {
	cd ${pkgname}
	install -D -m755 "target/release/$_pkgname" "$pkgdir/usr/bin/sworkstyle"
	install -D -m644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
