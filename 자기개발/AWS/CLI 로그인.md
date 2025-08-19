
#### 현재 로그인 확인
```
aws sts get-caller-identity
```

#### 다중 로그인 관리
1. .aws/config 추가
```bash
[profile telepix]
sso_start_url = https://d-9b677985b7.awsapps.com/start
sso_region = ap-northeast-2
sso_account_id = 242945818639
sso_role_name = AdministratorAccess
region = ap-northeast-2
output = json
```
2. 로그인
```bash
aws sso login --profile telepix
```

#### ECR 로그인
```bash
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com
  
```