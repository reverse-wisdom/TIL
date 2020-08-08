**iterable**

tuple, list, range, str, bytes, bytearray, set, dict

**immutable**

숫자, 글자, 참거짓, range, tuple, frozenset()

**mutable**

list, dict, set

**dict/key**

키에는 mutabel 올수없음



**가변인자리스트**

- 개수가 정해지지 않은 임의의 인자륿를 받기 위해서 가변인자 리스트  *args 를 활용

- 가변인자리스틑 tuple형태로 처리되며 매개변수에 *로 표현

  ```python
  *args : 임의의 개수의 위치인자를 받음을 의미
      보통 이 가변 인자리스트는 매개 변수 목록의 마지막에 옵니다.
  ```

  

<img src="C:\Users\OFFICE\AppData\Roaming\Typora\typora-user-images\image-20200808125209231.png" alt="image-20200808125209231" style="zoom:55%;" />

**내장함수 목록보기**

```python
print(dir(__builtins__))
```

**리스트와 딕셔너리**

```python
a = {'a': 1, 'b':2}
print(list(a))

#실행결과
['a', 'b']

```

**함수와 스코프**

전역 스코프: 코드 어디에서든 참조 할수 있는 공간

지역 스코프 : 함수가 만든 스코프로 함수 내부에서만 참조할 수있는 공간

### **문자열**

-> ★변경할 수 없고, 순서가 있고, 순회가 가능한

**.find(x)**

x 인덱스 반환 중복되면 첫번째 위치반환 없으면 -1반환

**.index(x)**

-> find랑 같은데 x의. 없으면 오류발생 (value error)

**.replace(old, new,횟수)**

-> 바꿀 대상 글자를 새로운 글자로 바꿔서 반환

횟수를 지정하면 해당 갯수만큼만 시행

**.strip()**

-> 특정한 문자들을 지정하면, 양쪽을 제거하거나 왼쪾을 제거하거나 오른쪾을 제거함

**split()**

문자열을 특정한 단위로 나누어 **리스트**로 반환

**.join()**

**'separator'.join(iterable)**

★ **반복가능한 컨테이너의 요소** 들을 **separator를 구분자로 합쳐  문자열로 반환**

 #반복가능 튜플 리스트 

**.capiltaize(), title(), upper(), lower(), swapcase()**

->변형시켜 반환만하기 떄문에 a를 출력해보면 그대로

```python
a = 'hI! Everyone, I\'m kim'
a.capitalize()
a.title()
a.upper()
print(a) #변형을 시켜 반환만 하기때문 a를 출력해보면 그대로
```



```python
a = 'hI! Everyone, I\'m kim'
print(a.capitalize()) #앞글자를 대문자로 만들어반환
print(a.title()) #어포스트로피나 공백이후를 대문자로 만들어반환
print(a.upper()) #모두 대문자로 만들어 반환
print(a.lower()) #모두 소문자로 만들어 반환한다
print(a.swapcase())  # 대 <-> 소문자로 변경하여 반환한다.

#실행결과
Hi! everyone, i'm kim
Hi! Everyone, I'M Kim
HI! EVERYONE, I'M KIM
hi! everyone, i'm kim
Hi! eVERYONE, i'M KIM

```

### **리스트**

★ 문자열은 변경불가, 리스트는 내용 변경가능

★ 변경가능하고, 순서가 있고, 순회가능한

**append(x)** : 리스트에 값을 추가 할 수 있음, 값변경됨

```python
cafe = ['starbucks', 'tomntoms', 'hollys']
print(cafe)
```



**extend(x)**: 리스트에 iterable 값을 붙일수 있음, 덧셈과 같은기능

```python
cafe = ['starbucks', 'tomntoms']

cafe.extend(['wcafe', '빽다방'])
print(cafe)
cafe.extend(range(1,10))
print(cafe)
cafe.extend('abc')
print(cafe)
cafe.extend(('t','a'))
print(cafe)
cafe.extend({'1': 'star'})
print(cafe)
cafe+=['mccafe','droptop']
print(cafe)

#실행결과
['starbucks', 'tomntoms', 'wcafe', '빽다방']
['starbucks', 'tomntoms', 'wcafe', '빽다방', 1, 2, 3]
['starbucks', 'tomntoms', 'wcafe', '빽다방', 1, 2, 3, 'a', 'b', 'c']
['starbucks', 'tomntoms', 'wcafe', '빽다방', 1, 2, 3, 'a', 'b', 'c', 't', 'a']
['starbucks', 'tomntoms', 'wcafe', '빽다방', 1, 2, 3, 'a', 'b', 'c', 't', 'a', '1']
['starbucks', 'tomntoms', 'wcafe', '빽다방', 1, 2, 3, 'a', 'b', 'c', 't', 'a', '1', 'mccafe', 'droptop']

```



**.insert(i, x)** : 정해진 위치 i에 값을 추가합니다  # 원본변경

```python
cafe = ['starbucks', 'tomntoms']
cafe.insert(0, 'start') #가장앞에추가
cafe.insert(len(cafe),'end') #맨 뒤에 추가

#실행결과
['start', 'starbucks', 'tomntoms']
['start', 'starbucks', 'tomntoms', 'end']
```



```python
cafe = ['starbucks', 'tomntoms']

cafe.insert(len(cafe)+100, '!')
print(cafe)
cafe.insert(10000, '!')
print(cafe)
#실행결과
['starbucks', 'tomntoms', '!']
['starbucks', 'tomntoms', '!', '!']
```



**.remove(x)**

리스트에서 값이 x인것을 삭제합니다.

값이 없으면  오류남

```python
numbers = [1, 2, 3, 1, 2]
numbers.remove(1)

```



**.pop(i)**

정해진 위치 i에 있는값을 삭제하여, 그항목을 반환합니다.

i가 지정되지 않으면 마지막항목을 삭제하고 되돌려줍니다

```python
a = [1, 2, 3, 4, 5]
a.pop(0)
print(a)

#실행결과
[2, 3, 4, 5]

```

```python
print(a)
deleted_value = a.pop()
print(f'{deleted_value}가 삭제되어 {a}가 되었습니다.')

#실행결과
[2, 3, 4, 5, 6]
6가 삭제되어 [2, 3, 4, 5]가 되었습니다.
```

**.clear()**

```python
numbers = list(range(1, 10))
print(numbers)
numbers.clear()
print(numbers)

#실행결과
[1, 2, 3, 4, 5, 6, 7, 8, 9]
[]

```

**.sort()**

- 정렬을 하는 함수, 내장함수 sorted() 와는 다르게 원본 리스트를 변형시키고 None을 반환시킴



**리스트복사**

```python
a = [1, 2, 3]
b = a[:]

#b[0] = 5
print(a)
print(b)
print(a is b)

#실행결과
[1, 2, 3]
[1, 2, 3]
False

a = [1, 2, 3]
b = list(a)

#b[0] = 5
print(a)
print(b)
print(a is b)

#실행결과
[1, 2, 3]
[1, 2, 3]
False
```

