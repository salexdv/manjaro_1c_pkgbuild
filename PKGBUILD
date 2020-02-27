pkgname=1c_enterprise83
_pkgname1c=1C_Enterprise83
if test "$CARCH" == x86_64; then
    _pkgarch1c=$CARCH
else
    _pkgarch1c=('i386')
fi
pkgver=8.3.15
pkgrel=1869
pkgdesc="1C 8.3.15 for Linux"
license=('custom')
arch=($CARCH)
options=('!strip')
depends=('webkitgtk3')
makedepends=('pkgextract')
url="www.1c.ru"
source=(
$_pkgname1c-client-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-client-nls-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-common-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-common-nls-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-crs-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-server-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-server-nls-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-thin-client-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-thin-client-nls-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-ws-$pkgver-$pkgrel.$_pkgarch1c.rpm
$_pkgname1c-ws-nls-$pkgver-$pkgrel.$_pkgarch1c.rpm
)

md5sums=('5fbc0b9cffe26b9149e54759130560a0'
         'e4c21dc3900e011983c9f42994b7d5cb'
         '6b9cff10127b094d9b25e84c06643c78'
         'fec4944de31c13dc8489c6ef0843f334'
         '8f4273dd65a32bb811ea6ac8e051f3df'
         '5f1ac20ad01de6e3a6bb4feffa938c23'
         '1be6227a001b06ab1fd925247d431d9e'
         '6d6afc9d92bfeec69b7e3f5a1479e6cb'
         '9715373142fb4adf2ed2ccdc7b674dc4'
         '24e56989693aeec9c12b227649bf63e6'
         '6950b27e3b56e6cf308df0470e8ffa8e')
package() {
   cd $pkgdir
   cp -r $srcdir/usr $pkgdir
   cp -r $srcdir/etc $pkgdir
   cp -r $srcdir/opt $pkgdir
}
