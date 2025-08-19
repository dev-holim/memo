
[[CLI 로그인]]
```
[profile 3d-viewer]
sso_start_url = https://d-9b677985b7.awsapps.com/start
sso_region = ap-northeast-2
sso_account_id = 801541932050
sso_role_name = AdministratorAccess
region = ap-northeast-2
output = json
```


```
aws eks update-kubeconfig \
  --region ap-northeast-2 \
  --name reten-eks \
  --profile 3d-viewer \
  --alias reten-eks
```
