

## **REVIEW(Private)**-(1)



> ## **True & False**

```python
#1
bool(0) =>F #0일경우
#2
bool("")=>F #빈 타입
#3
type(None)=>NoneType
#4
a = None
print(a)=>None
#5
bool(None)=>False

#6
type(True)
type(False)
=>bool

#7
a = [1, 2, 3]
b = [1, 2, 3]
print(a is b) =>false
print(id(a) == id(b)) =>false
print(a == b) => True
```

---

> ## **암시적형변환**

```python
#1
True + 3
print(int(True))
=>1
#2
check_passed = True
check_passed + 3

check_passed = True
print(check_passed + 3)

=>4

#3
int_number = 2020
float_number = 3.14
complex_number = 2 + 3j

print(int_number + float_number)
=>2023.14
print(type(int_number + complex_number))
=> complex

★# 더 범위가 큰것으로 암시적으로 형변환 됨
```



> ## 대소의 관계



``` => Tpython
3 < 6 => T
3 != 3.0 => F
3.0 == 3.0 =>T
3 == 3.0 =>T
'hello' == 'hello' =>T
```









> ## **실수의연산**

```python
#1
print(3.5 + 3.2)
=> 6.7

#2
print(3.5 - 3.2 == 0.3)
=>False

#3
print(round(3.5 - 3.2, 2) == 0.3) =>true
a = 3.141592
print(round(a, 2)) => 3.14

#4
print(3.5 - 3.2)
print(0.3)
=>
0.2999999999999998
0.3

#1
abs(a - b) <= 1E-10
#2
import sys
print(sys.float_info.epsilon)

abs(a - b) <= sys.float_info.epsilon
#3
import math
math.isclose(a, b)
```

> ## **String interpolation**

```python
name = 'an'
print('내 이름은 %s 입니다.' % name)
내 이름은 an 입니다
print('내 이름은 {} 입니다'.format(name))
내 이름은 an 입니다
print(f'내 이름은 {name}입니다')
내 이름은 an 입니다

```

```python
print(f'''
내 이름은
{name}
입니다.
''')

내 이름은
an
입니다.
```

```python
import datetime
now = datetime.datetime.now()
print(now)
=>2020-07-20 02:22:36.015179
        
now.today()
f'올해는 {now:%Y}년 이번달은 {now:%m}월 오늘은 {now:%d}일'
올해는 2020년 이번달은 07월 오늘은 20일
```

```python
pi = 3.141592
r = 10
print(f'{pi:.3} 넓이는: {pi*r*r:.3}')
=>3.14 넓이는: 3.14e+02
    
```



# int

Int(숫자, 계산식, 정수로 된 문자열만됨)





> # **float**

float(숫자, 계산식, 실수 또는 정수로된 문자열)

```py
float(5)
=>5.0
float(1+2)
=>3.0
float('5,3')
=>5.3

```



> ## **complex**

실수부와 허수부로 이루어진 복소수(complex number)도 사용할 수 있음

허수부는 `j` 를 붙인다

```python
print(1,2 + 1.3j)

#실행결과
(1.2 + 1.3j)

```



```python
complex(1.2, 1.3)

#실행결과
(1.2+1.3j)
```





> # **type**



객체의 자료형(타입)을 알아내는 함수

```python
type(10)
```



> # **divmod**

```python
#입력
quotient, remainder = divmod(5, 2)
print(quotient, remainder)
#실행결과
(2, 1)

```



> ## **2진수, 8진수, 16진수**

- 2진수: 숫자앞에 0b를 붙이며 0과 1을 사용합니다.

- 8진수: 숫자 앞에 0o(숫자 0과 소문자o)를 붙이며 0부터 7까지 사용합니다.

- 16진수: 숫자 앞에 0x 또는 0X를 붙이며 0부터 9, A부터F까지 사용합니다. (소문자 a부터 f도 가능)

  

  

> ## **실수계산하기**

- 두 실수가 같은지 판단하기

  ```python
  import math
  math.isclose(0.1+0.2,0.3)
  ```

- 실수+정수=실수

  ```python
  4.2 + 5 = 9.2
  #실수와 정수를 함께 계산하면 표현범위가 넓은 실수로 계산됨
  ```

  

> ## **객체가 같은지 다른지 비교하기**

- `is`,  `is not`은 객체를 비교합니다

  ```python
  1 == 1.0
  =>True
  
  1 is 1.0
  =>False
  
  1 is not 1.0
  =>True
  ```







> ## **List(리스트) **

- 리스트는 문자열， 정수， 실수， 불 등 모든 자료형을 저장할 수 있음, 자료형을 섞어서 저장가능

- 리스트 지정하는 방법

  ```python
  a = []
  print(a)
  => []
  b = list()
  print(b)
  => []
  ```

 **List(리스트)+ range** 

```python
#range는 기본값으로 양수1만큼증가함

print(range(10))
=>range(0,10)

a = list(range(10))
print(a)
=>[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

b = list(range(5, 12))
print(b)
=>[5, 6, 7, 8, 9, 10, 11]

c = list(range(-4, 10, 2)
print(c)        
=> [-4, -2 , 0, 2, 4, 6, 8J

d = list(range(10 , 0, -1)) 
print(d)
>>> [10 , 9, 8, 7, 6, 5, 4, 3, 2, 1]
```





> ## **tuple** (저장만됨, 변경, 추가, 삭제불가)   

- 리스트처럼 여러 자료형을 섞어서 저장해도됨

```python
#1
# 변수에 값을 저장할때()로 묶어주면 튜플이 되며 각 값은 ,(콤마)로 구분해줍니다.
# 또는 괄호로 묶지 않고 갑만 콤마로 구분해도 튜플이 됨

a = (38 , 21 , 53, 62, 19)
print(a)
=> 
(38 , 21 , 53, 62, 19)


#2
a = 38, 21, 53 , 62 , 19
print(b)
=> (38 , 21 , 53, 62 , 19)


#3
#요소가 한개인 튜플을 만들면 튜플이 아니라 그냥 값이됨
print((38))
=>38
print((38, ))
=>(38,)
print(38,)
=>(38,)

```





**tuple(튜플) + range**

- 형식:`튜플=tuple(range(횟수))`

```python
a = tuple(range(10))
print(a)
=>(0 , 1, 2, 3, 4, 5, 6, 7, 8, 9)
```



**tuple + list**

- 튜플과 리스트는 요소를 변경, 추가, 삭제할 수 있는지 없는지만 다를뿐 기능과 형태는 같습니다.

  따라서 튜플을 리스트로 만들거나 리스트를 튜플로 만들수 있음

```python
a = [1, 2, 3]
print(tuple(a))

=> (1, 2, 3)
```

```python
b = (4, 5, 6)
pritn(list(b))
=> [1, 2, 3]
```



**tuple/list + 문자열 **

```python
print(list('hello'))
print(tuple('hello'))
=>
['h', 'e', 'l', 'l', 'o']
('h', 'e', 'l', 'l', 'o')
```



**tuple/ list 와 input과 split**

```python
print(input().split())
=> 
['10’, '20']
   

```



>  ##  **시퀀스자료형**

- **리스트, 튜플, range, 문자열** 처럼 값이 연속적으로 이어진 자료형을 시퀀스 자료형이라고함

  

- 특정 값이 잇는지 확인

  ```python
  a = [1, 2, 3, 4]
  print(4 in a) =>True
  print(10 in a)=>False
  
  b= [5, 6, 7, 8]
  print(100 not in b) =>True
  print(8 not in b) =>False
  
  print(43 in (38, 43, 52)) =>True
  print(1 in rage(10)) =>True
  print('p' in 'python') =>True
  
  ```

  

- 시퀀스 객체 연결하기

- 연결: 시퀀스 객체1+ 시퀀스객체2 가능

※ range는 + 연산자로 객체연결 불가하지만 range를 리스트나 튜플로 만들어서 연결하면 가능

```python
print(list(range(0, 10)) + list(range(10,20))
print(tuple(range(0, 10)) + tuple(range(10,20))
print('hello'+'world')
```

- 반복:

```python
print(list(range(0, 5, 2))*3)
print(tuple(range(0, 5, 2))*3)
print('hello'*3)
=>
[0, 2, 4, 0, 2, 4, 0, 2, 4]
(0, 2, 4, 0, 2, 4, 0, 2, 4)
hellohellohello
```

- **요소 갯수 구하기**

  `len(a)` : 리스트, 튜플, range , 문자열 가능

  -문자열은 공백 포함해서 카운팅되고 ,묶은 따옴표는 제외

  

- **인덱스 사용하기**

  -**튜플， range, 문자열도 [ ] 에 인텍스를 지정하면 해당 요소를 가져올 수 있습니다.**

  -문자열은 인덱스 사용할 때 공백은 건너 뛰고 카운팅됨

  ```python
  hello = 'Hello , world!'
  hello = 'Hello, world!'
  print(hello[7])
  print(hello[7])
  =>
  w
  w
  ```

  



-  요소에 값 할당하기

  -시퀀스 객체는 []로 요소에 접근한뒤  = 로 값을 할당, 튜플, range, 문자열은 값 할당 불가, 읽기전용

- del로 요소 삭제하기

  -tuple, range, 문자열 튜플 요소 삭제 불가

  ```python
  a = [1, 2, 3, 4, 5]
  del a[2] #인덱스로 접근해서 삭제
  print(a)
  
  ```

  

  

- 슬라이스 사용가능: 튜플, range, 문자열

- 슬라이싱 사용해서 요소 할당하기 (튜플, range, 문자열)

  -인텍스 증가폭을 지정했을 때는 슬라이스 범위의 요소 개수와 할당할 요소 개수가 정확히 일치해야함	

- 슬라이스 사용해서 삭제

​	**※정리※**

​	**값할당은 리스트만 가능, 튜플 /range(연결불가)/ 문자열은, 인덱스로 불러오거나, 연결가능 , 삭제불가능**



>## **딕셔너리**

- `key`는 **변경 불가능(immutable)한 데이터**만 가능하다. (immutable : string, integer, float, boolean, tuple, range, frozenset)
- `value`는 `list`, `dictionary`를 포함한 모든 것이 가능하다.

- 키이름이 중복되면
  - 키가 중복되면 가장 뒤에 있는 값만 사용함
  - 중복되는 키는 저장되지 않음

- 딕셔너리 키의 자료형
  - 키로 올 수 있는 자료형: 정수, 실수, 불, 문자열 `리스트와 딕셔너리는 사용불가`
  - 값(Value): 모든 자료형 올 수 있음

- 빈 딕셔너리 만들기

  - 형식

    ```python
    딕셔너리 = {}
    딕셔너리 = dict{}
    
    #예제
    x = {}
    print(x)
    
    => {}
    y = dict()
    print(y)
    =>{}
    ```

    

  - dict로 딕셔너리 만들기

    딕셔너리 = dict(키1=값1, 키2=값2)

    딕셔너리 = dict(zip([키1, 키2]), [값1, 값2]

    딕셔너리 = dict([(키1,값1), (키2, 값2)])

    딕셔너리 = dict({키1: 값1, 키2: 값2})

    

  ```python
  x1 = dict(health=490, mana=334, melee=550, armor=18.72)
  
  #1
  lux2 = dict(zip( [' health' , ' mana ' , ’ melee' ’ 'armor'] , [490, 334, 550 , 18.72]))
  
  #2                                    
  lux3 = dict([( ’ health ’ , 490) , ('mana' , 334) , ('melee' ’ 550) , ('armor' , 18.72)]) 
  
  #3                  
  lux4 = dict({'health ’ 490 , ’ mana ’ 334, 'melee ’ 550 , ' armor ’ : 18 .72})
               
  
  print(x)
  
  #실행결과
  {'health': 490, 'mana': 334, 'melee': 550, 'armor': 18.72}
  ```

  

  

- 딕서너리의 키에 값 할당하기

  **딕서너리[키] = 값**

  ```python
  lux = {'health’: 490, ’mana’: 334, 'melee’: 550, ’armor': 18.72}
  lux['health'] = 2037 #키 'health'의 값을 2037로 변경
  lux['mana'] = 1184 # 키 'mana'의 값을 1184로 변경
  print(lux)
  
  lux['mana_regen']=3.28 #키 'mana_regen'을 추가하고 값 3.28 할당
        
  ```

  

- 딕셔너리에 키가 있는지 확인하기

  **키 in 딕셔너리**

   

> ## **if조건문에 문자열 지정하기**

문자열은 내용이 있을때 참, **빈 문자열은 거짓**입니다.

```python
if 'hello': 
    print('참')
else:
    print('거짓')
if '':
    print('참')
else:
    print('거짓')
=>
참
거짓
```



0, None, 빈문자열 ' '을 not으로 뒤집으면 참이 되므로 if를 동작시킬 수 있습니다.

```python
if not 0 :
print ('참') # not 0은 참
if not None:
print( ‘참‘ # None 은 참
if not '':
print( '참') # not 빈 문자열은 참
```



**True, False로 취급하는 것들**

```python
다음은 파이씬 문법 중에서 False로 취급하는 것들입니다
• None 
• False 
• 0 인 숫자들 0, 0.0, 0j 
• 비어있는문자열, 리스트，튜플，딕셔너리，세트: ", "" , [], (), {} , set() 
• 클래스 인스턴스의 __ booC _ ( ), __ len __ ( ) 메서드가 0 또는 Fa1se를 반환할 때
```



**None과 False는 같은건가요?**

None이 False로 취급되긴하지만 None과 False는 같지 않습니다. None은 아무것도 없다는 뜻이며, False는 거짓을 나타냅니다. 다음과 같이 is 연산자로 None과 False가 가은지 확인햅면 False가 나오므로 둘은 서로 다릅니다

```python
None==False
=>False
None is False
=>False
```





> ## **for문**



- 시퀀스 객체로 반복하기

  ```python
  for는 range 대신 리스트,튜플, 문자열 등 시퀀스 객체 반복가능함
  
  a = [10, 20, 30, 40]
  
  for i in a:
      print(i)
  ```

- 최대값 구하기

  ```python
  numbers = [7, 10, 12, 14, 26]
  max_num = numbers[0]
  for i in numbers:
  	if (max_num < i) 
  ```

- reversed 활용하기

  ```python
  for i reversed(range(10)):
      print('hello world, i')
  
                
  ```

> ## while문

```python
초기식
while 조건식:
    반복할 코드
   	변화식
```





> ##  all /any

```python
all: 인자로 받는 iterable(range, list)의 모든 요소가 참이거나 비어있으면 True를 반환합니다.

any:  인자로 받는 iterable(range, list)의 요소 중 하나라도 참이면 True를 반환하고, 비어있으면 False를 반환합니다.
ex) 리스트에 0 하나만 있으면 False로 반환함

    
```

>### **break, continue**

break 는 for , while 문법에서 제어 흐름을 벗어나기위해 사용, **continue**는 break와 비슷하지만 약간 다른 점이 있다. **break는 제어흐름을 중단하고 빠져나오지만, continue는 제어흐름(반복)을 유지한 상태에서 코드의 실행만 건너띄는 역할, 비유: 카드게임을 할 때, 패가 안 좋으면 판을 포기하고 다음 기회를 노리는 것과 비슷 **



- ### break

  - **while**

  ```python
  i = 0
  while True: # 무한루프
  	print(i) 
      i += 1 #i를 1씩 증가시킴
      if i == 100: #i가 100일때
          break #반복문을 끝냄, while의 제어흐름을 벗어남
          
          
  ```

  - **for**

  ```python
  for i in range(100):
      print(i)
      if i == 100:
          break
  ```

  

- ### **continue**

  - **for**

    ```python
    for i in range(100):
        if i % 2 == 0:
            continue
        print(i)
       
    #실행결과
    1
    3
    5
    ...(생략)
    95
    97
    99
    ```

    

  - **while**

    ```python
    i = 0
    while i < 100:
        i += 1
        if  i % 2 == 0:
            continue
        print(i)
        
    #실행결과
    1
    3
    5
    ...(생략)
    95
    97
    99  
    ```

    