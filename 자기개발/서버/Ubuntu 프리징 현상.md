인텔 시스템칩 SoC를 사용하는 컴퓨터에서 리눅스 운영체제를 사용할 때 리눅스와 인텔의 하드웨어 호환성 문제.


🚀 해결방법 1
1. `sudo gedit /etc/default/grub` 명령어로 `grub` 파일 오픈
2. `GRUB_CMDLINE_LINUX_DEFAULT='기존 파라미터'` -> `GRUB_CMDLINE_LINUX_DEFAULT='intel_idle.max_cstate=1'`로 수정
3. `update-grub` 으로 reboot

🚀 해결방법 2
1. `sudo nano /etc/default/grub` 명령어로 `grub` 파일 오픈
2. nomodeset추가
```bash
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash nomodeset" # nomodeset추가
```
![[image 6.png]]

3. `Software & Update` 를 실행해서 `Additional Drivers` (또는 `추가 드라이버`) 탭에 들어가면 본인 컴퓨터에서 사용할 수 있는 드라이버 목록이 나온다. 기본적으로는 Nouveau display driver 어쩌구가 선택되어 있을텐데 맨 위에 이미 **검증된(tested) 안전한 드라이버**를 선택
![[image 7.png]]

4. `Appply change`하고 컴퓨터를 재부팅
5. 해상도가 바뀌어있을테니 오른쪽 클릭해서 Display setting으로 들어가서 해상도 변경