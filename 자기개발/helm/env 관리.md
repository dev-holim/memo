```bash
kubectl create secret generic erp-be-env --from-env-file=.env -n erp --dry-run=client -o yaml > erp-be-env-secret.yaml
kubectl apply -f erp-be-env-secret.yaml
```

kubectl create secret generic homepage-fe-env --from-env-file=.env -n homepage --dry-run=client -o yaml > homepage-fe-env-secret.yaml

kubectl create secret generic sso-env --from-env-file=.env -n sso --dry-run=client -o yaml > sso-env-secret.yaml
kubectl apply -f sso-env-secret.yaml


kubectl create secret generic erp-fe-env --from-env-file=.env -n erp --dry-run=client -o yaml > erp-fe-env-secret.yaml
kubectl apply -f erp-fe-env-secret.yaml



kubectl create secret generic reten-fe-env --from-env-file=.env -n reten --dry-run=client -o yaml > reten-fe-env-secret.yaml
kubectl apply -f reten-fe-env-secret.yaml