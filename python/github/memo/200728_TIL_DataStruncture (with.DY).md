> ## **예외처리**

- 문법 에러: 문법적 오류가 있을 때

- exception

  - NameError

  - Type Error

  - Value Eroor: int('3.5')

  - ZeroDivisionError

  - IndexError

  - KeyError

  - ModuleError

  - ImportError

  - try & except

    ```python
    try:
        <코드블럭 1>
    except:
        <코드블럭 2>
    except:예외2. 예외3:
        <코드블럭 3>
    except 예외4 as err:
        print(f'{err}로 에러 메세지를 프린트 할 수 있다')
    else: #코드블럭 1에서 에러가 발생하지 않았을 때만 실행
        <코드블럭 4>
    finally:# 반드시 실행
        <코드블럭 5>
        
    ```

    

- 예외 발생

  - raise: 예이를 강제로 발생 `raise valueError` ('숫자를 입력해주세요')

  - assert: 예외를 강제로 발생

    - 상태를 주로 검증하기 위해서 assert Boolean expression, error message

    ```python
    assert type(x) == int, '숫자형이 아닙니다.'
    
    ```

    

> ## 데이터 구조1

- 데이터 구조: 데이터에 편리하게 접근을 하고, 변경하기 위해 데이터를 저장하거나 조작하는방법

- **순서가 있는구조(ordered)**

  - 문자열, 리스트

- **순서가 없는구조(unoredered)**

  - set, dictionary
    - 딕셔너리는 (순서가 있는걸 얼마전에 도입했지만

  ​              없는걸로 생각)

  >  ##  **문자열**
  - 변경할수 없다. (immutble) / 순서가 있다(ordered)/순회 가능하다(iterable)

  **string method**

  * 값을 변경하는 method

    **1)replace**

    ```python
    replace(바꿀문자열(old), 바꾸려는 문자열(new),숫자)
    'yay!'.replace('a', '-') #'y-y!'
    'wooooooo'.replace('o', '!', 3) #'w!!!0000'
    
    ```

    **2)strip([char])**

    ```python
    #특정 문자를 지저하면 해당 문자드를 양쪽에서 찾아 제거한다.
    #lstrip 해당문자를 왼쪽에서 찾아서 제거/rstrip
    ```

    **3)split([char])**

    ``` python
    #문자열을 특정단위로 나누어서 리스트로 반환
    input ='1 2 3 4 5'
    li_input = input.split() #['1', '2', '3', '4', '5']
    
    a = 'a_b_c'
    print(a.split('_')) #['a', 'b', 'c']
    print(a.split('b')) #[`a_', '_c']
    ```

    

    **4)join(iterable)**

    - 특정 문자열로 만들어서 반환

      ``` python
      word = '배고파'
      a = '!'.join(word) #'배!고!파'
      words =['a', 'b', 'c']
      b ='_'.join(words) #'a_b_c'
      
      ```

      

  - 문자변경
    - capitalize()
    - title(): New York Times
    - upper()
    - lower()
    - swapcase()

  - 문자열 관련 검증

    - istitle()
    - isalpha()
    - isspace()
    - isupper() / islower()
    - isdecimal() : 순수 int로 형변환이 가능한 문자열인지
    - isdigit(): 윗첨자도 숫자로 인식

    - isnumeric(): 분수의 특수기호, 특수 라마자도 숫자로 인식
      	 - 주의: 해당 decimal, digit, numeric 은 float형태의 문자열은 False반환

  - 기타 문자열 관련 메소드 확인하는 방법

    ```python
    dir('string')
    ```

  

  ## 

  >  ## **리스트**

  **변경 가능(mutable), 순서가 있고, 순회 가능하다(iterable)**

​		## **List Method**

  - 값을 추가 및 삭제

    - append(x)

    - extend(iterable)

    - insert(i, x)

      ---

    - remove(x) : 첫번째 x 만 삭제, 지우려는 값이 없으면 에러 발생 (반환x 삭제만 함)

    - pop(i) : 정해진 위치에 있는 값을 삭제하고 그값을 반환, i에 값이 없으면 마지막 항목
    - clear(): 리스트의 모든 항목을 삭제

- 탐색 및 정렬

  - index(x): 값이 없으면 에러

  - count(x): 리스트에서 x의 갯수를 count 후 반환

    ---

    ## sort vs sorted 차이점 중요!! 많이사용함

  - sort(): None을 반환, 그리고 원본을 변경 ' sort' (reverse =False 하면 내림차순 정렬 가능)

    **※sorted(iterable: 순서가 있는 타입들은 사용가능, [reverse = True]): 정렬된 값을 반환, 그리고 원본 유지**

    **※ sort는 리스트만 sorted 는 좀 더 유연하게 다양한 타입에 적용가능**

    ---

    

  - reverse(): 정렬 없이 앞뒤를 뒤집어준다.

    reversed():  앞뒤를 뒤집어 준다. list_reverseiterator object 반환

- 리스트 복사

   ```python
  a = [1, 2, 3]
  b = a
  b[0] = 10
  print(a) # [10, 2, 3]
  
   ```

  1. slicing 활용하여 복사

     ```python
     a = [[1, 2], [3, 4]]
     b = a[:]
     a[0] = [4, 5]
     print(b)
     
     # 실행결과
     [[1, 2], [3, 4]]
     
     ```

     ```python
     a = [1, 2, 3, 4]
     b = a[:]
     a[0] = [4, 5]
     print(b)
     #실행결과
     [1, 2, 3, 4]
     ```

     

  2. list() 메소드를 활용해서 복사

     ```python
     a = [1, 2, 3]
     b =list(a)
     b[1] =200
     print(b)
     #실행결과
     [1, 200, 3]
     ```

     

  3. copy 모듈을 활용

     ```python
     import copy
     
     a = [1, 2, 3]
     b = copy.copy(a)
     ```

     

  - deepcopy

    ```python
    import copy
    a =[1, 2, [1, 2]]
    b =copy.deepcopy(a)
    b[1][1] = 3
    print(b)
    ```

  **List Comprehension**

  - 간결한
  - pythonic 한 코드
  - 속도도 빠르다
  - 무분별하게 사용하게되면 가독성이 떨어질 수 있다.

  ```python
  # 기본 형태
  li_comp = [식 for 임시변수 in interable]
  li_comp2 = list(식 for 임시변수 in iterable)
  
  #기본 형태 +조건식
  li_comp3 = [식 for 임시변수 in iterable if 조건식]
  li_comp4 = [식1 if 조건식 else 식2 for 임시변수 in interable]
  li_comp5 = [식1 if 조건식 else 식2 if 조건식2 else 식3 for 임시변수 in iterable]
  ```

  

>  ## **데이터분류** 

 - immutable
   - number, string, bool, range, tuple, frozenset

- mutable
  - list, set, dictionary

---

> ## **Built -in Function**

​	**map(function, iterable)**

​		- iterable한 데이터를 인자로 받아 모든 요소에 function을 적용한 후 결과를 `map object`로 반환

```python
def square(num)
	return num**2

numbers = [1, 2, 3, 4, 5]
double_li = list(map(square, numbers))
print(double_li)
```

```python
input = '1 2 3 4 5'
numbers = input.split
new_numbers = list(map(int, numbers))

print(new_numbers)

#실행결과
[1, 4, 9, 16, 25]
```

 **filter(function, iterable)**

 - function의 return 값이 True인 값만 추출, filter object 값을 반환

   ```python
   def pos_num(num):
       if num > 0:
           return num
       else:
           return False
   number = list(range(-10, 10))
   pos = list(filter(pos_num, numbers))
   
   print(pos)
   #실행결과
   [1, 2, 3, 4, 5, 6, 7, 8, 9]
   ```

   

**zip(iterable)**

- 복수의 iterable 한 객체를 모아준다. tuple 모음으로 구성된 `zip object`를 반환

  ``` python
  girls = ['jane', 'iu', 'mary']
  boys = ['justin', 'david', 'kim']
  ranking = [1. 2 3]
  couples = list(zip(girs, boys, ranking )) 
  
  #실행결과
  [('jane', 'justin', 1), ('iu, 'david', 2), ('mary', 'kim', 3)]
  
  ※ 되도록이면 길이가 같은 객체를 사용하는 것이 좋다.
  ※ 길이가 다르다면 짧은 객체를 기준으로 합쳐주고 나머지는 무시된다.
  ※ itertools 내장 모듈안에 `zip_longest` 함수를 사용하면 긴 것을 기준으로 합쳐준다                    
  ```

  ```python
  #zip_longest
  from intertools import zip_longest
  num1 =[1, 2]
  num2 =[4, 5, 6]
  list(zip(num1, num2)) # [(1, 4), (2, 5)]
  list(zip_longest(num1, num2, fillvalue=0)) #[(1, 4), (2, 5), (0, 6)]
  ```



> ## 데이터구조 

## **세트 (set)**

- 변경가능하고, 순서가없고 순회는 가능
- 집합의 요소는 유니크하다. 중복 불가능
- 집합의 요소는 immutable한 값만 가능, mutable 객체를 넣으면 Type Error 발생
- Set Methods
  - 추가 및 삭제
    - add(elem): 값을 하나추가 시킬때 사용
    - update(*others) : 여러개의 값을 넣을때
    - remove(elem): 값을 삭제를 하고 만약 값이 없으면 KeyError 발생
    - discard(elem): 값을 삭제를 하고 만약 값이 없으면 에러발생하지않는다.
    - pop() : 임의의 요소를 제거한후 반환해준다.

## **딕셔너리**

- 변경가능하고, 순서가없고 순회가 가능하다

- dictionary Methods

  - get(key[,default])

    - key를 통해서 해당 value를 가져온다.

      dic['key']: 키 값을 직접 넣어서 값을 가져올 떄 키가없으면 KeyError 발생

    - key 가 없어도 에러를 발생하지 않음 None을 반환

  - pop(key)
    - key가 있으면 dictionary 에서 제거하고 키가 없으면 default 값을 반환
    - default 가 없으면 keyerror 발생

  - update()
    - 1개 이상의 값을 key = 'value' 의 형식으로 값을 추가 할 수 있다.
    - key가 존재하면 그 값을 수정
    - key 가 존재하지 않으면 새롭게 추가

  - keys()
    - 해당 dictionary의 키를 리스트로 반환 (dict_key object)
  - values()
    - 해당 dictionary의 value를 리스트로 반환 (dict_value object)
  - items()
    - 해당 dictionary의 key와 value를 tuple 로 반환 (dict_items object)

- Dictionary 순회

  ```python
  #1. dictionary를 for로 순회 했을때
  for dic in dicts
  	print(dic) #dicts의 키값이 들어있다
      
  #2. keys 로 순회했을때
  for dic in dicts.keys():
   	print(dic) #dicts 의 키값이 들어있다.
      
  #3. value로 순회 했을때
  for val in dicts.values()
  	print(val) #dicts의 value 만 들어있다.
      
  #4. items로 순회 했을때
  for dic in dicts.items():
      print(dic) #dic 에는 (key, value) 형태의 tuple값이 들어있다.
  
  #5 임시변수 두개 지정가능
  for key, value in dicts.items():
  	print(key)
      print(value)
  ```

  