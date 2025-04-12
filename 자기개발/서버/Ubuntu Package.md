```bash
sudo apt install
```

```bash
sudo apt remove
```

```bash
sudo apt purge
```


- remove
	- 패키지 삭제 및 설정파일 보존
- purge 
	- 패키지 삭제 및 설정파일 삭제


docker rmi -f crawl:latest & docker rm -f crawling

docker build -t crawl .

docker run -it -d --name crawling -v ~/workspace/crawling/downloads:/app/downloads crawl

docker exec -it crawling bash

watch -n 1 docker logs crawling