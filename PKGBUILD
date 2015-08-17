# Maintainer: Limao Luo <luolimao+AUR@gmail.com>
# Maintainer: perlawk

pkgname=unicon
pkgver=12.1
pkgrel=3
pkgdesc="Unicon is a very high level, goal-directed, object-oriented, general purpose applications language."
arch=(i686 x86_64)
url=http://unicon.sourceforge.net
license=(GPL)
conflicts=(icon unicon-svn)
provides=(icon)
options=(!emptydirs !strip)
source=(http://$pkgname.sourceforge.net/dist/uni.zip)
depends=( 'libgl' 'libiodbc' 'libjpeg-turbo' 'libxext')


build() {
    cd "$srcdir/$pkgname"
    if [[ $CARCH == "x86_64" ]] ; then
#        make Configure name=x86_64_linux
        CFLAGS='' make X-Configure name=x86_64_linux
    else
        CFLAGS='' make X-Configure name=x86_32_linux
    fi
    make Unicon 
    sed -i "s:^\t\tcp doc.*:\t\t# omitted:" Makefile
}

package() {
    cd "$srcdir/$pkgname"
		mkdir -p "$pkgdir"/usr/share/unicon/{bin,ipl,uni,doc}
		cp bin/[a-qs-z]*  "$pkgdir"/usr/share/unicon/bin
		cp -a ipl/lib ipl/incl ipl/gincl ipl/mincl "$pkgdir"/usr/share/unicon/ipl
		cp -a uni/lib "$pkgdir"/usr/share/unicon/uni
		cp ipl/docs/* "$pkgdir"/usr/share/unicon/doc
		rm -f "$pkgdir"/usr/share/unicon/doc/README
		cp ipl/gdocs/[a-z]* "$pkgdir"/usr/share/unicon/doc
		rm -f "$pkgdir"/usr/share/unicon/doc/README
		cp ipl/mdocs/[a-z]* "$pkgdir"/usr/share/unicon/doc
}
md5sums=('62b3ee4ef20c470545f47e094965ca49')
md5sums=('2960a5d93705ef8d26cdc2bd3f6dadbc')
