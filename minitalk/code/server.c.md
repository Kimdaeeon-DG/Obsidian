```C
#include "../minitalk.h"

void	check_interupt(siginfo_t *info, pid_t *client_pid, int *counter)
// 신호를 보낸 클라이언트의 PID를 확인
// 만약 새로운 클라이언트가 신호를 보낸 경우 현재 상태 초기화
{   
	if (info->si_pid != *client_pid) // 구조체 안에 info랑 pid랑 다르면
	{
		*client_pid = info->si_pid;
		// info->si_pid는 신호를 보낸 클라이언트의 PID
		// client_pid는 현재 처리 중인 클라이언트의 PID
		*counter = 0; // 0으로 초기화.
		// 새로운 문자를 수신하기 위한 준비과정
	}
}

void	handle_usr_signals(int SIGUSR, siginfo_t *info, void *vp)
{
	static int				counter;
	static pid_t			client_pid;
	static unsigned char	c;
	// static 쓰는 이유: 함수가 호출될 때마다 재초기화 되지 않고 값을 유지

	(void)vp; // 사용하지 않지만 적어주지 않으면 컴파일 할 때 오류 
	// 저 형식이 signal.h에 있음
	check_interupt(info, &client_pid, &counter);
	if (!counter) // 0이면 새로운 문자를 수신할 준비가 된 것
	{
		counter = 8;
		c = 0;
	}
	if (SIGUSR == SIGUSR1)
	// SIGUSR1 신호를 받으면 현재 문자의 해당 위치 비트를 1로 설정
	{
		c |= 1 << (counter - 1);
		counter--;
	}
	if (SIGUSR == SIGUSR2)
	// 현재 위치의 비트르 변경하지 않고 넘어감
		counter--;
	if (counter == 0)
	// 0이 되면 문자의 모든 비트가 수신된 것이므로 문자 출력
	{
		write(1, &c, 1);
		counter = 0; // 0으로 다시 초기화
	}
}

int	main(void)
{
	struct sigaction	sa_usrs;

	ft_putstr("PID: ");
	ft_putnbr(getpid());
	ft_putchar('\n');
	sa_usrs.sa_flags = SA_SIGINFO; // 신호 핸들러가 추가 정보를 받도록 설정
	sa_usrs.sa_sigaction = handle_usr_signals; // 신호가 발생했을 때 호출될 함수를 지정
	sigaction(SIGUSR1, &sa_usrs, NULL); 
	sigaction(SIGUSR2, &sa_usrs, NULL);
	// 신호를 처리하는 함수를 설정
	while (1)
		pause();
}
```