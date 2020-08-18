

django설치

제이슨에 usage 복사

pip list

터미널창 정리: clear ctr+l

django-admin startproject first_project

view 함수는 무조건 첫번쨰인자로 request로 받아야함

오픈제이슨에 usage 복붙

1. 앱생성
2. 앱등록

JSON 파일

- 파이썬 딕셔너리와 구조와 똑같다.

  {key: value}

- 단 차이점은 json은 binary 형식으로 저장된다. 

  - 쉽게말하면 문자열로 저장이 된다
  - 더 쉽게말하면 10 vs '10'

  

> ## Django

Django 3.1

핵심

사용자가 접근할 수 이는 url을 정의하고, view함수로 연결되게 한다.

view 함수에서 어떠한 데이터를 가공하고, 사용자가 보는브라우저 화면에 렌더링 시킨다

- 이떄 

`pip list`

- 장고 설치하기

  ```django
  pip install django
  
  #특정 버전으로 받고싶다
  pip install django==3.0.8
  
  ```

  

- 장고 시작하기

  ```django
  djang-admin startproject first_wbex
  ```

  - `first_webex`라는 이름으로 폴더가 생성

    - 여기 안에는 `first_webex` 폴더와 `manage.py` 생성되어짐

    - manage.py: 장고 명령어를 실행하기 위한 파일

      `python manage.py 장고 명령어`

    - 가장 바깥에 있는 프로젝트 폴도명은 수정 가능하나, setting 파일이 들어있는 폴더명은 건드리지  말자.

- 서버 실행하기

  - 명령어를 실행하는 경로에 manage.py가 있는지 반드시 확인한다.

  ```django
  $cd 프로젝트이름
  $python manage.py runserver
  ```

  

- 장고 프로젝트는 Application의 집합체로 동작
  - 실제로 어떠한 역할을 해주는 친구가 바로 app.
  - 하나의 프로젝트는 여러개의 어플리케이션을 가질 수 있음
    - 어플리케이션: 하나의 역할 및 기능 단위로 쪼개진 형태.
      - 회원관리/글 작성, 수정, 글 삭제/데이터를 수집분석/....
      - 어플리케이션을 이렇게 나뉘어야한다 같은 기준은 없음
      - 작은 프로젝트라면 어플리케이션을 따로 나누지 않아도 된다.

#### 여기 까지가 장고를 시작하기 위한 단계

---



- 어플리케이션 생성

  ```dj
  python manage.py startapp 앱이름 (복수형)
  ```

  - 해당 앱이름으로 폴더가 생성됨(앱폴더)
  - 바로 할일이 있따(안하면 1000퍼센트로 까먹음)
    - `settings.py` 에 내가 생성한 app을 등록해줘야함
    - installed.app에 가장 윗줄에 등록
    - language_code= ``ko-kr`` 왠만하면 소문자로
    - time-zone+:`Asia/Seoul` 앞에만 대문자

----

#### 이제부터는 서버를 동작하기 위한 단계

- MTV(MVC패턴)
  -  Model: 장고에서는 Model
  -  View:  장고에서는 Templete
  - Controller:  장고에서는 view

- **3대장: 우리가 가장 밀접하게 수정해야하는 파일명**

​	1.urls.py

​	2.views.py

​	3.templates(html등)

- url.py에서 해야할일
  - **path('url 패턴/', 실행이 되어야 하는 views에 있는함수.,해당 path의 별명)**
    - 많이 놓치는 부분: url 패턴뒤에 슬러쉬!!
- views.py에서 해야할일

  - 함수를 정의(첫번째 인자로 request 필수!!)

  - return은 꼭 필요

    - render: 주로 template과 함께 response할때 사용되는 함수

- template 에서 해야할일
  - 폴더명은 반드시  `templates` 인것을 확인

#### 여기까지가 기본 수정할 파일들 조작 방법

---

#### 여기서 부터는 본격 장고 동작 정의방법

- Template Variable

  - html 과 같은 template 에서 views.py 에서 준비한 변수를 가져다 쓰는 방법

  - render() 세번째 인자로 `{'key': value}` 와 같이 딕셔너리 형태로 넘겨 주면 Template에서 key 를 이용하여 value를 가져올 수 있다.

    ```django
    context= {'key': value}
    return rendeer(request, 'index.html', context)
    ```

    ```django
    {{ key }} 이렇게 value를 보여줄 수 있다.
    ```

    

- Variable Rounting(동적 라우팅)

  - url 주소 일부를 변수처럼 사용해서 동적인 주소를 만드는것

    주소요청 : `https://127.0.0.1:8000/hello/문자열`

    urls.py

    ```django
    path('hello/,<str(타입):name(저장되는 변수명)>/'.views.hello),
  ```
  
    - int: 숫자형식으로 받음.
  
      
  
    view.py
  
    ```django
    def hello(request, name(저장되는 변수명)):
    	print(name)
    	context = {
    		'name'=name,
    	}
    	return render(request, 'hello.html', context)
    ```
  
    template(hello.html)
  
    ```django
    <body>
    이름은: {{ name }} # context의 key의 값을 사용하면 value를 출력한다.
    </body>
    ```
  
    

- DTL(tag의 filter)

  - 로직을 표현할 때는 : `{% for %}`

  - 값을 표현할 때는 : `{{ }}`

  - 주석으로 나타내고 싶을 떄는: {#  #} or {%comment%} {%endcomment%}

    ```
      {% comment %} <h11>{{ i * 2}}</h11> {% endcomment %}
      <!--<h11>{#{ i * 2}#}</h11>-->
    ```

    

  - for 태그

    - 반복을 위한 태그

      ```django
      {% for 임시변수 in iterable 한 객체 %}
      {% endfor %}
      ```

      

    - for empty

      ```
      {% for 임시변수 in iterable 한 객체 %}
      	값이 하나라도 있으면 여기가 실행
      {% empty %}
      	출력한 값이 없으면 출력
      {% endfor %}
      ```

      

  - if 태그

    - 조건을 구분하기 위한 태그

    ```
    {% if 조건은 %}
    {% elif 조건문 %
    {% else %}
    {% endif %}
    ```

    

  

  - 나머지 기타 유용한 dtl 문서를 참고

    **검색: django built in template**

- Form

  - HTML form tag 의미

  - 입력 받은 데이터를 어딘가로 보낼때 사용

  - 입력받은 데이터를 어딘가로 보낼 때 사용

    ```html
    #action: 보내려는 목표 #method: http method(get, method)
    <form action=""> 
        #오락실 버튼
        <input type="button"> 
        #미사일 버튼 (데이터를 acion으로 전송)
        <input type = "submit">
        		or
        <button></button>
    </form>
    ```

    - action에 들어가는 목표 url 설정 주의 사항!

      ```django
      action="/cathch/"
      =>127.0.0.1:8000/catch?name=asdf
      현재주소: 127.0.0.1:8000/index
      action="cathch/"
      =>127.0.0.1:8000/index/catch?name=asdf
      ```

      

---

