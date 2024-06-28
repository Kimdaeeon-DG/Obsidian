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