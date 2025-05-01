```
sudo docker run --rm --gpus all nvidia/cuda:12.8.1-base-ubuntu24.04 nvidia-smi
```

- --rm: 컨테이너가 종료되면 해당 컨테이너를 자동으로 제거
- --gpus all: 호스트 시스템의 모든 GPU를 컨테이너와 공유, NVIDIA GPU 드라이버 및 [[NVIDIA Container Toolkit 설치]]이 호스트 시스템에 설치되어 있어야 함
- nvidia/cuda:12.8.1-base-ubuntu24.04: 실행할 Docker 이미지의 이름과 태그, NVIDIA GPU를 지원하며 CUDA 도구를 포함하고 있음. ([도커 태그 버전 확인](https://hub.docker.com/r/nvidia/cuda))
- nvidia-smi: 컨테이너 내에서 실행할 명령어. nvidia-smi는 NVIDIA GPU의 상태를 보고하는 도구로, GPU 정보, 메모리 사용량, 프로세스 정보 등을 표시