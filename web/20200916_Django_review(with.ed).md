

### CRUD의 연장선

- 장고에서 만들어준 USER모델을 사용
- 장고에서 만들어준 FORM 사용
- 그래서 외울게 좀 있음(import)
  - 기억이 나지 않으면 DJ DOC 찾아보자.



오늘 라이브에서 가장 처음 했던것.



- accounts 라는 앱을 생성
  - 동일하게 url 분리
  - models.py는 장고에서 제공하는 USER 사용하기 때무에 따로 정의는 하지 않음
  - form도 장고에서 제공하는 form을 사용하기 때문에 따로 정의하지 않음
    - but,  곧 custom 해야함

- 회원가입

  - Authentication(인증): 신원확인, 유저가 나는 여기 회원이다 라고 신원을 확인
  - Authorization(권한, 허가): 권한을 부여

  - 회원가입 => 새로운 유저를받겠다 => 유저정보를 받아서 DB에 생성(CREATE)

    - UserCreationForm: 장고 제공폼

      - 입력 받은 USER 정보를 최종적으로 DB에 저장

      - ModelForm

        ```python
        from djnago.contrib.form import UserCreationForm
        
        def signup(request):
            if request.method == "POST":
            	form = UserCreationForm(request.POST)
            	if form.is_valid():
            		form.save()
            		return redirect('articles:index')
            else:
                form = UserCreationForm()
            context = {
               'form':form,
            }
            
            return render(request, 'accounts/signup.html', context)
        
        ```

        



- 로그인

  - 새롭게 세션을 만드는 동작(CREATE)

  - 쿠키

    - 브라우저에 저장이 되는 내용

    - Key -Value의 작은 데이터파일

    - 만료날짜, 경로정보

    - 쿠키가 세션보다 속도가 빠름

    - 보안은 세션이 더 조음, 쿠키는 브라우저에 저장이 되기떄문에 타인이 볼 수 있음

    - 종류

      - 세션쿠키
        - 쇼핑몰 장바구니
        - 브라우저를 닫으면 삭제됨

      - 지속쿠키
        - 24시간 동안닫기, 로그인 이름 유지
        - 로컬에 저장이 되서 컴퓨터를 재시작해도 남아 있음

  - 세션
    - 서버의 DB,메모리
    - 특정 사용자의 중요한 정보
    - 사용자가많아지면 서버메모리를 많이 쓰게 되서 정말 중요한 정보만 저장 

  - 세션에 담긴 유저 정보가 특정 브라우저를 사용하는 유저가 맞는지 혹인하기 위해서

    세션 키(ID)를 쿠키에 전달을 해줌

  - 브라우저에서 쿠키를 삭제한다면?
    - 서버는 해당 브라우저의 유저가 누구인지 확인 할 수 없게됨 
    - 새롭게 로그인해서 새로운 세션키를 발급받앙함, 쿠키 새롭게 생성됨

  

  - AuthenticationForm
    - 장고에서 제공해주는 폼
    - 로그인에 필요한 정보를 받아서 유효성 검사하고 회원인것도 확인
    - 따로 DB에 저장하는것이 아니어서 Form
    - Form 
    - 첫번째 인자로 `request` 확인

  - 실질적으로 로그인을 하는 함수는 장고에서 제공해주는 login 함수

    - 회원임이 확인되면 세션을 생성

      ```python
      # views.py
      from django.cotrib.auth.form import AuthenticationForm
      from django.cotrib.auth import login as auth_login
      def login(request):
          if request.method == "POST":
          	form = AuthenticationForm(request, request.POST)
              if form.is_valid():
                  auth_login(request, form.get_user()) #장고에서 제공해주는 함수
                  return redirect('article:index')
              
          else:
              form = AuthenticationForm()
          context = {
      		'form' = form,
          }
          return render(request, 'accounts/login.html', context)
              
             
      ```

      

---

- 접근제한

  - request에 로그인 정보가 들어있음, user

  - request.user

    - is_authnticated: 로그인여부

    - is_superuser: 관리자인 아닌지여부
    - is_anonymous: 로그아웃여부

  - 데코레이터

    - login_required

      ```python
      from django.contrib.decorators import login_required
      @login_required:
      def update(request):
          ....
      ```

      - 로그아웃상태에서 update로 접근을 했다.
        - /account/login/?next=/accounts/update/ 로 주소가 나타는 것을 확인 가능
        - 이 주소 형식은 전형적인 GET 타입의 querystring
        - request.GET.get("next") 하면 /accounts/update/를 획득할 수 있음
        - redirect(request.GET.get("next") or 'articles:index')로 이동할 수 있음

---

- 회원탈퇴

  - urls.py 를 정의한다. 회원탈퇴 요청이 들어오면 views에서 함수를 실행하게 정의

  - views.py에서 삭제하는 함수를 정의

    - 회원가입 => DB에서 유저정보를 생성
    - 회원탈퇴=> DB에서 유저정보를 삭제
    - 유저정보를 delete() 실행하면 삭제됨
      - 유저 정보는 어디에?
        - request.user에 있음
        - request.use.delete() 하면 db에서 삭제됨

    - 여기에서 생각해보면 로그인 하지 않은 유저가 요청을 하면 되지 않음
    - 로그인 되었을떄만 회원 탈퇴하게끔 is_authenticated로 접근제한

---

- 회원 정보 수정

  - UserChangeForm 사용

    - User DB를 수정

    - 사용을 했떠니?

    - 일반 유저는 대박.

      - 내가 나를 최고 관리자로 만들 수 있다!!

         = > UserChangeForm을 그대로 사용하면 서비스 망..

  - Custom해서 사용해야함

    - forms.py 에서 CustomUserChangeForm을 정의

      - UserChangeForm을 상속을 받아서 정의

        ```python
        from django.contrib.auth.forms import UserChangeForm
        from django.contrib.auth import get_user_model
        class CustomUserChangeForm(UserChangeForm):
            class Meta:
                model = get_user_model()
                fields= ['email', 'first_name', 'last_name']
        ```

        