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