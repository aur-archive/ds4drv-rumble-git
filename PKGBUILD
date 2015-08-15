# Maintainer: Lauri Niskanen <ape@ape3000.com>
# Contributor: George Gibbs <vash63 at gmail dot com>

pkgname=ds4drv-rumble-git
pkgver=57
pkgrel=1
pkgdesc="Sony DualShock 4 Bluetooth Driver with Rumble support"
arch=('any')
url="https://github.com/chrippa/ds4drv"
license=('MIT')
depends=('python-setuptools' 'bluez-utils' 'python-evdev-rumble-git')
makedepends=('perl' 'git')
conflicts=('ds4drv')
provides=('ds4drv')
install=ds4drv.install
source=("${pkgname%}::git+https://github.com/Ape/ds4drv.git#branch=rumble" 50-uinput.rules)
sha256sums=('SKIP'
            'b67455c70a2559fbb6872949974c79503f9005ec44fd99ea2ca1f8ae47fe4d09')

pkgver() {
	cd "${srcdir}"/${pkgname}
	git rev-list --count HEAD
}

package() { 
	mkdir -pm755 $pkgdir/etc/udev/rules.d
        cp 50-uinput.rules $pkgdir/etc/udev/rules.d/50-uinput.rules
	cd "$srcdir/$pkgname"
	mkdir -pm755 $pkgdir/usr/share/licenses/$pkgname
	cp LICENSE $pkgdir/usr/share/licenses/$pkgname/
	python setup.py install --root="$pkgdir/" --optimize=1
	mkdir -pm755 $pkgdir/etc/systemd/system
	cp $srcdir/$pkgname/ds4drv.service $pkgdir/etc/systemd/system/ds4drv.service
}

# vim: ft=sh syn=sh
