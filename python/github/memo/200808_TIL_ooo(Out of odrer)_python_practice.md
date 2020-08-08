**iterable**

tuple, list, range, str, bytes, bytearray, set, dict



**[출처]** [[PYTHON\] iterable, iterator](https://blog.naver.com/imbgirl/221944531037)|**작성자** [내이름은소영](https://blog.naver.com/imbgirl)



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

-> 변경할 수 없고, 순서가 있고, 순회가 가능한

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

**.capiltaize(), title(), upper()**

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



**lower(), swapcase()**







