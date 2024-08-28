##### signal()
> `{C}void (*)(int) signal(int sig, void (*handler)(int));` 

>시그널 처리 방법을 설정
> sig는 처리해줄 시그널 번호로 *매크로* 중 하나여야 하며 signal.h 포함 파일에 정의
> 	매크로 : SIGABRT, SIGALL, SIGILL, SIGINT, SIGFPE, SIGIO, SIGOTHER, SIGSEGV, SIGTERM, SIGUSR1 또는 SIGUSR2
> * handler는 시그널을 처리해줄 핸들러 SIG_IGN을 인자로 넘겨주면 해당 시그널을 무시
> 함수 포인터를 넘겨주면 시그널일 들어왔을 때 특정 함수를 호출
##### SIGUSR1, SIGUSR2
>사용자 애플리케이션용 (ANSI로 연장)
##### getpid()
>`{C}pid_t getpid(void)`

>현재 프로세스의 아이디를 리턴
>아이디는 모든 프로세스가 고유한 값을 가지기 때문에 임시 파일명을 지을 때 좋음
>getpid와 getppid는 무조건 성공하기 때문에 실패 시 반환값 X
>	프로그램을 구동한다는 건 반드시 개별적인 프로세스가 동작하는 것과 같음
>	해당 함수를 불러오는 시점에서 프로세스 아이디는 무조건 존재
##### sleep()
>`{C}unsigned int sleep(unsigned int seconds);

>seconds 초만큼 스레드를 일시정지함 (대기 상태)
> 만약 sleep 중간에 시그널이 발생하면 바로 복귀 후 남은 시간이 반환 됨
> 만약 15초를 쉬는 중에 (seconds = 15) 5초만에 시그널이 발생하여 복귀하였을 경우, 리턴값은 10
##### usleep()
>`{C}int usleep(useconds_t microseconds);

> microseconds 마이크로초만큼 스레드를 일시 정지함
> 나머지는 sleep과 동일
##### pause()
>`{C}int pause(void);`

>kill() 함수나 내부 타이머에 의해 시그널을 받기 전까지 현재 스레드를 잠시 일시정지 시킴
>pause()를 통해 스레드가 일시정지된 상태에서 시그널 처리기 (signal handler)가 멈출 겨