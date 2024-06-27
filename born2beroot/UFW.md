``` bash
su - 
apt-get install ufw -y 
ufw status verbose 
ufw enable 
ufw default deny 
ufw allow 4242 
ufw status verbose
```