
인코딩하여 저장해줌
```bash
kubectl create secret generic sso-env --from-env-file=.env -n sso --dry-run=client -o yaml > sso-env-secret.yaml

kubectl apply -f sso-env-secret.yaml
```