pkgname=leveldb
pkgver=1.20
pkgrel=1
pkgdesc="A fast and lightweight key/value database library"
arch=('x86_64')
url="https://github.com/google/leveldb"
license=('BSD')
depends=('gperftools' 'snappy')
makedepends=('git')
source=("$pkgname-$pkgver.tar.gz::https://github.com/google/leveldb/archive/v$pkgver.tar.gz")
sha1sums=('df11440c30deed5987263730180225db98de9f57')

build() {
  make -C "$pkgname-$pkgver"
}

check() {
  make -C "$pkgname-$pkgver" check
}

package() {
  cd "$pkgname-$pkgver"

  install -dm755 \
      "$pkgdir"/usr/{include/leveldb,lib} \
      "$pkgdir"/usr/share/doc/"$pkgname"

  install -m644 -t "$pkgdir/usr/lib" "out-static/libleveldb.a"
  cp -P out-shared/libleveldb.so* "$pkgdir/usr/lib"
  install -m644 -t "$pkgdir/usr/include/leveldb" include/leveldb/*
}
