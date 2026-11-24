# Maintainer: Benedikt Heine <bebe@bebehei.de>

pkgname=linux-akulm
pkgver=0.4.1
pkgrel=1
pkgdesc="Pacman hooks to have loadable modules after pacman -Syu"
arch=('any')
url="https://github.com/bebehei/akulm"
license=('GPL3')
depends=('pacman' 'rsync')
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

	install -Dm644 "akulm-pre.hook" "${pkgdir}/usr/share/libalpm/hooks/00-akulm-pre.hook"
	install -Dm644 "akulm-post.hook" "${pkgdir}/usr/share/libalpm/hooks/90-akulm-post.hook"

	install -Dm644 "akulm.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/akulm.conf"

	install -Dm755 "akulm" "${pkgdir}/usr/bin/akulm"
}
