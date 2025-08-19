
#### 현재 로그인 확인
```bash
aws sts get-caller-identity
```

#### 다중 로그인 관리
1. .aws/config 추가
```bash
[profile {이름}]
sso_start_url = {IAM Identity Center > Settings의 url 값}
sso_region = ap-northeast-2
sso_account_id = {우측 상단 계정 account 들어가면 보이는 id}
sso_role_name = AdministratorAccess
region = ap-northeast-2
output = json
```

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

3. config 설정
```bash
aws configure sso --profile 3d-viewer
```

#### ECR 로그인
```bash
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com
  
```

