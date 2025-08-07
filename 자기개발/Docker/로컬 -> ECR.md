```bash
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com
```

```bash
docker buildx build --platform linux/amd64 --build-arg API_URL="https://homepage-api.telepix.kr" -t homepage-fe .
 
docker buildx build --platform linux/amd64 -t media-scrapper .

docker build -t media-scrapper .
```

```bash
docker tag media-scrapper:latest 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-v1.0.2

docker tag sso:be 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/sso:be
```

```bash
docker push 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-v1.0.2
```

```bash
docker run -d -p 8090:8000 --name scrapper media-scrapper

kubectl exec -it media-scrapper-deployment-55b6d89bb5-snwsx -n cron -- bash
```



docker tag homepage-fe:latest 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/homepage:fe.stage.2018daf

docker push 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/homepage:fe.stage.2018daf