
> [!NOTE] 🔒UFW 
> iptable 을 기반으로 만들어진 방화벽 소프트웨어. 
> 명령어 문법이 간결하고 iptables 에 비해서 훨씬 사용자 친화적이다.
###### UFW 실행
``` bash
su - 
apt-get install ufw -y 
ufw status verbose 
ufw enable 
ufw default deny 
ufw allow 4242 
ufw status verbose
```
###### 포트 차단
> `sudo ufw deny 8080`
###### 포트 삭제
1. 삭제하려는 포트의 번호 확인하기
	`sudo ufw status numbered`
2. 해당번호 삭제하기		
	`sudo ufw delete 3`

###### 다양한 명령어
>`apt install ufw` ㅡ UFW 설치 여부 확인하고 없으면 설치.  
>`ufw **enable/disable**` ㅡ 방화벽의 활성화/비활성화.  
`ufw **status verbose**` ㅡ 방화벽의 활성화 및 설정 상태 확인  
`ufw **default deny**` ㅡ 모든 종류의 ( 입력 + 접속자 유형) 트래픽을 차단함. 필요한 포트만 열기 위함.  
`ufw **allow** 4242` ㅡ 4242 포트를 통한 모든 종류의 접근을 허용함  
`ufw **delete allow** 4242` ㅡ 접근 허용 정책을 삭제함  
`ufw **allow** [in|out] [포트/프로토콜] from [ip]` ※ 특정 포트에 특정한 접근을 ( 입력|출력, /유형) 허용함  
`ufw **deny** [in|out] [포트/프로토콜] from [ip]` ※ 특정 포트에 특정한 접근을 ( 입력|출력, /유형) 허용함  
`systemctl status ufw` ㅡ 방화벽이 활성화되어있는지 확인  
`systemctl list-unit-files` ㅡ 부팅시 시작 프로그램 목록에 UFW가 있는지 확인