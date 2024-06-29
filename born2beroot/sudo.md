###### sudo 설치 확인
> `sudo --version`

###### sudo 규칙 설정
> `visudo`

### visudo
```bash
Defaults authfail_message="권한 획득 실패 메세지" 
Defaults badpass_message="비밀번호 틀릴때 메세지" 
Defaults iolog_dir="/var/log/sudo/" 
Defaults log_input Defaults log_output 
Defaults requiretty 
Defaults passwd_tries=3
```

###### tty
