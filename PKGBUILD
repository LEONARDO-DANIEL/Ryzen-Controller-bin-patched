pkgname=ryzen-controller-bin
_pkgver=2.6.0
pkgver=${_pkgver//[+-]/_}
pkgrel=2
pkgdesc="(DEPRECATED) A minimal Electron application to use ryzenAdj through a friendly interface"
arch=('x86_64')
depends=('gtk3' 'ryzenadj-git')
provides=('ryzen-controller')
conflicts=('ryzen-controller' 'ryzencontroller')
url="https://gitlab.com/ryzen-controller-team/ryzen-controller"
license=('CC0 1.0 Universal')
source=(
  "ryzen-controller_${_pkgver}_amd64.deb::https://gitlab.com/ryzen-controller-team/ryzen-controller/-/jobs/3178939815/artifacts/raw/dist/deb/ryzen-controller_2.6.0_amd64.deb"
  "ryzen-launcher"
  "ryzencontroller"
  "ryzen-controller.desktop"
  "ryzen-controller.png"
  "remove-ryzen-controller.hook"
)
  
sha256sums=('ab611dca6894aef92ab8159890efa7f21b5ded3391444f994977efbdf2ff0a37'
'891dd7b6a4a9771b4976010530700e8a8abfeb6ad9c0cf70b026d91dea5bb2bf'
'7e866fa9a201044bff077bfcef3afba94762db3856cc727899ebb815e4e0200c'
'433cadddf16a7a98df6f3b958e6ae45b3afb3a78aaa3aa96a1db02c946572ed1'
'2a2d035008beb7c623e208bf5b6bf06c270157838c40d7375aefa9aee8f5f77f'
'785755b6bdef8b3e125d046c7ba0d2f7463b7bf83daac0425c6c458ae65cad45')








package() {
    bsdtar -xvf data.tar.xz -C "$pkgdir"
    chmod -R g-w "$pkgdir"/{usr,opt}

    install -Dm755 "$srcdir/ryzen-launcher" "$pkgdir/usr/local/bin/ryzen-launcher"
    install -Dm440 "$srcdir/ryzencontroller" "$pkgdir/etc/sudoers.d/ryzencontroller"
    install -Dm644 "$srcdir/ryzen-controller.desktop" "$pkgdir/usr/share/applications/ryzen-controller.desktop"
    install -Dm644 "$srcdir/ryzen-controller.png" "$pkgdir/usr/share/icons/hicolor/128x128/apps/ryzen-controller.png"
    install -Dm644 "$srcdir/remove-ryzen-controller.hook" "$pkgdir/usr/share/libalpm/hooks/remove-ryzen-controller.hook"
    chmod 750 "$pkgdir/etc/sudoers.d"
}


