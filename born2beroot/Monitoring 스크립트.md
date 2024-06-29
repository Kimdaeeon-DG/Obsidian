### 코드 설명
> `wc -l` : 갯수를 셈
> `tr -d \n` : 개행 문자 제거
> `ip link show` : 네트워크 인터페이스 정보 출력


```bash
apt-get -y install sysstat
vi /root/monitoring.sh

아래 내용 그대로 입력. 틈틈히 저장하고 출력 확인하면서 만들 것.

printf "#Architecture: "
uname -a

printf "#CPU physical : "
nproc --all

printf "#vCPU : "
cat /proc/cpuinfo | grep processor | wc -l

printf "#Memory Usage: "
free -m | grep Mem | awk '{printf"%d/%dMB (%.2f%%)\n", $3, $2, $3/$2 * 100}'
// fre
printf "#Disk Usage: "
df -a -BM | grep /dev/map | awk '{sum+=$3}END{print sum}' | tr -d '\n'
printf "/"
df -a -BM | grep /dev/map | awk '{sum+=$4}END{print sum}' | tr -d '\n'
printf "MB ("
df -a -BM | grep /dev/map | awk '{sum1+=$3 ; sum2+=$4 }END{printf "%d", sum1 / sum2 * 100}' | tr -d '\n'
printf "%%)\n"
// 사용한 용량과 총 용량을 각각 합산하여 사용률을 백분율로 개산한 후 출력

printf "#CPU load: "
mpstat | grep all | awk '{printf "%.2f%%\n", 100-$13}'

printf "#Last boot: "
who -b | awk '{printf $3" "$4"\n"}'
// who -b는 마지막 부팅 시간을 출력함
// awk로 날짜와 시간을 추출하여 출력

printf "#LVM use: "
if [ "$(lsblk | grep lvm | wc -l)" -gt 0 ] ; then printf "yes\n" ; else printf "no\n" ; fi
// lsblk는 블록장치를 출력함
// grep lvm은 파티션을 필터링함
// wc -l로 수를 세어 lvm이 사용 중인지 확인

printf "#Connections TCP : "
ss | grep -i tcp | wc -l | tr -d '\n'
printf " ESTABLISHED\n"
// 소켓 통계를 출력함
// TCP 연결을 필터링함

printf "#User log: "
who | wc -l
// 현재 로그인한 사용자를 출력

printf "#Network: IP "
hostname -I | tr -d '\n'
// 시스템의 IP주소 출력

printf "("
ip link show | awk '$1 == "link/ether" {print $2}' | sed '2, $d' | tr -d '\n'
printf ")\n"
// 네트워크 인터페이스 정보 출력
// MAC주소 추출
// 두 번째 이후의 모든 라인 삭제
// 개행 삭제


printf "#Sudo : "
journalctl _COMM=sudo | wc -l | tr -d '\n'
printf " cmd\n"
// sudo 명령어의 로그 출력
// 횟수 세기
// 개행 문자 제거
```