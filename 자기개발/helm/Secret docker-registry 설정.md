

```bash
kubectl create secret docker-registry ecr-sso-credential \
  --docker-server=242945818639.dkr.ecr.ap-northeast-2.amazonaws.com \
  --docker-username=AWS \
  --docker-password=$(aws ecr get-login-password --region ap-northeast-2) \
  --namespace=sso
```



```bash
kubectl create secret docker-registry ecr-erp-credential \
  --docker-server=242945818639.dkr.ecr.ap-northeast-2.amazonaws.com \
  --docker-username=AWS \
  --docker-password=$(aws ecr get-login-password --region ap-northeast-2) \
  --namespace=erp
```