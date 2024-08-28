```C title:'signal()'
`void (*)(int) signal(int sig, void (*handler)(int));` 
```
>시그널 처리 방법을 설정
> sig는 처리해줄 시그널 번호로서 매크로 중 하나여야 하며, signal.h 포함 파일에 정의
> * handler는 시그널을 처리해줄 핸들러 SIG_IGN을 인자로 넘겨주면 해다