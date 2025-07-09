```bash
kubectl create secret generic erp-be-env --from-env-file=.env -n erp --dry-run=client -o yaml > erp-be-env-secret.yaml
kubectl apply -f erp-be-env-secret.yaml
```


