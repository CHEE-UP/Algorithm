## N-Queen

N-Queen문제를 풀어보려했지만 실패했다...너무어려운것 아닙니까. 어제 dfs 알고리즘 개념 이해해서 백트래킹 해보고싶다! 했는데 어떻게 풀지 감도 안오고, 코드를 봤음에도 이해를 할 수 없었다 😭핵좌절 

그래도 푸는 원리는 남기고 싶어서 작성 

##### 원리

n-queen 문제는 체스의 여왕을 어떻게 배치하는가의 문제이다. 퀸은 (상하좌우/대각선)이 다 갈수있다. n*n의 체스판에 n개의 여왕을 배치할 경우, 서로 공격할 수 없는 조건으로 배치하는 경우의수는 몇인가? 를 푸는 알고리즘이다. 딱 봤을때 DFS 를 생각할 수 있다. (`1x1`의 경우에는 1)



![img](https://t1.daumcdn.net/cfile/tistory/216ADD4451A1DABE2F)

이런식으로 0번째 row 에 하나씩 배치한 후, 그 옆칸에 여왕이 올수 있는 경우를 찾는다. 없다면 back tracking 을통해 다시 내려가면서 경우의 수를 찾을 수 있다.

##### 찾아본 코드

```python
def promising(i,col):
    k=0
    correct=True
    while (k<i and correct): 
        if (col[i]==col[k] or abs(col[i]-col[k])==i-k):
            correct=False
            break
        k+=1
    return correct

def queens(n,i,col,count):
    if (promising(i,col)): # queue 배치할 수 있는지 체크 
        if (i==n-1):
            count.append(col)
        else:
            for j in range(n):
                col[i+1]=j
                queens(n,i+1,col,count)

def solution(n):
    col= [0] * n  
    global count
    count=[]
    queens(n,-1,col,count)
    return len(count)
```

promissing 에서 배치가 되는지를 체크하고, 해당 값이 다 체크되면 queen 에서 한번 더 체크하여 경우의수를 더해준다. 하지만 명확히 이해하지 못했음 ㅠㅠ 오늘은 여기서 끝...나의 알고리즘 한계를 느낀다. DFS BFS 정말 어려운듯 