
현재 aws 적용 로그
```bash
watch -n 0.5  kubectl logs -n kube-system -l app.kubernetes.io/name=aws-load-balancer-controller
```


```
kubectl get secret homepage-be-env -n homepage -o jsonpath='{.data.DB_PORT}' | base64 -d 
```


kubectl get secret erp-be-env -n erp -o jsonpath='{.data.JWT_ALGORITHM}' | base64 -d