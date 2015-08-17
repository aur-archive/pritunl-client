# Maintainer: Pritunl <contact@pritunl.com>

pkgname=pritunl-client
pkgver=1.0.601.3
pkgrel=1
pkgdesc="Pritunl VPN Client"
arch=("any")
license=("custom")
url="https://github.com/pritunl/${pkgname}"
depends=(
    "python2"
    "python2-requests"
    "net-tools"
    "iproute2"
    "openvpn"
)
makedepends=(
    "python2-distribute"
)
provides=("${pkgname}")
conflicts=(
    "pritunl-client"
    "pritunl-client-dev"
    "pritunl-client-gtk"
    "pritunl-client-gtk-dev"
)
install=${pkgname}.install
source=("${url}/archive/${pkgver}.tar.gz")
sha256sums=("ad66609c9ec1d01a447276443717d76298561eb91abab876e8822f6c7d2c0437")
options=("emptydirs")
backup=(
    "var/log/${pkgname}.log"
    "var/log/${pkgname}.log.1"
)

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    python2 setup.py build
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    mkdir -p "${pkgdir}/etc/pritunl_client"
    python2 setup.py install --root="${pkgdir}" --prefix=/usr --no-upstart --no-gtk
}
