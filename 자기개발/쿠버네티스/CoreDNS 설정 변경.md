```bash
kubectl edit configmap coredns -n kube-system
```

```diff
- forward . /etc/resolv.conf {
+ forward . 8.8.8.8 8.8.4.4 {
    max_concurrent 1000
}
```

```bash
kubectl rollout restart deployment coredns -n kube-system
```