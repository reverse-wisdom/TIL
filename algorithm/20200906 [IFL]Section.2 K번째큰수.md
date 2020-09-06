> ## [IFL]Section.2 K번째 큰수

```python
N, K = map(int, input().split())
arr = list(map(int, input().split()))
total = set() # 합계가 같을수 있으므로 set 자료형에 담기

for i in range(N):#첫번째
    for j in range(i+1,N): #두번째수
        for m in range(j+1,N): #세번째수
            total.add(arr[i]+arr[j]+arr[m]) #세개 더한거 set에 포함
total = list(total) #set은 순서가 없음, 그래서 list로 다시변환
total.sort(reverse=True) #큰수를 찾아야하므로 내림차순으로 정렬
print(total[K-1])#인덱스는 -1


```

