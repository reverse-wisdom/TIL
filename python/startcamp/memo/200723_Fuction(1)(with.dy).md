> ## **함수**

1. **함수를 사용하는 이유**

   - 한번 정의하면 이후에는재활용해서 사용할 수 있기 때문
   - 코드의 짜임새가 좋아지며 간결하게 표현할 수 있기 때문

2. **함수의 기본특징**

   - return: input을 가공한 결과로 함수 밖에서 활용하기 위해 내보내는 역할
     - 함수는 그 즉시 종료된다.

   - argument(인자): 함수에 input으로 들어오는 값
   - parameter(매개변수): 함수에 들어올 값을 받는 변수

3. 함수호출

   - 정의한 함수의 명과 함수에 필요한 input값을 같이 넣어주는 형태로 호출

   - 내장함수: `dir(__builtins--)`

      비교: 식별자(예약어)

     ```python
     import keyword
     print(keyword.kwlist)
     ```

4. 일급객체(first class object)

   - 파이썬은 객체이며 파이썬 함수는 아래 3가지 조건을 만족하깅 1급 객체이다.

   - 3가지조건

     1. 변수에 담을 수 있다.
     2. 인자로 해당 객체를 전달할수 있다.
     3. 반환값으로 전달할 수 있다.

     ```python
     def first():
         return 3 # 일반 변수
     def second():
         return first() #첫번째 함수
     def third(func):
         return func() # 인자로도 반환값 전달가능
     
     sample = second()
     third(first)
     
     ```

     

5. 위치 인자 : 매개변수가 선언된 순서대로 인자의 값이 대입되는 형태

   ```python
   def func(a, b):
   	return a + b
   func(3, 5)
   ```

6. 키워드 인자: 해당 매개변수에 직접 인자를 전달하는 형태

   ```python
   def func(a, b):
       return a + b
   func(a=6, b=7)
   #위치인자와 같이 사용가능
   func(4, b=10) # 사용가능
   func(a=9, 10) # 사용불가 
   #위치인자가 먼저 나오고 나중에 키워드 인자를 사용해야하기 때문
   func(8, a=10) # 사용불가
   #위치인자로 a가 절달이 되었는데 키워드인자로 다시 전달되기 떄문에 에러발생
   ```

   

7. 기본값 인자 : 매개변수에 초기 값을 설장한 형태

   ```python
   def func(a, b=5):
       return a + b
   func(3, 4) ->7
   func(2) -> a=2, b=5 -> 7
   ```

   

8. 가변 인자 리스트

   - 입력되는 입자의 갯수가 정해져 있지 않을때 사용.
   - 가변인자로 들어오는 인자들은 `tuple` 형태로 저장되어짐
   - 매개변수 앞에  `*`를 붙여주는 형태로 가변인자를 받을 수 있음

   ```python
   def func(*args):
       print(type(args)) #tuple
       print(args) #(인자1, 인자2, 인자3)
   ```

   

9. 정의되지 않은 키워드 인자

   - 입력되는 키워드가 다영할 떄 주로 사용.
   - `dictionary` 형태로 저장이 되어짐.
   - 매개변수 앞에 **를 붙여주는 형태로 정의

   ```python
   def func(**kwargs):
       print(type(kwargs)) #dictionary
       print(kwargs) #{키워드: 값, 키워드2: 값2, 키워드3: 값3}
   ```

   

10. 이름공간(name space)부제: 우리집 중2 히키코모리 동생.

    - LEGB

      - Local (정의된 함수 내부)

      - Enclosed (함수 내부에 다시 함수가 정의 되어 있을때 내부함수가 아닌 바깥의 함수)

      - Global (함수밖의 변수)

      - Built-in

11. 재귀함수

    - 함수가 함수 본인을 내부에서 호출하는 형태

    - 작고 반복적인 문제로 나눌 수 있는 문제를 해결하기 위해 사용

    - 재귀함수는 메모리를 많이 사용하기 때문에 사용에 신중할 필요가 있다(공간 복잡도 상승)

      

      ```python
      K = K(n-1) + K(n-2)
      
      def fib(n):
          if n > 2:
          	return fib(n-1) + fib(n-2)
          else:
              return n
      ```

      