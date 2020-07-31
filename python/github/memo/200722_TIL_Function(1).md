> ## 20200722 [온라인]함수 - 개념정리

###  함수

- **함수(funtion) : 특정한 기능을 하는 코드의 묶음**
  
  - 가독성
  - 재사용성
  
  - 유지보수
- **함수의 선언과 호출**

  - 함수 선언은 `def`로 시작하여 `:` 으로 끝나고, 다음은 4spaces 들여쓰기로 코드블록을 만든다.

  - 함수는 `매개변수` 를 넘겨줄 수 도있다

  - 함수는 동작후에 `return`을 통해 결과값을 전달할 수 도 있다.

    (`return` 값이 없으면 `None`을 반환한다.)

  - 함수는 호출을 `func()/fun(val1, val2)`  와 같이한다.

- **함수관련용어**

  - 함수의 입력

    - 매개변수(parameter)  = 형식인자

       ```python
      def func(x):
          return x + 2
      ```

      -`x`는 매개변수

      -입력을 받아 함수 내부에서 활용할 변수라고 생각하면 된다

      -함수의 정의 부분에서 볼 수 있음

    - 전달인자(argument)

      ```python
      func(2)
      ```

      -`2`는 전달인자

      -실제로 전달되는 `입력값`이다.

      -함수를 호출하는 부분에서 볼 수 있다

  - 함수의 출력

    - 함수의 return

  - 함수의 인자

    - 위치 인자(Positional Arguments) : 함수는 기본적으로 인자를 위치로 판단합니다.

    - 기본 인자값(Default Argument Values): 함수가 호출될 때, 인자를 지정하지 않아도 기본 값을 설정할 수 있습니다. 

      ```python
      # 1.함수정의
      def greeting(name = '익명')
      	return f'{name}, 안녕?'
      # 2,호출
      greeting()  #인자를 지정하지 않아도
      
      # 3.실행결과
      '익명, 안녕?'
      ```

      

      ```python
      # 1.함수정의
      def greeting(name ='익명'): 
          return f'{name}, 안녕?'
      # 2.호출
      greeting('ssafy')
      # 3.실행결과
      'ssafy, 안녕?'
      ```

      ** `★주의★ 단, 기본 인자값(Default Argument Value)을 가지는 인자 다음에 기본 값이 없는 인자를 사용할 수는 없습니다.`**

      ```python
      # 1.함수정의
      def greeting(name='익명', grade):
          return f'{grade}학년 {name}님,환영합니다'
      # 2. 호출
      greeting(4)
      # 3. 실행결과
      SyntaxError: non-default argument follows default argument
      # 전달인자가 name 인지, grade 인지 확실하지 않음
          
      ```

      ```python
      # 1.함수정의
      def greeting(grade, name='익명'):
          return f'{grade}학년 {name}님,환영합니다'
      # 2. 호출
      greeting(4)
      # 3. 실행결과
      '4학년 익명님,환영합니다'
      ```

      

    - 키워드 인자(Keyword Arguments): 키워드 인자는 직접 변수의 이름으로 특정 인자를 전달 가능

       **★키워드인자 쓸 때 주의할점★**
         1) 호출할때, 함수정의할때 쓴 매개변수 다 명시해서 지정해주던지
         2) 뒤에만 쓰던지 해야함

      ```python
      # 예시1
      # 1. 함수정의
      def greeting(age, name='익명'):
          return f'{age}세 {name}님 환영합니다'
      # 2. 함수호출
      greeting(20, '홍길동')
      # 3. 실행결과
      20세 홍길동님 환영합니다'
      ```

      ```python
      # 예시2
      # 1. 함수정의
      def greeting(age, name='익명'):
          return f'{age}세 {name}님 환영합니다'
      # 2. 함수호출
      greeting(age=20, name='홍길동')
      # 3. 실행결과
      20세 홍길동님 환영합니다'
      ```

      ```python
      # 예시3
      # 1. 함수정의
      def greeting(age, name='익명'):
          return f'{age}세 {name}님 환영합니다'
      # 2. 함수호출
      greeting(name='홍길동', age='20') #★강제로 매개변수를 지정하고 호출하면 위차변경가능
      # 3. 실행결과
      20세 홍길동님 환영합니다'
      ```

      ```python
      # 예시4
      # 1. 함수정의
      def greeting(age, name='익명'):
          return f'{age}세 {name}님 환영합니다'
      # 2. 함수호출
      greeting(name='홍길동', 20) 
      #  ==>호출할때, 함수정의할때 쓴 매개변수 다 명시해서 지정해주어야함
      
      # 3. 실행결과
      SyntaxError: positional argument follows keyword argument
      ```

      ```python
      # 예시5
      # 1. 함수정의
      def greeting(age, name='익명'):
          return f'{age}세 {name}님, 환영합니다'
      # 2. 함수호출
      greeting(20, name='홍길동')
      # 3. 실행결과
      '20세 홍길동님 환영합니다'
      ```

      ```python
      # 예시6
      # 1. 함수정의
      def greeting(age, name='익명'):
          return f'{age}세 {name}님, 환영합니다'
      # 2. 함수호출
      greeting('tom', age=32)
      
      #age='tom'
      #age=20
      
      # 3. 실행결과
      TypeError: greeting() got multiple values for argument 'age'
      # ==> age에 값이 두개라서 오류남
      
      ```

      

    - 가변인자리스트 

      -앞서 설명한 `print()`처럼 개수가 정해지지 않은 임의의 인자를 받기 위해서는 가변 인자 리스트`*args`를 활용합니다. 

      -가변 인자 리스트는 `tuple` 형태로 처리가 되며, 매개변수에 `*`로 표현합니다.

      -타입: tuple

      ```python
      def func(a, b, *args):
      
      # args : 임의의 개수의 위치인자를 받음을 의미
      # 보통, 이 가변 인자 리스트는 매개변수 목록의 마지막에 옵니다.
      ```

      ```python
      # 예시(타입 및 출력값 확인)
      def func(a, b, *args):
          print(type(a))
          print(type(b))
          print(type(args))
          pritn(args)
          
      #함수호출
      func(10, 20, 30, 40, 50, 60)
      
      #실행결과
      <class 'int'>
      <class 'int'>
      <class 'tuple'>
      (30, 40, 50, 60)    
      ```

      ```python
      # 예시2
      
      def func(*args):
          for i in args:
          	if i % 2 ==0:
          		print(i, end=' ')
              
      func(1, 2, 3, 4, 5, 6)
      
      # 실행결과
      2 4 6
          	
      ```

      ```python
      
      ```

      

    - 가변 키워드 인자

      -*args 차이점: 인자를 두개 받음 *args 는 한개

      -정해지지 않은 키워드 인자들은 **`dict`** 형태로 처리가 되며, `**`로 표현합니다. 

      -보통 `kwargs`라는 이름을 사용하며, `**kwargs`를 통해 인자를 받아 처리할 수 있습니다.

      ```python
      def func(**kwargs):
          
      ```

      > `**kwargs` : 임의의 개수의 키워드 인자를 받음을 의미 		

      ```python
      # 예시1(타입 및 출력값 확인)
      
      # 1. 함수정의
      def func1(**kwargs):
          print(type(kwargs))
          print(kwargs)
          print(kwargs['name'])
          
      # 2. 함수호출
      func1(name='ed', age='20', gender='male')
      
      # 3. 실행결과
      <class 'dict'>
      {'name': 'ed', 'age': '20', 'gender': 'male'}
      ed
      ```

      ```python
      # 예시2
      # 딕셔너리 생성 함수(키워드 인자)
      
      hi = dict(한국어='안녕',영어='hi')
      print(hi)
      
      #실행결과
      {'한국어': '안녕', '영어': 'hi'}
      ```

      ```python
      # 예시3
      
      # 1. 함수정의
      def my_dict(**kwargs):
          return kwargs
      
      # 2. 함수호출
      my_dict(한국어 = '안녕') #앞에꺼는 스트링 붙이지말것
      
      # 3. 실행결과
      {'한국어': '안녕'}
      ```

      

  ```python
  # 기본형식
  def <함수이름>(parameter1, parameter2):
      <코드블럭>
      return value
  
  # 참고 
  
  def cube(num): # num 이라는 이름을 쓰겠다
      return num
  cube(2)
  
  #실행결과
  2 # 반환값 // 코드블럭이 따로 없어서 입력한 값 바로 뱉음
  ```

  

  ```python
  # 예시1
  Q. 입력 받은 수를 세제곱하여 반환(return)하는 함수 cube()을 작성해보세요.
  
  # 입력
  def cube(num): #함수이름 cube, 매개변수 num // 1.함수정의
      cubed = num**3 
      return cubed #반환값
  cube(2) #2는 전달인자 // 2. 함수호출
  
  #실행결과
  8 #8은 리턴값
  
  ```

  **※ 제곱함수 `pow`**

  pow(2, 3)

  =>8

  ```python
  # 예시2
  Q. 사각형 넓이를 구하는 함수
  밑변(width)과 높이(height)를 입력받아 사각형의 넓이와 둘레를 반환(return)하는 함수 `rectangle()`을 작성해보세요.
  
  [입력 예시]
  rectangle(30, 20)
  
  [출력 예시]
  (600,100)
  
  # 입력
  def rectangle(width, height):
      area = width * height
      perimeter = (width + height)*2
      return(area, perimeter)
  print(rectangle(30, 20))
  print(rectangle(50, 70))
  
  #실행결과
  (600, 100)
  (3500, 240)
  ```

  ```python
  # 예시3
  Q.2개의 매개변수중 최대값 구하는 함수를 작성하고 하출하세요
  
  def my_max(a, b):
      if a >= b:
          return f'{a}가 더 큽니다'
      else:
          return f'{b}가 더 큽니다'
  my_max(6, 8)
  
  ```

  

- **내장함수 목록 보는 방법**

  ```python
  dir(__builtins__)
  
  #실행결과
  ['ArithmeticError',
   'AssertionError',
   'AttributeError',
   'BaseException',
   'BlockingIOError',
   'BrokenPipeError',
   'BufferError',
   'BytesWarning',
   'ChildProcessError',
   'ConnectionAbortedError',
   'ConnectionError',
   'ConnectionRefusedError',
   'ConnectionResetError',
   'DeprecationWarning',
   .
   .
   .]
  ```

  