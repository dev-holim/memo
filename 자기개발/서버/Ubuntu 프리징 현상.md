인텔 시스템칩 SoC를 사용하는 컴퓨터에서 리눅스 운영체제를 사용할 때 리눅스와 인텔의 하드웨어 호환성 문제.


🚀 해결방법
1. `sudo gedit /etc/default/grub` 명령어로 `grub` 파일 오픈
2. `GRUB_CMDLINE_LINUX_DEFAULT='기존 파라미터'` -> `GRUB_CMDLINE_LINUX_DEFAULT='intel_idle.max_cstate=1'`로 수정
3. `update-grub` 으로 reboot