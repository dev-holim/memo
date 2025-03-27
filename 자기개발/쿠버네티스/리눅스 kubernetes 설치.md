필수 패키지 설치
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```


kubernetes 설치
```bash
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo tee /etc/apt/trusted.gpg.d/kubernetes.asc
echo "deb https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /" | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt update
sudo apt install -y kubelet kubeadm kubectl
sudo systemctl enable kubelet
```


Master 노드 설정 (init)
```bash
sudo kubeadm init --pod-network-cidr=192.168.0.0/16
sudo kubeadm init --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address=192.168.0.32
```

Worker 노드 추가
```bah
# key 확인
sudo kubeadm token create --print-join-command
```

```
sudo kubeadm reset -f
```

```bash
# config
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

8080 에러가 났을 경우 config 과정 다시..
![](image%201.png)


#개발언어 #쿠버네티스