

> ## 201006 pjt06 README



### [진행과정]

어제 프로젝트와 연결되서 진행되어야 하는 부분이라 오늘도 파일을 내가 메인으로 맡기로 했는데 어제 

진행한 부분에서 navbar가 전체리뷰에서만 적용되고 다른페이지에서는 적용안되어, labssafy 파일로 받아서 프로젝트를 진행했다 오전에는 M:N 모델 추가된 부분을 반영했고, 오후에는 스타일링에 집중을 했다.

### [어려웠던 점]

1) block과 inline 요소들의 특징과  관련된 태그들 배운지 오래되서  이번 프로젝트를 통해 시행착오를 여러번 느끼면서 다시 복기하게 되었다 

2) 배치가 원하는 대로 되지 않아서 답답했다. d-flex, justify-content-center,  박스에 auto 넣는 부분들

정렬을 하는 방법이 여러방법이 있지만 언제 어디서 어떻게 쓰이는지 헷갈렸다.



### [후기]

아쉬웠던점은, 클라이언트입장에서 UI가 얼마나 직관적으로 보여질지에 초점을 두다보니 navbar에만 초점을 둔 나머지 기능 구현에 대해서 신경을 많이 못써서 아쉬웠다. 시간이 남았으면 게시글에서 프로필에 유저 이미지를 보이게 하거나, 리뷰작성시 드롭다운기능으로, 장르(복수선택)나, 성별, 나잇대를 선택해서 게시글을 작성할수있게끔하고 전체리뷰에서 해당 내용을 보이게해서 유저가 전체리뷰페이지를 볼떄 대략적인 취향에 맞게 리뷰를 보게끔 만들고 싶다는 아쉬운 맘이 남았고, 오늘 프로젝트는 싸피들어오면서 제일 재미있었던 날이었다. 개념이 흐릿하게 안 상태에서, 이리저리 시행착오를 겪으면서 마지막에 원하는 페이지가 렌더링 될때 그 보람이 무엇보다 알찼고 이 맛으로 FE를 하는가? 하는 생각이 들었다. 앞으로 배울 vue와 ,js가 기대된다.





### [코드구현]

<models.py>



```python
class Review(models.Model):
    title = models.CharField(max_length=100)
    movie_title = models.CharField(max_length=50)
    rank = models.IntegerField()
    content = models.TextField()
    image = models.ImageField(blank=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    like= models.ManyToManyField(settings.AUTH_USER_MODEL, related_name='like_reviews')
```

```
like= models.ManyToManyField(settings.AUTH_USER_MODEL, related_name='like_reviews')

user는 여러 리뷰에 좋아요를 누를 수 있고, review는 여러 유저로부터 좋아요를 받을 수 있게끔
하기위해 ManyToManyField M:N 관계인 모델을 정의
```



```HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" integrity="sha384-JcKb8q3iqJ61gNV9KGb8thSsNjpSL0n8PARn9HuZOnIxN0hoP+VmmDGMN5t9UJ0Z" crossorigin="anonymous">
  <script src="https://kit.fontawesome.com/eb3d7ba0fe.js" crossorigin="anonymous"></script> 
  <link href="https://fonts.googleapis.com/css2?family=Jua&display=swap" rel="stylesheet">
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
  />  

  <title>Document</title>
</head>
<body style="font-family: 'Jua', sans-serif;">
  
  <nav class="nav nav-pills nav-fill bg-info justify-content-around py-4" style="font-size: 1.5rem;">
    <div>
    
    <span style="font-size: 2em; font-color: tan;">
      <i class="fas fa-film text-white"></i>
    </span>
    
    <h4 class="text-white mb-4" style="bold; font-size: 3rem;">[ SSAFY 영화리뷰 커뮤니티 ]</h4>
    <h4 class="text-white" style="font-color:tan;">Hello, {{ user.username }}</h4>
    </div>
    {% if request.user.is_authenticated %}
    <li class="align-center">
     <i class="far fa-user justify-content-center text-white"></i><a class="nav-link text-white" href="{% url 'accounts:profile' request.user.id %}"> ｜ My Profile </a>
    </li>
    <li>
      <i class="fas fa-users text-white"></i><a class="nav-link text-white" href="{% url 'community:index' %}">｜ Community </a>
    </li>    
    <li>
      <i class="far fa-plus-square text-white"></i><a class="nav-link text-white" href="{% url 'community:create' %}">｜ New Review </a>
    </li>  
    <li>
      <i class="fas fa-sign-out-alt text-white"></i>
      <form action="{% url 'accounts:logout' %}" method="POST">
        {% csrf_token %}
        
        <input type="submit" class="btn btn-sm bg-info text-white "  style="font-size: 1.5rem;" value="｜ Logout">
      </form>
    </li>  
```

```P
  <script src="https://kit.fontawesome.com/eb3d7ba0fe.js" crossorigin="anonymous"></script> 
  -> navbar에 아이콘은 fontawesome 활용
  
  <link href="https://fonts.googleapis.com/css2?family=Jua&display=swap" rel="stylesheet">
  -> 글씨체는 googlefont활용
  
```

