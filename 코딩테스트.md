```python title:리스트에서_가장_많은_인자_찾기
from collections import Counter
# 예시 정수형 리스트
tangerine = [4, 7, 3, 7, 2, 7, 4, 3, 3, 3]
# 리스트 내 각 정수의 빈도 계산
count = Counter(tangerine)
# 가장 많이 나타나는 정수들의 빈도 구하기
most_common_counts = count.most_common()
print(most_common_counts)
```
```python title:출력결과
[(3, 4), (7, 3), (4, 2), (2, 1)]
```
> most_common_counts[0]는 (3, 4)로, 숫자 3이 리스트에 4번 등장했다는 의미입니다.
> most_common_counts[1]는 (7, 3)로, 숫자 7이 리스트에 3번 등장했다는 의미입니다.
> most_common_counts[2]는 (4, 2)로, 숫자 4가 리스트에 2번 등장했다는 의미입니다.
>  most_common_counts[3]는 (2, 1)로, 숫자 2가 리스트에 1번 등장했다는 의미입니다.