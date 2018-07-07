# Contributor: Oleksiy Zakharov <alexzkhr@gmail.com>
pkgname=VC4CLStdLib
pkgver=0.4.0
pkgrel=1
pkgdesc="It is VC4CL implementation of the OpenCL standard-library and is required to build the VC4C compiler."

provides=('VC4CLStdLib')
arch=('i686' 'x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')


license=('MIT')
depends=(opencl-headers)
makedepends=(llvm clang)
source=(git://github.com/doe300/VC4CLStdLib)        
md5sums=('SKIP')


build() {   
  #compiler strings are taken from VC4C cmake file (which originally installs lib, but..)
  cd $srcdir
  clang -cc1 -triple spir-unknown-unknown -O3 -ffp-contract=off -cl-std=CL1.2 -cl-kernel-arg-info -cl-single-precision-constant -Wno-all -Wno-gcc-compat -Wdouble-promotion -Wno-undefined-inline -x cl -emit-pch -o include/VC4CLStdLib.h.pch include/VC4CLStdLib.h
  clang -cc1 -triple spir-unknown-unknown -O3 -ffp-contract=off -cl-std=CL1.2 -cl-kernel-arg-info -cl-single-precision-constant -Wno-all -Wno-gcc-compat -Wdouble-promotion -Wno-undefined-inline -x cl -emit-llvm-bc -o include/VC4CLStdLib.bc include/VC4CLStdLib.h
}

package() {  
  mkdir -p $pkgdir/usr/include/vc4cl-stdlib
  install -m644 $srcdir/VC4CLStdLib/include/*.* $pkgdir/usr/include/vc4cl-stdlib
}

