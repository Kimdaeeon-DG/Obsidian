##### signal()
`C title:'signal()'
`void (*)(int) signal(int sig, void (*handler)(int));` 
```
>시그널 처리 방법을 설정
> sig는 처리해줄 시그널 번호로 *매크로* 중 하나여야 하며 signal.h 포함 파일에 정의
> 	매크로 : SIGABRT, SIGALL, SIGILL, SIGINT, SIGFPE, SIGIO, SIGOTHER, SIGSEGV, SIGTERM, SIGUSR1 또는 SIGUSR2
> * handler는 시그널을 처리해줄 핸들러 SIG_IGN을 인자로 넘겨주면 해당 시그널을 무시
> 함수 포인터를 넘겨주면 시그널일 들어왔을 때 특정 함수를 호출

##### SIGUSR1, SIGUSR2
>사용자 애플리케이션용 (ANSI로 연장)

##### getpid()
>`{C}pid_t getpid(void)`