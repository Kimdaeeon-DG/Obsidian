##### Counter 함수
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
> most_common_counts[0]는 (3, 4)로, 숫자 3이 리스트에 4번 등장했다는 의미.
> most_common_counts[1]는 (7, 3)
> most_common_counts[2]는 (4, 2) 
>  most_common_counts[3]는 (2, 1)
##### all() 함수
> 하나라도 거짓이면 False, 모두 참인 경우만 True를 출력함

```python title:예시
numbers = [1, 2, 3, 4, 5]
result = all(x > 0 for x in numbers)  # 모든 요소가 0보다 큰지 확인
print(result)
```
##### dictionary
> 값의 쌍으로 데이터를 저장하는 자료형을 나타냄
> 빠른 조회와 업데이트가 가능한 해시 테이블 기반의 자료 구조
```python
my_dict = {}
```
```python
my_dict = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
	}
print(my_dict["name"])  # 출력: Alice
```



