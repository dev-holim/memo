```bash
aws ecr get-login-password --region ap-northeast-2 --profile telepix | docker login --username AWS --password-stdin 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com
```

```bash
docker buildx build --platform linux/amd64 --build-arg API_URL="https://homepage-api.telepix.kr" -t homepage-fe .
 
docker buildx build --platform linux/amd64 -t media-scrapper .

docker build -t media-scrapper .
```

- scrapper
```bash
docker buildx build --platform linux/amd64 -t media-scrapper .

docker tag media-scrapper:latest 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-v1.1.3

docker push 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/scrapper:media-v1.1.3
```


```bash
docker run -d -p 8090:8000 --name scrapper media-scrapper

kubectl exec -it media-scrapper-deployment-55b6d89bb5-snwsx -n cron -- bash
```



### 리텐

```
aws ecr get-login-password --region ap-northeast-2 --profile reten | docker login --username AWS --password-stdin 801541932050.dkr.ecr.ap-northeast-2.amazonaws.com
```


```
docker buildx build --platform linux/amd64 -t reten .
```

```
docker tag reten:latest 801541932050.dkr.ecr.ap-northeast-2.amazonaws.com/reten:1.0.0


docker push 801541932050.dkr.ecr.ap-northeast-2.amazonaws.com/reten:1.0.0
```


### 이종연
```
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 396531908600.dkr.ecr.ap-northeast-2.amazonaws.com

docker pull 396531908600.dkr.ecr.ap-northeast-2.amazonaws.com/ljy:1.0.1

docker run -d -p 80:80 --name ljy --env-file .env 396531908600.dkr.ecr.ap-northeast-2.amazonaws.com/ljy:1.0.1


```


### 유포리아

```
aws ecr get-login-password --region ap-northeast-2 --profile euphoria | docker login --username AWS --password-stdin 484907526002.dkr.ecr.ap-northeast-2.amazonaws.com
```


```
docker buildx build --platform linux/amd64 -t euphoria .
```

```
docker tag euphoria:latest 484907526002.dkr.ecr.ap-northeast-2.amazonaws.com/euphoria:1.0.0


docker push 484907526002.dkr.ecr.ap-northeast-2.amazonaws.com/euphoria:1.0.0
```


```
aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin 484907526002.dkr.ecr.ap-northeast-2.amazonaws.com

docker pull 484907526002.dkr.ecr.ap-northeast-2.amazonaws.com/euphoria:{}

docker run -d --name euphoria-app -p 3000:3000 484907526002.dkr.ecr.ap-northeast-2.amazonaws.com/euphoria:{}
```