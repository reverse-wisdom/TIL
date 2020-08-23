

**1.장고설치: pip install django**
**2.프로젝트생성:django-admin startproject first_project**
**3.앱생성:python manage.py startapp articles**
**4.서버실행python manage.py runserver**
**5.템플릿확장: templates > base.html 생성**

- base.html

  - bootstrap cdn 삽입

  - {% block content %} {% endblock %}

    ```html
    #block tag
    하위 템플릿에서 재 지정(overriden)할 수있는 블록을 정의
    하위 템플릿이 채울 수 있는 공간
    ```

- 사용할 html

  - {% extends 'base.html' %}

    ```html
    #extends tage
    1. 이(자식) 템플릿이 부모 템플릿을 확장한다는 것을 알림
    2. 반드시 문서의 최상단에 위치해야 한다.
    ```

    

  - {% block content %} {% endblock %}

    ```html
    #block tag
    하위 템플릿에서 재 지정(overriden)할 수있는 블록을 정의
    하위 템플릿이 채울 수 있는 공간
    ```



**6.환경설정**
	setting.py
	1)INSTALLED_APPS = [
	2)DIRS : [BASE_DIR / 'workshop_sol'/'templates']

**7.models.py**

​	1) 모델정의

```python
from django.db import models

class Article(models.Model): 
    # Article이 models 모듈 안에 있는 Model 클래스 상속받음
    title = models.CharField(max_length=200)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    def __str__(self):
        return self.title
```



​	2) 설계도 작성 및 DB 반영(처음 작성후 변경사항 발생시 (생성 / 수정) 꼭 해줘야하는 작업)

```python
python manage.py makemigrations
```

```python
python manage.py migrate
```



**8.urls.py **

**※(메인) 콤마, include확인**

​	1)from articles import views

​	2)분리시 include 삽입

​	3)url 추가시

```python
 #형태
    
 path('index/', views.index),
 path("<int:pk>/", views.detail, name="detail"),
 path("<int:pk>/edit/", views.edit, name="edit"),

```

```python
type 뒤에 있는 변수명은 views.py 에서 함수 매개변수를 말함
```



**8-1 url.py(앱내부)**

```python
from django.urls import path
from . import views 
app_name = "앱이름"
```



**9.views.py**

​	1) redirect import



**10.templates**

**템플릿 분리**

- ```python
  ├── articles
  │   ├── templates
  │   │   └── articles
  │   │       ├── catch.html
  │   │       ├── dinner.html
  │   │       ├── dtl_practice.html
  │   │       ├── hello.html
  │   │       ├── index.html
  │   │       └── throw.html
  
  ```

  

  1.form	

  ```html
  action —> 입력 데이터가 전송될 URL 지정
  method —> 입력 데이터 전달 방식 지정
    get:서버의 데이터나 상태를 변경 시키지 않아야 하기 때문에 조회(html)를 할 때 사용
  ```

  2.url 이름 활용법

  ```html
  action="{% url '{앱이름:url이름}' %}"
  ```

**11.Admin(admin.py)**

```python
$ python manage.py createsuperuser
```

```python
from django.contrib import admin
from .models import Article # 명시적 상대경로 표현

admin.site.register(Article)

```







---

### **Django DB API**

django가 기본적으로 orm을 제공함에 따른 것으로 db를 편하게 조작할 수 있도록 도와줌

1. 환경셋팅

   1)

   ```python
   pip install ipython django-extensions
   ```

   2)

   ```PY
   # settings.py
   
   INSTALLED_APPS = [
       ...
       'django_extensions',
       ...
   ]
   ```

   3)

   ```python
   python manage.py shell_plus
   ```

2. 구문

   ```PY
   Article.objects.all()
   =classname.managet.querysetAPI
   ```

   

---

> ### CRUD



### 1.Create

```python
article = Article() :  클래스로부터 인스턴스 생성
```

 1) 첫번째방식

```python
article.title = 'first' # 인스턴스 변수(title)에 값을 할당
article.content = 'django!' # 인스턴스 변수(content)에 값을 할당
article.save()
```

2) 두번째방식

```python
article = Article(title='second', content='django!!')
article.save()
```

3)세번째 방식

```python
Article.objects.create(title='third', content='django!')
```



### 2.Read

`all()`

```python
>>> Article.objects.all()
<QuerySet [<Article: Article object (1)>, <Article: Article object (2)>, <Article: Article object (3)>, <Article: Article object (4)>]>
get()

```

`get()`

- 객체가 없으면 DoesNotExist 에러가 나오고 객체가 여러 개일 경우에 MultipleObjectReturned 오류를 띄움.
- 위와 같은 특징을 가지고 있기 때문에 unique 혹은 Not Null 특징을 가지고 있으면 사용할 수 있다.

```python
#없을때
>>> article = Article.objects.get(pk=100)
DoesNotExist: Article matching query does not exist.

#없을때    
>>> Article.objects.get(content='django!')
MultipleObjectsReturned: get() returned more than one Article -- it returned 2!
**filter()**


```



`filter()`

```python
>>> Article.objects.filter(content='django!')
<QuerySet [<Article: first>, <Article: fourth>]>

>>> Article.objects.filter(title='first')
<QuerySet [<Article: first>]>

```





## 3.Update

```python

```

