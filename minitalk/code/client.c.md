```C title:client
#include "../minitalk.h"

void	send_sig(unsigned char s, int server_pid)
{
	int	i;

	i = 8;
	while (--i >= 0) // 비트가 8개 쌓였으면
	{
		if (s & (1 << i)) // 1 전송
			kill(server_pid, SIGUSR1);
		else // 2 전송
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
			ft_putstr("Error: Invalid PID.\n"); // 에러 출력
			return (1); // 끝
		}
		server_pid = ft_atoi(argv[1]); // 문자를 숫자로 바꿔줌
		if (server_pid <= 0)
		{
			ft_putstr("Error: Invalid PID.\n");
			return (1);
		}
		i = -1;
		while (argv[2][++i])
			send_sig((unsigned char)argv[2][i], server_pid);
	}
	return (0);
}
```