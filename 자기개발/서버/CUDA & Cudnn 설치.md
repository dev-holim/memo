```bash
nvidia-smi
```
### CUDA 설치

1. OS, GPU 확인
```bash
cat /etc/os-release
lspci | grep -i NVIDIA
```

2. 시스템 업데이트
```bash
sudo apt update
sudo apt upgrade -y
```

3. 추천 driver 확인
```bash
sudo ubuntu-drivers devices
```
![[image 8.png]]


4. ndivia driver 설치
```bash
sudo apt install nvidia-driver-550

sudo reboot
```

5. gcc 설치
```bash
sudo apt install gcc
```

6. CUDA 설치
```
sudo wget https://developer.download.nvidia.com/compute/cuda/12.9.0/local_installers/cuda_12.9.0_575.51.03_linux.run

sudo sh cuda_12.9.0_575.51.03_linux.run
```

7. 아래 상태가 나오면 **Continue**로 진행
![[image 9.png]]

8. **accept** 입력
![[image 10.png]]

9. Driver 해제 후 install
![[image 11.png]]

10. 설치 완료
![[image 12.png]]

11.  .bashrc 하단에 아래 추가
```.bashrc
export PATH=/usr/local/cuda-12.9/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-12.9/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

```bash
source ~/.bashrc
```

12. conf 변경
```bash
sudo nano /etc/ld.so.conf
```

```bash
# 하단에 추가
/usr/local/cuda-12.9/lib64
```
![[image 13.png]]

13. 확인
```bash
sudo ldconfig -p | grep cuda

nvcc --version
```


### Cudnn 설치

1. [설치 사이트 접속](https://developer.nvidia.com/rdp/cudnn-archive)
![[image 14.png]]
2. 압축 해제 및 복사
```bash
tar -xvf cudnn-linux-x86_64-8.9.7.29_cuda12-archive.tar.xz
```

```bash
cd cudnn-linux-x86_64-8.9.7.29_cuda12-archive

# 복사
sudo cp include/cudnn*.h /usr/local/cuda-12.8/include
sudo cp lib/libcudnn* /usr/local/cuda-12.8/lib64
sudo chmod a+r /usr/local/cuda-12.8/include/cudnn*.h /usr/local/cuda-12.8/lib64/libcudnn*
```

3. cudnn 테스트
```bash
nano test_cudnn.c
```

```c
// test_cudnn.c
#include <cudnn.h>
#include <stdio.h>

int main() {
    cudnnHandle_t handle;
    cudnnStatus_t status = cudnnCreate(&handle);
    if (status == CUDNN_STATUS_SUCCESS) {
        printf("cuDNN successfully initialized.\n");
    } else {
        printf("cuDNN initialization failed.\n");
    }
    cudnnDestroy(handle);
    return 0;
}
```

```bash
gcc -o test_cudnn test_cudnn.c -I/usr/local/cuda-12.8/include -L/usr/local/cuda-12.8/lib64 -lcudnn
```

```bash
./test_cudnn
```