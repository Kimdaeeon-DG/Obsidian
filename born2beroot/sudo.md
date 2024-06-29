###### sudo 설치 확인
> `sudo --version`

###### sudo 규칙 설정
> `visudo`

### visudo
```bash
Defaults authfail_message="권한 획득 실패 메세지" 
Defaults badpass_message="비밀번호 틀릴때 메세지" 
Defaults iolog_dir="/var/log/sudo/" 
Defaults log_input 
Defaults log_output 
Defaults requiretty 
Defaults passwd_tries=3
```

###### Defaults log_input
> sudo를 사용해 명령을 실행할 때 사용자의 입력(키 입력)을 로그에 남깁니다. 즉, 사용자가 sudo를 통해 실행한 명령어를 입력하는 동안의 키보드 입력이 로깅됩니다.
###### Defaults log_output
> sudo를 통해 실행된 명령어의 출력 결과를 로그에 남깁니다. 즉, 명령어가 실행된 결과로 터미널에 출력된 내용이나 프로그램이 생성한 출력이 로깅됩니다.
###### tty
>실제 터미널 사용자만 sudo 권한을 쓸 수 있음. 
>포트포워딩 등으로 접근한 사용자는 sudo 권한 없음
>최상위 항목인 tty 뒤로 pty, pts가 있음