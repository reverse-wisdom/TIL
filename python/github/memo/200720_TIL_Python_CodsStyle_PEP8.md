>## **Python PEP 8 표준 코드 스타일 **

▣ 기본 규칙

- 코드 내 일관성이 중요함

* 들여쓰기 레벨당 4개의 공백의 사용

* 한줄에 최대 79글자로 제한, 넘어가면 역슬러쉬로 줄나눔

* 갈호 열때, 요소들이 여러개 일 경우 수직으로 정렬해서 쓰자

  ```python
  #1 갈호가 열렸을떄 라인을 맞춤
  foo = long_function_name (var_one, var_two,
                           var_three, var_four)
  #2 함수가 정의 될때 name level 4칸 들여쓰기
  def = long_function_name (
          var_one, var_two, var_three,
          var_four) :
      print(var_one)
  #3 인자끼리 라인 맞추기
  foo = long_function_name (
      var_one, var_two,
      var_three, var_four)
  
  wrong
  
  #1
  foo = long_function_name (var_one, var_two,
      var_three, var_four)
  #2
  def long_function_name (
      var_one, var_two, var_three,
      var_four) :
      print(var_one)
  
  ```

  

  //그외 들여쓰기 모음

  ```python
  #Correct
  #1
  my_list = [
      1, 2, 3,
      4, 5, 6,
      ]
  결과 = some_function_that_takes_arguments (
      'a', 'b', 'c',
      'd', 'e', ​​'f',
      )
  
  #2
  my_list = [
      1, 2, 3,
      4, 5, 6,
  ]
  결과 = some_function_that_takes_arguments (
      'a', 'b', 'c',
      'd', 'e', ​​'f',
  )
  
  ```

  

* 스페이스바와 탭과 공백을 혼합하여 사용할 수 없음

* 연산자가 여러개 일 경우 

  ```python
  # Wrong
  # 연산자는 피연산자로부터 멀리 떨어져 있습니다.
  수입 = (총액 +
            taxable_interest +
            (배당금-유자격 배당금)-
            ira_deduction-
            student_loan_interest)
  #Correct
  피연산자와 연산자를 쉽게 일치시킬 수 있습니다.
  수입 = (총액
            + taxable_interest
            + (배당금-유자격 배당금)
            -ira_deduction
            -student_loan_interest)
  
  ```

  

* 불필요한 공백을 피하자

  - case1

    ```python
    # Correct:
    spam(ham[1], {eggs: 2})
    
    # Wrong:
    spam( ham[ 1 ], { eggs: 2 } )
    
    ```

  - case2

    ```python
    # Correct:
    foo = (0,)
    
    # Wrong:
    bar = (0, )
    
    ```

  - case3

    ```python
    # Correct:
    if x == 4: print x, y; x, y = y, x
        
    # Wrong:
    if x == 4 : print x , y ; x , y = y , x
    ```

  - case4

    ```python
    # Correct:
    ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
    ham[lower:upper], ham[lower:upper:], ham[lower::step]
    ham[lower+offset : upper+offset]
    ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
    ham[lower + offset : upper + offset]
    
    
    # Wrong:
    ham[lower + offset:upper + offset]
    ham[1: 9], ham[1 :9], ham[1:9 :3]
    ham[lower : : upper]
    ham[ : upper]
    
    ```

  - case5

    ```python
    # Correct:
    i = i + 1
    submitted += 1
    x = x*2 - 1
    hypot2 = x*x + y*y
    c = (a+b) * (a-b)
    
    # Wrong:
    i=i+1
    submitted +=1
    x = x * 2 - 1
    hypot2 = x * x + y * y
    c = (a + b) * (a - b)
    ```

- 변수짓기

  -L 소문자와 I대문자 , 숫자 0 알파벳 O 가급적 사용하지 말것

  -변수지을때 가급적이면 소문자,길어지면 언더스코어(_) 사용

  

- 기본 UTPF8로 설정되어있음

- 영문법에 따르자

  ```python
  # Correct:
  if foo is not None:
  
  # Wrong:
  if not foo is None:
  ```

- 함수 선언할때 ramda 쓰지말것

  