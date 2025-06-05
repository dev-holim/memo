```bash
docker run -it --rm --runtime=nvidia --gpus all nvidia/cuda:12.8.1-base-ubuntu24.04 bash
```

```bash
apt update
apt install -y nvidia-utils-550
nvidia-smi
```


```bash

docker build --no-cache -t whisper-transcribe .

docker run --rm --runtime=nvidia --gpus all \
-v $(pwd)/assets:/app/assets \
-v $(pwd)/txt:/app/assets/txt \
whisper-transcribe
```

