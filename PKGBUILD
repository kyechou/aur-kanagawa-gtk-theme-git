# Maintainer: Kuan-Yen Chou <kuanyenchou at gmail dot com>

pkgbase=kanagawa-gtk-theme-git
pkgname=('kanagawa-icon-theme-git' 'kanagawa-gtk-theme-git')
pkgver=r34.825ac8d9
pkgrel=1
pkgdesc='GTK theme with the Kanagawa colour palette'
arch=('any')
url='https://github.com/Fausto-Korpsvart/Kanagawa-GKT-Theme'
license=('GPL3')
depends=('sassc' 'gtk-engine-murrine' 'gnome-themes-extra')
makedepends=('git')
source=("$pkgbase::git+https://github.com/Fausto-Korpsvart/Kanagawa-GKT-Theme.git")
sha256sums=('SKIP')

pkgver() {
    cd "$srcdir/$pkgbase"
    if git describe --long --tags >/dev/null 2>&1; then
        git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
    else
        printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git describe --always)"
    fi
}

package_kanagawa-icon-theme-git() {
    cd "$srcdir/$pkgbase"
    sed -e 's/oomox-//' -i icons/*/index.theme
    mkdir -p "$pkgdir/usr/share/icons"
    cp -r icons/Kanagawa "$pkgdir/usr/share/icons"
}

package_kanagawa-gtk-theme-git() {
    cd "$srcdir/$pkgbase/themes"
    ./build.sh
    mkdir -p "$pkgdir/usr/share/themes"
    ./install.sh --dest "$pkgdir/usr/share/themes" --theme all
}

# vim: set ts=4 sw=4 et :
