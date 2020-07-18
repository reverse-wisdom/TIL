#### 2020.07.17 스타트캠프 파이썬 학습내용

#2020.07.16 내용 복습 #웹크롤링

#G : 구글링해서 알게된 내용 추가

#### 1) 프로그램 언어: 저장, 조건, 반복![구글링아이콘](커밋.assets/구글링아이콘.PNG

* 저장

  내용: 글자( 따옴표 ''로 둘러싼 형태), 숫자(23eb(x), 문자 섞이면 안됨), T/F

  박스형식: 변수, 리스트([ ]), 딕셔너리 ( {키 : 아이템})
  
  ``` python
  # 박스이름이 'dust' 인 박스에 60을 저장(할당) 한다
  dust = 60
  
  ```
  
  #버그원인: 대소문자, 띄어쓰기, 스펠링

- 조건(IF)

  ``` python
  if dust > 150:
      print("매우나쁨")
  elif dust>80:
      print('나쁨')  
  elif dust>30:
      print('보통')
  else:
      print('좋음')
      
  ```

  

- 반복(While/ For문)

  ​	while :  종료조건을 지정해주어야함
  ​	for : 정해진 범위를 반복하기 때문에 종료조건이 필요없음, 반복횟수가 정해져있음

  - [x] while/ for 예시

    ``` python
    #입력
    n = 0
    greeting = '안녕하세요'
    while n < 5:
        print(greeting)
        n = n + 1
       
    ```

    ``` python
    #실행결과
    안녕하세요
    안녕하세요
    안녕하세요
    안녕하세요
    안녕하세요
    ```

    ``` python
    n = 0
    greeting = '안녕하세요'
    for i range(5): #range(5)는 [0,1,2,3,4] 와 같은 의미
        print(greeting)
    ```

    ``` python
    #실행결과
    안녕하세요
    안녕하세요
    안녕하세요
    안녕하세요
    안녕하세요
    ```

    

#### 2) 함수종류

- 내장함수(ex. random, webbrowser, os 등) 

   - 파이썬이 기본으로 제공하는 외장모듈(책상서랍에 위치)

     ​	- import

     ​	- 사용

```python	
#사용예시
import random
```

- [x] **random 모듈 random, randint, randrange 함수 **( **#G** )

  * **random**

    - 0.0이상 1.0 미만의 실수(float)를 리턴(반환)한다.

          ``` python
    # 입력
    r = random.random() + 1.0
    #원하는 숫자를 더해 그 난수의 범위를 조절할 수 있다.
          ```

     ``` python
    #출력결과
    1.4285550600788803 
     ```

  * **randint**

    ``` python
    # 입력
    r = random.randint(1, 10) # 1 이상 10 이하의 정수(int)를 리턴한다.
    ```

    ``` python
    # 출력결과
    10 # random, randrange 함수와는 달리 마지막 숫자가 포함되는 것이 특이하다.
    ```

    

  * randrange

    ``` python
    # 입력
    r = random.randrange(0, 10, 2) #0이상 10 미만 2의 배수를 리턴한다.
    ```

    ``` python
    # 출력결과
    6
    ```

    * **range 함수 사용법과 동일**하다.

- [x] **random 사용예시**

  * sample : 로또번호 추천

  ``` python
  #입력
  import random
  numbers= range(1,46)
  lucky=randome.sample(numbers,6)
  print(lucky)
  
  ```

  ``` python
  #실행결과
  [8, 20, 17, 33, 28, 29]
  ```

  * choice: 점심메뉴고르기

  ``` python
  lunchmenu = ['새우오일파스타', '광어초밥', '해물순두부']
  import random
  random_luchmenu=random.sample(lunchmenu)
  print(random_runchmenu)
  ```

  ``` python
  #실행결과
  해물순두부
  ```

  

  |          |                            sample                            |                            choice                            | shuffle(#G)                                                  |
  | :------: | :----------------------------------------------------------: | :----------------------------------------------------------: | ------------------------------------------------------------ |
  | 사용예시 |                        로또번호 추천                         |                        점심메뉴고르기                        |                                                              |
  |   설명   | 시퀀스 자료형을 인자로 전달받아 임의의 값(난수)을 필요한 개수만큼 리스트(list)로 반환 | 리스트 같은 시퀀스 자료형을 인자로 전달받아 임의의 값을 반환 | - 시퀀스 자료형을 인자로 전달받아 임의의 값(난수)을 필요한 개수만큼 리스트(list)로 반환                                                                            - 리턴값이 없고, 전달하는 시퀀스 자료형(리스트)*변수 내용 자체를 변경한다. |



![난수,랜덤함수](커밋.assets/난수,랜덤함수.PNG)

- 외장함수

  - 다른 사람이 만들어둔 외장모듈 (문구점에 사러가야 함.)

    ​	- pip 툴을 이용해서 외장 모듈을 설치

    ​	- import

    ​	- 사용

#### 3) 웹크롤링을 위한 외장모듈

 #모듈: 함수나 클래스를 모아 놓은것 

- requests

  - 간편한 http 요청처리기가 들어있는 모듈

  - 설치하는 방법

    ``` python
    pip install requests
    ```

* BeautifulSoup

  - 텍스트로 나타나는 html을 우리가 사용하기 쉽게 바꿔주는 역할을 하는 모듈

  - 설치가 필요함

    ``` python
    pip install beautifulsoup4
    ```

  * 파이썬 내장함수인 json을 활용해서 json형태는 -> Dictionary 형태로 변환해서 사용

#### 4) 웹크롤링 & API 통신의 큰 흐름

1. url로 요청을 한다.
2. 받은 응담을 가지고 원하는 데이터를 가지고 온다.





​		