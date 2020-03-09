## K번째 수 

https://programmers.co.kr/learn/courses/30/lessons/42748

##### 통과 코드

```python
def solution(array, commands):
    return [sorted(array[i[0]-1:i[1]])[i[2] -1] for i in commands]
```