#### | 웹크롤링 & API 통신의 큰 흐름

1. url로 요청을 한다.
2. 받은 응답을 가지고 원하는 데이터를 가지고 온다.

* [x] **웹크롤링 예시**

  **1) 코스피**

  ``` python
  #입력
  
  
  import requests #reaquest 모듈 불러오기 
  from bs4 import BeautifulSoup # bs4 모듈에서 Beautifulsoup 함수 불러오기
  
  # import와 from import 차이
  # 후자가 더 간단함
  # ex)BeautifulSoup를 쓰기 위해서 bs4.BeautifulSoup 이렇게 써야하는데
  # bs4를 쓰기 귀찮고 BeautifulSoup만 쓰기 위해서 from bs4 import BeautifulSoup 씀
  # => 하단 data 변수 저장할때 bs4.를 안붙여도됨
  
  url = 'https://finance.naver.com/sise/' # 데이터 불러올 사이트
  
  response = requests.get(url).text
  data = BeautifulSoup(response, 'html.parser')  #html.parser와 xml 있음
  select = data.select_one('#KOSPI_now') # url사이트에서 F12(개발자도구 활성화 키) 누르고 필요한 값 불러오기
  print(select.text)
  
  
  #실행결과
  2,202.19
  ```

  **2)실시간검색어**

  ```python
  #입력
  
  
  import requests
  from bs4 import BeautifulSoup
  
  url = 'https://www.daum.net/'
  
  response = requests.get(url).text
  data = BeautifulSoup(response, 'html.parser')
  select = data.select('#wrapSearch > div.slide_favorsch > ul > li > a') 
  #: 이하 지우기
  for i in select: #리스트 각 요소 하나씩 출력하기
      print(i.text) #텍스트만 추출
      
      
  #실행결과
  생활 속 거리두기
  해수부 기술이전
  내차가격알아보기
  이승우 퇴장
  린넨자켓추천
  코로나19 발생현황
  제니 브랜드평판
  샌들쇼핑몰
  싹쓰리 1위
  명품가방브랜드순위
  ```

  ※차이점

  코스피는 파싱하는 값이 하나, 실시간검색어는 다수라서 전자는 select, 후자는 select_one을 쓰고

  실시간 검색어는 리스트 각각의 값을 불러와야 하기 때문에 for문으로 받아야함

  

  

