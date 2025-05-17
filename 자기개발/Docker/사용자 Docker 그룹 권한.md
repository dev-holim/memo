```bash
sudo usermod -aG docker $USER
```


docker.sock의 권한이 아래와 같다면 root -> docker로 변경해줘야 함
```bash
ls -l /var/run/docker.sock
# srw-rw---- 1 root root 0 May 16 23:50 /var/run/docker.sock
```

아래와 같이 docker가 없다면 docker를 추가
```bash
groups
# hoya adm cdrom sudo dip plugdev lxd
```

```bash
newgrp docker
# or
sudo groupadd docker
```

```bash
groups
# hoya adm cdrom sudo dip plugdev lxd docker
```

```bash
sudo chown root:docker /var/run/docker.sock
```

```bash
ls -l /var/run/docker.sock
# srw-rw---- 1 root docker 0 May 16 23:50 /var/run/docker.sock
```