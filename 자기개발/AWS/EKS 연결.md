
[[CLI 로그인]]
```
[profile reten]
sso_start_url = https://d-9b677985b7.awsapps.com/start
sso_region = ap-northeast-2
sso_account_id = 801541932050
sso_role_name = AdministratorAccess
region = ap-northeast-2
output = json
```


#### 텔레픽스
```
aws eks update-kubeconfig --region ap-northeast-2 --name telepix-eks --profile telepix --alias telepix-eks
```

#### 리텐
```
aws eks update-kubeconfig --region ap-northeast-2 --name reten-eks --profile reten --alias reten-eks
```

#### 리텐 US
```
aws eks update-kubeconfig --region us-east-2 --name reten-eks-us --profile reten-us --alias reten-us-eks
```

#### 이종연
```
aws eks update-kubeconfig --region ap-northeast-2 --name ljy-eks --profile ljy --alias ljy-eks
```