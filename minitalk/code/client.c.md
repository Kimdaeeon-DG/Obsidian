```C title:client
#include "../minitalk.h"

void	send_sig(unsigned char s, int server_pid)
{
	int	i;

	i = 8; // 비트가 8개 쌓였으면
	while (--i >= 0) // s의 비트를 가장 높은 위치(7)부터 검사
	{
		if (s & (1 << i)) // s의 i번째가 1인지 확인 
			kill(server_pid, SIGUSR1);
		else // 아니면 
			kill(server_pid, SIGUSR2);
		usleep(300); // 마이크로초
	}
}

int	is_valid_pid(const char *pid_str) // pid가 정수인가
{
	int	i;

	i = 0;
	while (pid_str[i])
	{
		if (!ft_isdigit(pid_str[i]))
			return (0);
		i++;
	}
	return (1);
}

int	main(int argc, char **argv)
{
	int	server_pid;
	int	i;

	if (argc == 3)
	{	
		if (!is_valid_pid(argv[1])) // pid가 정수가 아니면
		{
			ft_putstr("Error PID.\n"); // 에러 출력
			return (1); // 끝
		}
		server_pid = ft_atoi(argv[1]); // 문자를 숫자로 바꿔줌
		if (server_pid <= 0)
		{
			ft_putstr("Error PID.\n");
			return (1);
		}
		i = -1;
		while (argv[2][++i])
			send_sig((unsigned char)argv[2][i], server_pid);
	}
	return (0);
}
```