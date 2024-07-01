- ##### _**sa** : (`swap a`) - Swap the first 2 elements at the top of stack a.  
    **sa** : (`swap a`) - 스택 a의 맨 위에 위치한 두 개의 원소의 순서를 맞바꿉니다.  
    스택 a가 비어 있거나 원소가 1개만 있을 때는 아무 동작도 하지 않습니다.
- ##### _**sb** : (`swap b`) - Swap the first 2 elements at the top of stack b.  
    **sb** : (`swap b`) - 스택 b의 맨 위에 위치한 두 개의 원소의 순서를 맞바꿉니다.  
    스택 b가 비어 있거나 원소가 1개만 있을 때는 아무 동작도 하지 않습니다.
- ##### _**ss** : `sa` and `sb` at the same time._
    **ss** : `sa`와 `sb`를 동시에 수행합니다.
- ##### _**pa** : (`push a`) - Take the first element at the top of b and put it at the top of a.  
    **pa** : (`push a`) - 스택 b의 맨 위에 위치한 원소 한 개를 스택 a의 맨 위로 옮깁니다.  
    스택 b가 비어 있을 경우에는 아무 동작도 하지 않습니다.
- ##### _**pb** : (`push b`)- Take the first element at the top of a and put it at the top of b.  
    **pb** : (`push b`) - 스택 a의 맨 위에 위치한 원소 한 개를 스택 b의 맨 위로 옮깁니다.  
    스택 a가 비어 있을 경우에는 아무 동작도 하지 않습니다.
- ##### _**ra** : (`rotate a`) - Shift up all elements of stack a by 1.  
    **ra** : (`rotate a`) - 스택 a의 원소를 한 칸씩 위로 옮깁니다.  
    스택의 첫 번째 원소는 맨 마지막 원소가 됩니다.
- ##### _**rb** : (`rotate b`)- Shift up all elements of stack b by 1.  
    **rb** : (`rotate b`) - 스택 b의 원소를 한 칸씩 위로 옮깁니다.  
    스택의 첫 번째 원소는 맨 마지막 원소가 됩니다.
- ##### _**rr** : `ra` and `rb` at the same time._
    **rr** : `ra`와 `rb`를 동시에 수행합니다.
- ##### _**rra** : (`reverse rotate a`) - Shift down all elements of stack a by 1.  
    **rra** : (`reverse rotate a`) - 스택 a의 원소를 한 칸씩 아래로 옮깁니다.  
    스택의 마지막 원소는 맨 첫 번째 원소가 됩니다.
- ##### _**rrb** : (`reverse rotate b`) - Shift down all elements of stack b by 1.  
    **rrb** : (`reverse rotate b`) - 스택 b의 원소를 한 칸씩 아래로 옮깁니다.  
    스택의 마지막 원소는 맨 첫 번째 원소가 됩니다.
- ##### _rrr : `rra` and `rrb` at the same time._
    **rrr** : `rra`와 `rrb`를 동시에 수행합니다.