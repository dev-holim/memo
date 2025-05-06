```bash
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com
```

```bash
docker buildx build --platform linux/amd64 -t media-scrapper .

docker build -t media-scrapper .
```

```bash
docker tag media-scrapper:latest 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-OuAqF4VQQIfA
```

```bash
docker push 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-OuAqF4VQQIfA
```









```bash
docker run -d -p 8090:8000 --name scrapper media-scrapper

kubectl exec -it media-scrapper-deployment-55b6d89bb5-snwsx -n cron -- bash
```
