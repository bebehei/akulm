# Maintainer: Benedikt Heine <bebe@bebehei.de>

pkgname=linux-akulm
pkgver=0.3.1
pkgrel=2
pkgdesc="Pacman hooks to have loadable modules after pacman -Syu"
arch=('any')
url="https://github.com/bebehei/akulm"
license=('GPL3')
depends=('pacman')
source=(
	'akulm'
	'akulm-pre.hook'
	'akulm-post.hook'
	'akulm.tmpfiles'
)
# Skip checksumming, as these files are
# currently tracked in the same gitrepo
md5sums=('SKIP' 'SKIP' 'SKIP' 'SKIP')


package() {
	cd "${srcdir}"

	for hook in akulm-pre akulm-post; do
		install -Dm644 "${hook}.hook" "${pkgdir}/usr/share/libalpm/hooks/00-${hook}.hook"
	done

	install -Dm644 "akulm.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/akulm.conf"

	install -Dm755 "akulm" "${pkgdir}/usr/bin/akulm"
}
