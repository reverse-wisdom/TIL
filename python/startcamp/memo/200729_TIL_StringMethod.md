> ## **문자열 메소드**

문자열바꾸기

- **replace**

  문자열 안의 문자열을 다른 문자열로 바꿉니다.(문자열 자체는 변경하지 않으면 바뀐 결과를 반환)

  ```python
  #형식
  replace('바꿀 문자열(new)', '새문자열(old)')
  ```

  ```python
  #예시
  s = 'Hello, world!
  s = s.replace('world', 'Python')
  print(s)
  
  #실행결과
  'Hello, Python'
  ```

문자 바꾸기

- **translate**

  문자열 안의 문자를 다른 문자로 바꿉니다. 

  ```python
  #형식
  str.maketrans('바꿀문자', '새문자')
  ```

  ```python
  #예시
  
  ```

  

  먼저 str. maketrans('바꿀 문자',  '새문자')

