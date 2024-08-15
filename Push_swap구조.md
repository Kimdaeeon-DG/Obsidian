#### 1. 자료구조 만들기
```C
typedef struct s_node
{
	int				data;
	struct s_node	*prev;
	struct s_node	*next;
}	t_node;

typedef struct s_deque
{
	int		size;
	t_node	*top;
	t_node	*bottom;
}	t_deque;
```
#### 2. 인자 확인 후 문제 없으면 길이 반환
```C
nums_len = check_args(ac, av);

```
#### 3. 배열에 인자들 담기
1