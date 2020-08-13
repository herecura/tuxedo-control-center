# Based on the file created by the Manjaro Team:
# Maintainer: Philip Müller <philm[AT]manjaro[DOT]org>
# Contributor: Helmut Stult <helmut[AT]manjaro[DOT]org>

# Maintainer: Steven Seifried <gitlab@canox.net>

pkgname=tuxedo-control-center
pkgver=1.0.3
pkgrel=2
pkgdesc="An application helping you to tune your TUXEDO"
arch=(x86_64)
url="https://github.com/tuxedocomputers/tuxedo-control-center"
license=('GPL')
#depends=(alsa-lib hicolor-icon-theme libxcursor libxss libxtst nss tuxedo-cc-wmi)
depends=()
options=(!strip)
install=${pkgname}.install

source=("https://rpm.tuxedocomputers.com/opensuse/15.2/x86_64/${pkgname}_${pkgver}.rpm"
        tuxedo-control-center.install)
sha512sums=('cc76fe1b65f8b8bd8c43352cd64400c635e7b8db0fd07b71fff6caef690d9c3f415350cba5dbdab14c8dca5aadf045d458ab399bc58cb070b0ee2d11563252c0'
            '944637c5818e9aa88840dcde3171df5ce0c58c15927dc800b3481f13ab0a20aaf629d6538e16b752cf97f8a716921a99adb7058a262ce87096089eb2e96cde62')

package() {
    install -dm755 "${pkgdir}/usr"
    cp -av usr/share "${pkgdir}"/usr/
    cp -av opt "${pkgdir}"

    install -dm755 "${pkgdir}/usr/bin"
    ln -sfv /opt/tuxedo-control-center/tuxedo-control-center \
        "${pkgdir}/usr/bin/tuxedo-control-center"

    distpath='/opt/tuxedo-control-center/resources/dist/tuxedo-control-center'
    install -Dm644 \
        "${srcdir}${distpath}/data/dist-data/de.tuxedocomputers.tcc.policy" \
        "${pkgdir}/usr/share/polkit-1/actions/de.tuxedocomputers.tcc.policy"
    install -Dm644 \
        "${srcdir}${distpath}/data/dist-data/com.tuxedocomputers.tccd.conf" \
        "${pkgdir}/usr/share/dbus-1/system.d/com.tuxedocomputers.tccd.conf"

    install -dm755 "${pkgdir}/usr/lib/systemd/system"
    install -Dm644 \
        "${srcdir}${distpath}/data/dist-data/tccd.service" \
        "${pkgdir}/usr/lib/systemd/system/tccd.service"
    install -Dm644 \
        "${srcdir}${distpath}/data/dist-data/tccd-sleep.service" \
        "${pkgdir}/usr/lib/systemd/system/tccd-sleep.service"
}

