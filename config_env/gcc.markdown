# gcc 4.8.2
## 编译gcc需要安装的库
```shell
yum install gmp gmp-devel
yum install mpfr-devel mpfr
yum install libmpc libmpc-devel
```

## steps
```
download gcc4.8.2.tar.gz
tar -zxvf gcc4.8.2.tar.gz
cd gcc4.8.2/
./configure --prefix=/usr/share/gcc4.8.2/
make
sudo make install
```
## qa
**/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: 找不到文件**
  
> yum install yum install install glibc-devel.i686

## config multi gcc
```
alternatives --install /usr/bin/gcc gcc /usr/share/gcc4.8.2/bin/gcc 60
alternatives --config gcc 
```
