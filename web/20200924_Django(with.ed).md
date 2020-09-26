## Custome User



```python
# accounts/models.py

class User(AbstractUser):
    pass
```



- AbstractBaseUser

- AbstractUser

```python
#settings.py
AUTH_USER_MODEL ='accounts.User' #str 형태!
```



- 기존 DB삭제

- makemigrations

- migrate





## Custom User를 했을 시 수정되어야 하는 Form

- user를 모델로 하는 모델폼들을 수정해야함

- 제공되는 user관련 모델폼은 auth.User(Django에서 제공해주는 User 클래스)를 model 정보로 가지고 있기 때문

- UserCreationForm/UserChangeForm

  ```python
  # account/forms.py
  
  class CustomUserCreationForm(UserCreationForm):
  	class Meta(UsercreationForm.Meta):
  		model = get_user_model()
          fields = UserCreationForm.Meta.fields + ('email') #튜플형태로 추가
  ```

  



- get_user_model()
- - return 유저 클래스
  - models.py를 제외한 모든 곳!

- settings.AUTH_USER_MODEL

  - return 유저 클래스 문자열(str)

  - model.py에서 사용

---

User -Article(1:N)

User-Comment(1:N)

```python
artilces/models.py

class Article/ class Comment
	user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=CASCADE)
    
```





원인) 

1. 비로그인으로 POST요청 

2. login_required 로 인해서 `accounts/login/` 으로 이동 (POST 요청에 대한 내용이 상실 http는 현재상태를 저장 x)

3. login 진행

4. login 함수의 redirect부분에서 request.GET.get('next')에 저장된 delete경로로 다시요청(GET방식)
   - redirect는 함수 GET 방식으로 주소요청
5. require_POST 때문에 405 Methon not Allowed status code가 발생함.

해결방법

- POST  method로 처리
- 인증되지 않은 사용자는 메인페이지.

```python
@login_required
def delete(request, pk):
	article = get_object_or_404(Article, pk=pk)
    if request.method == "POST":
        article.delete()
    return redirect('article:index')
```



```python
@login_required
def delete(request, pk):
    if request.user.is_authenticated:
        article = get_object_or_404(Article, pk=pk)
        article.delete()
    return redirect('article:index')
```

