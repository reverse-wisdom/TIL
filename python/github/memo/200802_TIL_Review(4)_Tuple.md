> # **tuple 응용하기**

- 튜플은 리스트와 달리 내용을 변경할 수 없음(**불변:immutable**) 따라서 내용을 변경하는 **append** 같은 메서드는 사용불가, 요소의 정보를 구하는 메서드만 사용가능

  > ### **튜플에서 특정값의 인덱스 구하기**

  - #### **index**

    **index(값)**은 튜플에서 특정 값의 인덱스를 구합니다. 이때 같은 값이 여러개일 경우 처음 찾은 인덱스를 구합니다.(가장 작은 인덱스)

    ```python
    a = (38, 21, 53, 62, 19, 53)
    print(a.index(53))
    
    #실행결과
    2
    
    ```

  - #### **count**

    **count(값)**은 튜플에서 특정값의 개수를 구합니다. 

    ```python
    a = (10, 20, 30, 40, 50, 20)
    print(a.count(20))
    
    #실행결과
    2
    ```

    

  - #### **for반복문으로 요소 출력하기**

    ```python
    a = (38, 21, 53, 62, 19)
    for i in a
    	print(i, end = '')
        
    #실행결과
    38 21 53 62 19
    ```

    

  - #### **튜플 표현식 사용하기**

    ```python
    a = tuple(i for i in rage(10) if i % 2 == 0)
    print(a)
    
    #실행결과
    (0, 2, 4, 6, 8)
    ```

  - #### **tuple에 map사용하기**

    ```python
    a = (1.2, 3.5, 4.4, 8,3)
    a = tuple(map(int, a))
    print(a)
    
    #실행결과
    (1, 3, 4, 8, 3)
    ```

    

  - #### **튜플에서 가장 작은 수, 가장 큰 수, 합계구하기**

    ```python
    a =[1, 2, 3, 4, 5]
    b = range(6)
    c = (1, 2, 3, 4, 5)
    d= 'apple'
    
    print(max(a))
    print(max(b))
    print(max(c))
    
    print(max(d))
    
    print(min(a))
    print(min(b))
    print(min(c))
    print(min(d))
    #실행결과
    5
    5
    5
    1
    0
    1
    
    ```

    ★ min, max : 반복가능한 객체에서 사용가능 

