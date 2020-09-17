> # CRUD

---

프로젝트 이름: afterschool

앱이름: gumi

---





## ▣ 준비단계

1. master가 보이는경우

OFFICE@OFFICE MINGW64 ~/Desktop/SSAFY_fourth/class/django/online-coaching/Django_OC/bc_0915

**(master)**

---

->git에서 사용  **branch명**



2. venv 가 보이는 경우

**(venv) **

OFFICE@OFFICE MINGW64 ~/Desktop/SSAFY_fourth/class/django/online-coaching/Django_OC/bc_0915

---

-> 가상환경 설정





1. 가상환경 설정

   ```python -m venv venv```

   ```source venv/Scripts/activate``` # 가상환경 수동설정

   (또는 F1->venv 선택)

   `pip list` # package 깨끗한지 보기



2. 장고설치

   `pip install django`



3. 패키지 묶음 박제 및 설치

   - `pip freeze > requirements.txt`  # 파일을 배포하는 입장

     일일히 어떤 패키지를 사용해야하는지 한번에 알수 있고 명령어를 통해서 해당 파일을 실행하기위한 

     패키지모음을 한꺼번에 설치할 수 있음 상기 명령어는 해당 파일을 실행하기위한 패키지를 갱신?박제하WJ는거임

   - `pip install -r requirements.txt` #배포한 파일을 받아서 사용하는 입장

     배포한 파일의 패키지를 한꺼번 설치하는 방법

4. 프로젝트 생성

   `django-admin startproject afterschool`

5. 서버 실행시키기(함정)

   `python manage.py runserver`

   -> 에러발생 현재 카테고리 확인

6. 카테고리 이동

   `ls` -> `manage.py`  있는지 확인, 없으면

   `cd afterschool` (afterschool로 가세요)



![image-20200916005614276](C:\Users\OFFICE\AppData\Roaming\Typora\typora-user-images\image-20200916005614276.png)





 7.앱생성 및 등록

​	**생성**

​	`python manage.py startapp gumi`

​	**등록**

​	`settings.py` : **`'gumi'`**(INSTALLED_APPS)

​	**언어/시간**

​	언어: **en-us**(에러났을때 영어로 설정해놓으면 찾기쉬움) or **ko-kr**

​	시간: Asia/Seoul



8.url 분리

​	[1] 프로젝트 urls.py 에서 분리

​		1) `include` 삽입

​			- `from django.urls import path, include`

​		2) 앱 url 분리(1차)

​			- `path('', include('gumi.urls'))`,

​	[2]  앱 url (*gumi*) 생성

​		1)모듈 import 2) 앱변수 생성 3) urlpatterns 만들기

```python
from django.urls import path

app_name = 'gumi' 
urlpatterns = [

]

```



9.base.html 생성 

​	[1]위치

​		1) 프로젝트 폴더 밑에 or 2) 프로젝트폴더-프로젝트폴더(settings.py랑 나란하게)

​	[2] !+ 탭

​		bootstrap CDN 삽입

​		1) head안에 한개, 2)body에 3줄

​	[3] div 태그, 클래스는 container

​	[4]title은 Gumi AS



10. 템플릿 등록

    1) **settings.py**

    ​	TEMPLATES / DIRS (55번째줄)

    ```python
    'DIRS': [BASE_DIR / 'templates'],
    ```

    

## ▣ Model

1. model data 생성

```python
class Student(models.Model): #상속
    name = models.CharField(max_length=20)
    age = models.IntegerField()
    address = models.TextField()

    created = models.DateField(auto_now_add=True)
    updated = models.DateField(auto_now=True)
     
```

 2. 설계도 작성

    ```python manage.py makemigrations```

3. 설계도에 데이터 넣기

   `python manage.py migrate`



## ▣ admin

목적 : admin 사이트를 Student 데이터베이스 테이블 접근가능 (수정, 생성, 삭제)

```python
from django.contrib import admin

from .models import Student
# Register your models here.

admin.site.register(Student)
```

- 관리자 페이지를 입장하기 위해 계정 생성

  `python manage.py createsuperuser`

- 웹페이지 접속 admin/
  - 데이터 3개만들기

- 데이터를 나타내는 걸 객체로 말고 이름으로 나타낼려면

  `models.py`

  ```python
  class Student(models.Model):
      name = models.CharField(max_length=20)
      age = models.IntegerField()
      address = models.TextField()
  
      created = models.DateField(auto_now_add=True)
      updated = models.DateField(auto_now=True)
  
      def __str__(self):
          return self.name
  ```



## ▣ Urls-Views-Templates

![image-20200916234427617](20200915_Django_review(form, static, media, with.ed).assets/image-20200916234427617.png)

```python
{% url 'gumi:add' %} 
앱이름 구미안에 있는 urls.p에서(app_name) name이 add인 url로 이동
```



