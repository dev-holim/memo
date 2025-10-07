
목적: 10.0.10.220:30007 엔드포인트의 DB 테이블(읽기, 쓰기, 수정)과 10.0.10.102:13000 엔드포인트의 DB 테이블(읽기)을 동일한 내부 테이블로 사용



퍼블리셔(읽기, 쓰기, 수정)와 서브스크라이버(읽기)로 구성


1. 현재 실행 중인 서버에서 확인
```sql
SHOW config_file;   -- postgresql.conf 파일 경로
SHOW hba_file;      -- pg_hba.conf 파일 경로
```

2. pg_hba.conf 파일 수정
```
# 퍼블리셔(10.0.10.220) 서버의 pg_hba.conf
host    replication   replicator   10.0.10.102/32   md5
host    appdb         replicator   10.0.10.102/32   md5
```