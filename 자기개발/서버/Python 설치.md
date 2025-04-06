
```bash
cd /usr/src

sudo wget https://www.python.org/ftp/python/3.10.8/Python-3.10.8.tgz

sudo tar xzf Python-3.10.8.tgz

cd Python-3.10.8


sudo ./configure --enable-optimizations --with-ensurepip=install
sudo ./configure --enable-optimizations --without-pymalloc

sudo make -j$(nproc)

sudo make altinstall
```

#### Python 버전별로 관리

```bash
# update-alternatives에 추가
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.12 1
sudo update-alternatives --install /usr/bin/python3 python3  /usr/local/bin/python3.10 2
# 선택
sudo update-alternatives --config python3
```


완전 삭제
```
sudo rm -rf /usr/local/bin/python3.9
sudo rm -rf /usr/local/bin/python3.9-config
sudo rm -rf /usr/local/bin/pip3.9
sudo rm -rf /usr/local/lib/python3.9
sudo rm -rf /usr/local/include/python3.9
sudo rm -rf /usr/local/share/man/man1/python3.9.1


sudo find /usr/local -name '*python3.9*' -exec rm -rf {} +
```