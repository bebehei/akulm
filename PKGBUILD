# Maintainer: Benedikt Heine <bebe@bebehei.de>

pkgname=linux-akulm
pkgver=0.2.4
pkgrel=1
pkgdesc="Pacman hooks to have loadable modules after pacman -Syu"
arch=('any')
url="https://github.com/bebehei/akulm"
license=('GPL3')
depends=('pacman')
source=(
	'akulm'
	'akulm-pre.hook'
	'akulm-gc.hook'
	'akulm-post.hook'
	'akulm.tmpfiles'
)
# Skip checksumming, as these files are
# currently tracked int the same gitrepo
md5sums=('SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP')


package() {
	cd "${srcdir}"

	for hook in akulm-pre akulm-gc akulm-post; do
		install -Dm644 "${hook}.hook" "${pkgdir}/usr/share/libalpm/hooks/${hook}.hook"
	done

	install -Dm644 "akulm.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/akulm.conf"

	install -Dm755 "akulm" "${pkgdir}/usr/bin/akulm"
}
