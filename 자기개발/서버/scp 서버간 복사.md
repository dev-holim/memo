```sh
#!/bin/bash

# scp.sh

# SCP 로그인 정보
USER="osangu"
PASSWORD="o.sangu.dev"
REMOTE_HOST="10.0.30.198"
REMOTE_DIR="/mnt/ssd_new/purchase_platform/satellite-images/cog/"

# 현재 디렉토리 내에서 sentinel-2_ 또는 sentinel_으로 시작하는 디렉토리 목록 가져오기
DIRECTORIES=$(ls -d sentinel-2_* sentinel_*)
# 각 디렉토리를 원격 서버로 전송
for DIR in $DIRECTORIES; do
  echo "Transferring $DIR to $REMOTE_HOST:$REMOTE_DIR"

  sshpass -p "$PASSWORD" scp -r "./$DIR" "$USER@$REMOTE_HOST:$REMOTE_DIR"

done

echo "All specified directories transferred."
```