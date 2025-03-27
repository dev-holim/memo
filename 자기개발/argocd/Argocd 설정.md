```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}' # 서비스 타입을 NodePort로 설정
```

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}' # 서비스 타입을 로드밸런서로 설정
```

```bash
brew install argocd
```

```bash
argocd admin initial-password -n argocd

argocd login --core

kubectl exec -n argocd -it pod/argocd-server-55896669d5-hr6f6 -- /bin/bash
```

```bash
kubectl get po -n argocd
kubectl get pods -n argocd
```

```bash
kubectl get svc -n argocd
```

```bash
kubectl describe svc argocd-server -n argocd
```


```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

```bash
kubectl config set-context --current --namespace=argocd
```

---

#개발언어 #Argocd
