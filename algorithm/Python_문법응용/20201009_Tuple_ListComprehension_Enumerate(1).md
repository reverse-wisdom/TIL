> ### 2020.10.09
>
> ### Python  문법 -  튜플, 리스트 컴프리헨션, enumerate 응용



```python
#1 20 10 30
#2 10 20 60
#3 80 25 79
#4 30 50 80
#5 80 25 81
-> 대소관계가 같은 배열 확인하고 싶을때
```



```python
for i in range(M):
    li = [(b, a) for a, b in enumerate(map(int, input().split()))]
    uni_list = sorted(li)
```

```py
#출력결과
[(20, 0), (10, 1), (30, 2)]
[(10, 0), (20, 1), (60, 2)]
[(80, 0), (25, 1), (79, 2)]
[(30, 0), (50, 1), (80, 2)]
[(80, 0), (25, 1), (81, 2)]
```

```python
uni_list = sorted(li)
```

```py
#출력결과
[(10, 1), (20, 0), (30, 2)]
[(10, 0), (20, 1), (60, 2)]
[(25, 1), (79, 2), (80, 0)]
[(30, 0), (50, 1), (80, 2)]
[(25, 1), (80, 0), (81, 2)]
```

```python
#요약
for i in range(M):
    li = [(b, a) for a, b in enumerate(map(int, input().split()))]
    # enumerate (인덱스, 값) 으로 출력되서 뒤에 값 정렬을 위해, a랑 b 위치 바꿈
    uni_list = sorted(li) #정렬하면 b기준(인덱스 0 기준으로 정렬됨)
    print(li)    
    
```

