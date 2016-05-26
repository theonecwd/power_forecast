# make -v 3.8.2
## steps
```
download make3.8.2.tar.gz
tar -zxvf make.tar.gz
./configure --prefix=/usr/share/make3.8.2/
make 
make install
```
## config multi make 
```
sudo alternatives --config make
sudo alternatives --install /usr/bin/make make  /usr/share/make3.8.2/bin/make  60
```

