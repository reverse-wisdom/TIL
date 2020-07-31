> ## **문자열 메소드**

**문자열바꾸기**

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

**문자 바꾸기**

- **translate**

  문자열 안의 문자를 다른 문자로 바꿉니다. 

  ```python
  #형식
  str.maketrans('바꿀문자', '새문자')
  ```

  ```python
  #예시
  table = str.maketrans('aeiou', '12345')
  'apple'.translate(table)

  #실행결과
'1ppl2'
  
  ```
  
  

**문자열 분리하기**

- **split**

  공백을 기준으로 문자열을 분리하여 **리스트**를 만듭니다. 

  ```python
  'apple pear grape pineapple orange'. split()
  
  #실행결과
  ['apple', 'pear', 'grape', 'pineapple', 'orange']
   
   
  ```

  

  **split('기준문자열')**과 같이 기준 문자열을지졍하면 기준 문자열로 문자열을 분리합니다. 즉 문자열에서 각 단어가 ,(콤마)와 공백으로 구분되어 있을 때 ', '으로 문자열을 분리하면 단어만 리스트로 만듭니다.

  ```python
  'apple, pear, grape, pineapple, orange'. split(', ')
  
  #실행결과
  ['apple', 'pear', 'grape', 'pineapple', 'orange']
  
  ```

  

**구분자 문자열과 문자열 리스트 연결하기**

- **join**

  구분자 문자열과 문자열 리스트의 요소를 연결하여 문자열로 만듭니다. 다음은 공백 '  '에 join을 사용하여 각 문자열 사이에 공백이 들어가도록 만듭니다.

  ```python
  #형식
  join(리스트)
```
  
  ```python
  ' '.join(['apple', 'pear', 'grape', 'pineapple', 'orange'])
  #실행결과
  'apple pear grape pineapple orange'
  ```
  
  ```python
  '-'.join(['apple', 'pear', 'grape', 'pineapple', 'orange'])
  'apple-pear-grape-pineapple-orange'
  ```

**소문자를 대문자로 바꾸기**

- **upper**

  ```python
  #형식
  upper()
  ```

  ```python
  'python'.upper()
  #실행결과
  'PYTHON'
  ```

- **lower**

  ```python
  #형식
  lower()
  ```

  ```python
  'PYTHON'.lower()
  
  #실행결과
  'python'
  ```

  