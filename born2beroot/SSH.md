
> [!NOTE] SSH (Secure Shell)
>  네트워크를 통해 다른 컴퓨터에 안전하게 접속하고 명령을 실행할 수 있게 해주는 프로토콜입니다. 주로 원격 시스템 관리 및 파일 전송을 위해 사용됩니다. SSH는 보안이 강화된 통신 채널을 제공하여 데이터의 무결성과 기밀성을 보장합니다.
### SSH를 사용하면 좋은 점
> SSH는 네트워크 보안과 관리 효율성을 크게 향상시키는 도구입니다. 안전한 데이터 전송, 원격 시스템 관리, 파일 전송 및 자동화 기능을 제공하여 다양한 환경에서 매우 유용하게 사용됩니다. 

```bash
su -
apt install openssh-server 
vim /etc/ssh/sshd_config
systemctl restart ssh
systemctl status ssh
```
### vim에 들어가서 설정
>Port 22 -> Port 4242로 변경
>PermitRootLogin prohibit-password -> PermitRootLogin no 로 변경