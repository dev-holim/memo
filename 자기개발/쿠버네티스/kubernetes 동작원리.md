마스터 컴포넌트
1. etcd
   - key-value 타입 저장소
2. kube-scheduler
   - 파드를 실행할 노드 선택
3. kube-controller-manager
   - 파드를 관찰하며 개수를 보장

워커노드 컴포넌트
1. kubelet
   - 모든 노드에서 실행되는 k8s 에이전트
   - 데몬 형태로 동작
2. kube-proxy
   - k8s의 network 동작을 관리
   - iptables rule을 구성
3. 컨테이너 런타임
   - 컨테이너를 실행하는 엔진
   - docker, containerd, runc

![[image 1.png]]

---

#개발언어 #쿠버네티스