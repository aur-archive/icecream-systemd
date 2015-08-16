#Contributor: Isaac C. Aronson <isaac@pingas.org>

pkgname=icecream-systemd
pkgver=0.9.7
pkgrel=2
pkgdesc="Icecream takes compile jobs from your build and distributes it to remote machines allowing a parallel build on several machines. This package includes files needed for use with systemd."
url="http://en.opensuse.org/Icecream"
license="GPL"
depends=('gcc')
provides=('icecream' 'icecream1')
conflicts=('icecream' 'icecream1')
optdepends=('icemon-svn' 'systemd')
backup=('etc/icecream.conf')
arch=('i686' 'x86_64')
install=icecream.install
source=(ftp://ftp.suse.com/pub/projects/icecream/icecc-$pkgver.tar.bz2 icecream-daemon icecream-scheduler-daemon icecream.conf icecream.service icecream-scheduler.service icecreamd icecream-schedulerd)
md5sums=('c06900c2f4011428d0d48826a04f74fb'
         'ada145106134e30b6b22dfb5e982f7e3'
         '7fc4e0b1b56600673c0c1c3087928cb9'
         '51aae781751a11d108e174352d6e739d'
         '256dbfd08c2c7b51cbb62de3ae830afd'
         'b97228cf444282a995fa228b9969d7da'
         'aad41fb7f4b7dacf4321a64f55e65e39'
         '62295c0d75d9fd67a8dcf88ab3d04d7a')

build() {
        cd $startdir/src/icecc-$pkgver
        ./configure --prefix=/usr/lib/icecream
        make
}

package() {
        make DESTDIR=$startdir/pkg install
        install -D -m755 ../icecream-daemon $startdir/pkg/etc/rc.d/icecream
        install -D -m755 ../icecream-scheduler-daemon $startdir/pkg/etc/rc.d/icecream-scheduler
        install -D -m755 ../icecream.conf $startdir/pkg/etc/icecream.conf
        install -D -m755 ../icecreamd $startdir/pkg/usr/lib/icecream/icecreamd
        install -D -m755 ../icecream-schedulerd $startdir/pkg/usr/lib/icecream/icecream-schedulerd
        install -D -m644 ../icecream-scheduler.service $startdir/pkg/lib/systemd/system/icecream-scheduler.service
        install -D -m644 ../icecream.service $startdir/pkg/lib/systemd/system/icecream.service
}
