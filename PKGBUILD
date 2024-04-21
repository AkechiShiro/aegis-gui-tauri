pkgname=aegis-gui-tauri
pkgver=86.283cb70
pkgrel=1
pkgdesc="Tauri-based GUI front-end for Aegis."
arch=('x86_64' 'aarch64')
url="https://github.com/Athena-OS/${pkgname}"
license=('GPL3')
depends=('glib2' 'gtk3' 'libappindicator-gtk3' 'svt-av1' 'util-linux-libs' 'webkit2gtk')
makedepends=('cargo-tauri' 'pnpm' 'yarn' 'git')
source=("git+https://github.com/mwaurawakati/$pkgname.git")
sha512sums=('SKIP')

pkgver() {
  cd $pkgname

  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
    cd $pkgname
    export NO_STRIP=true
    yarn install
    NO_STRIP=true 
    unset SOURCE_DATE_EPOCH
    cargo tauri build
}

package() {
    cd $pkgname
    install -Dm 755 "src-tauri/target/release/$pkgname" "$pkgdir/usr/bin/$pkgname"
}
