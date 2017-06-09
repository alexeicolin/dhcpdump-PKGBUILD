# Maintainer: Janne Heß <jannehess@gmail.com>

pkgname=dhcpdump
pkgver=1.8
pkgrel=2
pkgdesc='Parse DHCP packets'
arch=('x86_64' 'i686')
url='http://mavetju.org/unix/general.php'
license=('custom:dhcpdump')
depends=('libpcap')
source=("http://mavetju.org/download/dhcpdump-1.8.tar.gz"
        dhcpdump-1.8-includes.patch)
sha512sums=('52cd63d581a3c530c2f5baa66808d5b0241853651c720bd513b769b8301b4dff9c87243787014aea98a5b3ebed86ec317b58d262bf5031015141a4da50fb76e6'
            '1e95b1662a734174c79cba90d3b6a6ccd8cf7792b8d273a75fbe591ceea5edbe8e585123a82ce83515560a933ccf7e1f1296628200a9cc4fde279bb2b76ecced')

prepare() {
	cd "${srcdir}/${pkgname}-${pkgver}"
	patch -p1 < ../dhcpdump-1.8-includes.patch
}

build() {
	cd "${srcdir}/${pkgname}-${pkgver}"

	make all
}

package() {
	cd "${srcdir}/${pkgname}-${pkgver}"

	install -Dm755 ${pkgname} "${pkgdir}/usr/bin/${pkgname}"
	install -Dm644 ${pkgname}.8 "${pkgdir}/usr/share/man/man8/${pkgname}.8" # FIXME
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}"
}
