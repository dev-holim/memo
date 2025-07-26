```
docker run -it -d -p 3000:3000 --name erp-be 242945818639.dkr.ecr.ap-northeast-2.amazonaws.com/erp:fe.stage
```


docker build -t ljy_web .

docker run -it -d -p 9000:9000 --name ljy_web ljy_web