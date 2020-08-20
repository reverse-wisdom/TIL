### Field lookups

- 구글링 키워드: `django queryset`
- `필드명__필드룩업`

- `exact`: 대소문자 전부 일치해야함.
- `iexact`: 대소문자 상관없이 일치하면 됨.
- `contains`: 해당 글자가 어느 위치에 있던 상관없이 포함되어 있으면 됨.
- `startswith`: 해당 글자로 시작
- `endswith`: 해당 글자로 끝나는 것만

- `gt`/`gte`/ `lt`/ `lte` : 비교연산자

#### **실습**

- 제목이 first이고 한개만 가져와라.(여러개의 데이터가 있는데 하나만 가져오고 싶을 때)

  ```django
  #1
  Article.objects.filter(title='second').first()
  #실행결과
  <Article: second>
  
  #2
  Article.objects.filter(title='second')
  #실행결과
  <QuerySet [<Article: second>]>
  ```

  

​	- 해당 모델 클래스로 값이 리턴

- 정렬을 하고 싶을때 (오름차순/내림차순)

  ```dj
  #오름차순
  Article.objects.order_by('title')
  #실행결과
  <QuerySet [<Article: first>, <Article: second>, <Article: third>]>
  #내림차순
  Article.objects.order_by('-title')
  #실행결과
  <QuerySet [<Article: third>, <Article: second>, <Article: first>]>
  ```

  

- QuerySet으로 리턴을 받았을 때

  - QuerySet은 List와 유사함
  - 인덱싱/ 슬라이싱

  ```django
  #인덱싱
  Article.objects.all()[2]
  #실행결과
  <Article: third>
  
  ※ Article.objects.all()[-1] #지원하지 않음
      
  #슬라이싱
  Article.objects.all()[:2]  
  #실행결과
  <QuerySet [<Article: first>, <Article: second>]>
      
  ```



## Templates 확장 사용하기



**step1. base.html 생성하고 원하는 위치에 templates 폴더안에 위치 시킨다.**

1base.html 에는 기본 html DOM 트리를 구성한다.

2boostrap CDN을 복붙해준다

3block 을 body 안에 적절한 곳에 위치 시켜준다

**step2.setting.pyd에 base.html의 경로를 등록한다.**

- TEMPLATES 라는곳에 있는 DIRS에 그 경로를 추가한다
- `base.html` 이 있는 경로를 BASE_DIR로 부터 설정해주면됨
- 'DIRS' : [BASE_DIR / 'workshop_sol'/'templates']: Django 3.xx 등록방식
- 'DIRS':[os.path.join(BASE_DIR,'workshop_sol', 'templates')]:  Django 2.xx등록방식

BASE_DIR: c/aclass/Django/0820/0819_workshop



**step3. 확장하고 사용한다.**

	1. 가장 첫번째 줄에 {% extends 'base.html' %}을 해준다
 	2. 그 다음 block 을 위치 시키고 block 안에 적절히 꾸며주면된다

---

## **CRUD**

### Read

- DB에 전체 글목록을 가져와서 page에 보여주자!

- Article.objects.all()의 QuerySet을 그대로 context에 담아서 template 파일에 전달
- template은 for 문으로 하나씩 db값을 접근 가능하고, 연산자를 이용해서 값에 접근도 가능

### Create

- form 태그에서 데이터를 전달하고

- 그 데이터를 3가지 방법 중 1개의 방법으로 DB에 저장하면 끝

- GET/POST

  - GET: 주소줄에 쿼리스트링 형식으로 데이터가 전달, (255자가 최대), 전달하는 길이가 한계가 있음

    - 주로 데이터 정보를 가져올 떄 사용 (즉, 데이터를 조회할 때 이용 )

    

  - POST: 패킷 바디안에 데이터가 저장되서 전달, 좀 더 많은 양의 데이터를 전달할 수 있음

    - 주로 데이터의 정보를 생성, 수정, 삭제할 때 사용

  - GET/article/: article의 정보를 조회
  - POST/article/: article을 생성
  - POST/article/1/: article을 수정하겠다
  - REST API: 나중에 수업할 예정

  

- method를 POST로 변경할 떄 해야할 일!
  - CSRF: Form tag 사이에 {% csrf_token %} 추가
  - request.GET을  request. POST로 변경
- Redirect() : 이미 만들어진 페이지로 경로 재설정.





### **Update**

- 글 제목을 클릭했을 때, 
- detail 페이지를 먼저 만들자!
  - 어떠한 글의 detail 페이지인지 해당 글의 정보(pk)가 필요함.
  - 글의 정보를 동적 라우팅 방법으로 주소로 전달
  - 주소로 전달 받은 글의 pk 값을 가지고 db에서 데이터를 가져옴
  - 가져온 데이터를 tempalte 파일에서 보여주면 그것이 detail page!

- detail 페이지하단에 수정하기 링크를 만들어준다.
  - 수정하기 링크는 edit 하는 페이지를 보여주면된다.
  - create 방법과 유사하게 form을 보여주는데
  - 차이점은 해당글의 data를 같이 넘겨주고 그 데이터를 같이 보여주는게 차이점.
  - 수정하기 최종 버튼을 눌렀으면 post 방식으로 DB에 적용
  - 이때 필요한 정보도 주소 줄을 이용해서 전달한다

- DB에 적용시키는 방법은
  - 해당 PK를 가지는 데이터를 불러오고
  - 값을 수정하고
  - save 한다

- 끝나면 detail page로 redirect 시키면 끝!





### **DELETE**

- 삭제하기 버튼을 누르면 삭제할 글의 pk각 같이 주소로 전달되고
- views.py 에서 해당 pk값의 정보를 가져온 다음에 delete 함수를 호출하면 끝.
- 