

# **Model**

- db에서 데이터를 저장하고 가져오는 것

- s



> ## CharField()

- 길이의 제한이 있는 문자열을 넣을 때 사용
- max_length가 필수 인자
- 필드의 최대 길이, 데이터베이스와 django 유효성검사에서 사용

> ## TextField()

- 글자의 수가 많을 때 사용

> ## DateTimeField()

- 최초  생성 일자: `auto_now_add=True`

  - django ORM이 최초 데이터 입력시에만 현재 날짜와 시간으로 갱신
  - 테이블에 어떤 데이터를 최초로 넣을 때

- 최종 수정 일자 `auto_now=True`

  - django ORM이 save를 할 때마다 현재 날짜와 시간으로 갱신

  

**IntegerField, BooleanField 등등 있음**

**Django 공식문서 Model field라고 구글링하면 찾을 수 있음**

---

## Migrations

#### **makemigrations**

`python manage.py makemigrations [앱이름]`

- 모델을 변경한 것에 기반한 새로운 마이그레이션(설계도)을 만들 떄 사용
- 모델을 활성화 하기전에 DB 설계도를 작성
- 생성된 마이그레이션 파일은 데이터베이스 스키마를 위한 버전관리 시스템이라고 생각
- app 이름을 뒤에 적으면 app에 있는 model.py의  내용만 설계도를 만듬

#### **migrate**

`python manage.py migrate [앱이름]`

- 작성된 마이그레이션 파일들을 기반으로 실제 DB에 반영
- db.sqlite3라는 데이터베이스 파일에 테이블을 생성
- 모델에서의 변경 사항들과 DV의 스키마가 동기화를 이룸
- app이름을 적으면 해당 app에 있는 migration 파일을 db에 적용 시킴

#### **sqlmigrate**

- 해당 마이그레이션 파일이 SQL 문으로 어떻게 해석되어서 동작할지 미리 확인하기 위한 명령어

#### **showmigrations**

- 마이그레이션 파일들이 migrate여부를 확인하기 위한 명령어

---

### DB 사용

- DB api

  ```django
  모델클래스이름.objects.QuerSetAPI
  Article.objects.all()
  #objects: s를 내비두고 놀지 말자, 항상같이 델꼬 다니자 
  ```

  

#### **Model의 중요 3단계**

1. models.py:변경사항(작성, 수정, 삭제...) 발생
2. makemigrations: 설계도 만들기
3. migrate: DB에 적용