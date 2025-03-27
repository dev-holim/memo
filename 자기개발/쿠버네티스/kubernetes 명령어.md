적용 
```bash
kubectl apply -f { 파일명.yaml 혹은 URL }
kubectl create -f { 파일명.yaml 혹은 URL }
```

pod 적용 확인 
```bash
kubectl get pods
```

pod로 진입
```bash
kubectl exec -it { metadata > name } -- bash
kubectl exec -it nginx-pod -- bash

kubectl exec -it { metadata > name } -- sh
kubectl exec -it nginx-pod -- sh
```

포트 포워드
```bash
kubectl port-forward pod/{ metadata > name } {pod에서의 포트}:{로컬에서의 포트} kubectl port-forward pod/nginx-pod 80:80
```

pod 삭제
```bash
kubectl delete pod { metadata > name }
kubectl delete pod nginx-pod
```

pod 로그 확인
```bash
kubectl describe pods { metadata > name }
kubectl describe pods nginx-pod

kubectl logs { metadata > name }
kubectl logs nginx-pod
```

한번에 전체 삭제
```bash
kubectl delete all --all
```

pod 생성
```bash
kubectl run {이름} --image={도커 이미지} --port {포트}
kubectl run webserver --image=nginx:1.14 --port 80
```

deployment 생성
```bash
kubectl create deployment {이름} --image={도커 이미지} --replicas={개수} kubectl create deployment myapp --image=httpd --replicas=3
```

명령어 yaml 포맷으로 확인하기
```bash
kubectl run {이름} --image={도커 이미지} --port {포트} --dry-run -o yaml kubectl run webserver --image=nginx:1.14 --port 80 --dry-run -o yaml kubectl run webserver --image=nginx:1.14 --port 80 --dry-run -o yaml > webserver-pod.yaml
```

실행중인 pod 각각의 형태로 상태검사
```bash
kubectl get pods -o wide
kubectl get pods -o json
kubectl get pods -o yaml
```

namespace 생성
```bash
kubectl create namespace {이름}
kubectl create namespace myapp-ns
```

namespace 관리
```bash
kubectl get namespace {이름}
kubectl delete namespace {이름}
```

베이스(디폴트) 네임스페이스 설정
```bash
kubectl config get-contexts
kubectl config current-context
kubectl config use-context {사용할 컨텍스트} kubectl config set-context <context-name> --cluster=<cluster-name> --user=<user-name> --namespace=<namespace>
```

==🔴네임스페이스 지우면 해당 api들이 전부 삭제됨!==

실사간 pods 확인
```bash
kubectl get pods -o wide --watch
kubectl get pods --all-namespace

watch kubectl get pods -o wide
```

스케일 업 다운 (edit, scale)
```bash
# 파드를 줄일 때는 가장 최근에 싫행된 것부터 죽임
kubectl edit rc rc-nginx
kubectl scale rc rc-nginx --replicas=2
```


```bash
# Replicaset을 지울때 파드는 그대로 두고 지우는 경우 
kubectl delete rs rs-nginx --cascade=false
```

---

#개발언어 #쿠버네티스