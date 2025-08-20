```bash
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com
```

```bash
docker buildx build --platform linux/amd64 --build-arg API_URL="https://homepage-api.telepix.kr" -t homepage-fe .
 
docker buildx build --platform linux/amd64 -t media-scrapper .

docker build -t media-scrapper .
```

- scrapper
```bash
docker buildx build --platform linux/amd64 -t media-scrapper .

docker tag media-scrapper:latest 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-v1.0.6

docker push 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-v1.0.6
```


```bash
docker run -d -p 8090:8000 --name scrapper media-scrapper

kubectl exec -it media-scrapper-deployment-55b6d89bb5-snwsx -n cron -- bash
```





```
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 801541932050.dkr.ecr.ap-northeast-2.amazonaws.com
```


```
docker buildx build --platform linux/amd64 -t reten .
```

```
docker tag reten:latest 801541932050.dkr.ecr.ap-northeast-2.amazonaws.com/reten:1.0.0


docker push 801541932050.dkr.ecr.ap-northeast-2.amazonaws.com/reten:1.0.0
```