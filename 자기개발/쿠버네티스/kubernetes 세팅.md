mac에서 kubernets 시작
- minikube 설치
```bash
# 설치 
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-darwin-arm64 
sudo install minikube-darwin-arm64 /usr/local/bin/minikube 

# 도커 pull 
minikube start 
minikube delete 
minikube node add --worker 
minikube node delete minikube-m02
```

현재 셸에 zsh의 자동 완성 설정
```bash
source <(kubectl completion zsh)
```

자동 완성을 zsh 셸에 영구적으로 추가한다.
```bash
echo "[[ $commands[kubectl] ]] && source <(kubectl completion zsh)" >> ~/.zshrc
```


[[리눅스 kubernetes 설치]]

---

#개발언어 #쿠버네티스