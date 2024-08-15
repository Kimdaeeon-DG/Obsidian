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
```C
array = get_nums(nums_len, av);
```
#### 4. 중복성 확인하기
```C
check_duplication(array, nums_len);
```
#### 5. 정렬이 되어 있으면 메모리 해제 후 종료
```C
if (is_sorted(array, nums_len))
	ft_free(array, sorted, 0);
```
#### 6. 인덱싱 작업을 위한 정렬이 된 배열 만들기
```C
sorted = copy_sorted(array, nums_len);
```
#### 7. 길이가 2면 따로 처리 
```C
if (nums_len >= 2)
	sort2(array, sorted);
```
#### 8. 