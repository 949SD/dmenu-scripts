# Maintainer: David K david.dk949@gmail.com
pkgname=dmenu-scripts
pkgver=unknown
pkgrel=2
pkgdesc="Various scripts that use dmenu"
arch=('any')
url="https://github.com/dk949/$pkgname"
license=('MIT')
optdepends=(
    'xdotool: for greek and sym'
    'xclip: for greek and sym'
    'unclutter: for screenshot'
    'unclutter: for screenshot'
    'imagemagick: for screenshot'
)
provides=(
    'bookmark'
    'greek'
    'screenshot'
    'sym'
)
source=("git+$url")
md5sums=() #autofill using updpkgsums
sha256sums=('SKIP')

pkgver() {
    ___DATE="$(git -C "$pkgname" log -1 --format='%cd' --date=format:'%F')"
    ___DATE_TIME="$___DATE 00:00"
    ___COMMIT_COUNT=$(git -C "$pkgname" rev-list --count HEAD --since="$___DATE_TIME")
    echo "$(date -d "$___DATE" +'%Y%m%d')_$___COMMIT_COUNT"
    unset ___DATE
    unset ___DATE_TIME
    unset ___COMMIT_COUNT
}

build() {
    cd "$pkgname"
    make -j
}

package() {
    cd "$pkgname"

    make DESTDIR="$pkgdir/" PREFIX="/usr" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
