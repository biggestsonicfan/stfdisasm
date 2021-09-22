# Using the GNU Assembler and Linker
Included in this folder are copies of GNU binutils and an old copy of texinfo should you need it.
## For Linux users:
I recommend making and *not* installing these old versions of binutils. To make them, it is suggested to do the following:

 1. tar xjf binutils-2.16.1a.tar.bz2
 2. mkdir build && cd build
 3. ../binutils-2.16.1/config.guess (use the output  of this in the next bit)
 4. ../binutils-2.16.1/configure --target=i960-coff --enable-obsolete --prefix=/wherever/you/want/to/put/the/binutils/ --build=(config.guess ouput) --host=(config.guess ouput)--with-gcc --with-gnu-as --with-gnu-ld
 5. make tooldir=/wherever/you/want/to/put/the/binutils/
 6.  make tooldir=/wherever/you/want/to/put/the/binutils/ install

## For Windows users:
It is recommended to use Cygwin i686 for this due to the age of the source code. Follow the steps above for Linux except for --build and ---host you will use "i686-pc-cygwin", and to locate a folder on your hard drive for --prefix and tooldir, use /cygdrive/(Drive letter eg. "c" here). For example:

 1. tar xjf binutils-2.16.1a.tar.bz2
 2. mkdir build && cd build
 3. ../binutils-2.16.1/configure --target=i960-coff --enable-obsolete --prefix=/cygdrive/c/GNU960/install/binutils --build=i686-pc-cygwin --host=i686-pc-cygwin --with-gcc --with-gnu-as --with-gnu-ld
 4. make tooldir=/cygdrive/c/GNU960/install/binutils
 5. make  tooldir=/cygdrive/c/GNU960/install/binutils install
