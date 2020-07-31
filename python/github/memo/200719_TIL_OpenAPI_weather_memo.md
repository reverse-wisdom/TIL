* [x] **API활용해서 날씨정보 구하기**

  구동환경: https://py.hphk.io/bots/2960 > 날씨

```python

#API를 활용해서 실시간 날씨 확인
#https://openweathermap.org/current
#Examples of API calls > api.openweathermap.org/data/2.5/weather?q=London 클릭
#CROME Web Store > JSON viewer 설치 

#1.필요한 모듈 불러오기

import requests

# 2. 요청 url을 만드세요.

city = 'Gumi'
url = f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={key}'
#문자메소드 f''
#복사값에서 https//:, city, key 값 편집
response = requests.get(url).json()
#Gumi찾기
# By citi ID > http://bulk.openweathermap.org/sample/ > 제일 최근 파일 업로드 > CODE 열기 > 'Gumi' 검색

#기온에 대한정보
#바깥꺼부터 접근
data = response['main'] #3 링크에서확인
print(data['temp'])
#날씨, 현재온도, 최저 및 최고온도에 대한 데이터
weather = response['weather'][0]['main'] #값이 한개밖에 없어서 0
temp = data['temp']-273.15
max_temp = data['temp_max']-273.15
min_temp = data['temp_min']-273.15

print(f'현재 {city}의 날씨는 {weather}이며, 현재 기온은 {temp} (최저:{min_temp} /최고:{max_temp}')
```

