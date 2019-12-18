# centos6.5_install_nodejs

### update gcc
```
wget http://ftp.tsukuba.wide.ad.jp/software/gcc/releases/gcc-5.2.0/gcc-5.2.0.tar.bz2
tar -xf gcc-5.2.0.tar.bz2
cd gcc-5.2.0
./contrib/download_prerequisites
mkdir gcc-temp
cd gcc-temp
../configure --enable-checking=release --enable-languages=c,c++ --disable-multilib
make -j4
make install
ls /usr/local/bin | grep gcc
/usr/sbin/update-alternatives --install  /usr/bin/gcc gcc /usr/local/bin/x86_64-unknown-linux-gnu-gcc-5.2.0 52
gcc -v
find / -name "libstdc++.so*"
cp /root/gcc-5.2.0/gcc-temp/stage1-x86_64-unknown-linux-gnu/libstdc++-v3/src/.libs/libstdc++.so.6.0.21 /usr/lib64
cd /usr/lib64
rm -rf libstdc++.so.6
ln -s libstdc++.so.6.0.21 libstdc++.so.6
strings /usr/lib64/libstdc++.so.6 | grep GLIBC
```
### update glibc
```
wget https://github.com/ltybenet/centos6.5_install_nodejs/raw/master/glibc-2.17.zip
cd glibc-2.17
yum -y install glibc-*
```
