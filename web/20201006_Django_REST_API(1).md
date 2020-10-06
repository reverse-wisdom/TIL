> ### \DRF 

- REST
- URI + http method -> JSON
- URI:  자원정보
- http method: 행위정보
- =

---

- django, django-seed, djangorestframework 설치

- 뒤에꺼 두에꺼는  앱등록해줘야함(django_seed, rest_framwork로등록)

---

urls.py(boards)

```python
from django.urls import path
from . import views

app_name = 'boards'
urlpatterns = [
    path('boards/', views.board_list_create, name='board_cr'),
    path('boards/<int:board_pk>/', views.board_detail_update_delete, name='board_rud')
    path('boards/<int:board_pk>/comments/', viewes.comment_create, 		             name='comment_create'),
   	path('comments/', viewes.comment_list, 		             name='comment_list'),
	path('comments/<int:co mment_pk>/', views.comment_detail_update_delete, name='comment_rud'),
]
```





<models.py>

```python
class Board(models.Model):
	title=models.CharField(max_length=200)
	content=models.CharField(max_length=200)
    created_at = models.DateTimeField(auth_now_add=True)
    updated_at= models.DateTimeField(auto_now=True)
    
```



<serializers.py>

```python
from rest_framework import seralizers
from .models import Board

class BoardListSerializer(serializers.ModelSerializer):
    class Meta:
        model =Boar:
        fields = ['id', 'title',]
        
class CommentListSerializer(serializers.ModelSerializer):
    class Meta:
        model=Comment
        fields= ['id', 'content','board']
        read_only_fields= ['board',]
        
class BoradSerializer(serializers.ModelSerializer):
   # nested serializer
    comment_set =  CommentListSerializer(many=True, read_only=True) 
   # serialize fields 참고 (get_absolue_url->docs 초코몽키참고)
    comment_cnt= serializers.IntergerField(soruce='comment_set.count',read_only=True)

    
    #views.py 차이점은 many=True만 있음, 데이터를 받아서 요청하는게 아니고 읽기만하는거라서
    
    class Meta:
        model= Board
        fields = '__all__'
        read_only_fields= ['comment_set', 'comment_cnt']
        
# 순서를 바꾸고 싶을떄(댓글이 아래로)
	#['id', 'title','content','created_at','updated_at','comment_set',]
#comment_set
	# 게시글에 대한 댓글 볼때는 역참조이므로 보여질 모델이름_set

class CommentSerializer(serializers.ModelSerializer):
    class Meta:
        model=Comment
        fields= '__all__'
        read_only_fields= ['board',]
        
        
        #read_only_fields= ['board',]
        #input 받는 데이터가 아니라 정해둔 값이라서 유효성 검사를 하지 않기 위해서
        #read_only_fields를 정해줌
        #외부데이터를 넣을떄 유효성검사 pass

        
```

필드 할당할때 튜플은 끝에 꼭 콤마찍어야함

## CREATE, READ

**READ **

1. db에서 data가져오기
2. Serializer로 data 직렬화
3. response
4. @api_view

```python
@api_view(['GET','POST'])
def board_list_create(request):
	#CREATE
    if request.method == 'POST':
		serializer= BoardSerializer(data=request.data)
        if serailizer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data, status 
                            = status.HTTP_201_CREATED)
    #READ
    else:
        boards= Boad.objects.all()
        serializer=BoardSerializer(boards, many=True)
        return Response(serializer.data)
```

- request.data: POST보다 유연하게 사용가능(PUT, FILES,POST 다 받을 수 있음), drf에서만 지원

- raise_exception: 유효성검사를 통과하지 못했을떄, False인경우(기본값) 에러페이지 보여줌

  True이면 에러내용을 담은 JSON을 반환해줌

- status: 어떠한 작업을 했는지 더 자세하게 추가정보를 알려줌

## DETAIL, UPDATE, DELETE

1. db에서 data 가져오기
2. Serializer에 어떤데이터를 넣어줄건지, 인스턴스만들기
3. Response

---

한개만 가져오기 때문에 many =True 없음



```python
@api_view(['GET','PUT','DELETE'])
def board_detail_update_delete(request, board_pk):
	board = get_object_or_404(Board, pk=board_pk)
    if request.metho=='PUT':
        serializer= BoardSerializer(instance=board, data=request.data)
        if serializer.is_valid(raise_exception.True):
            serializer.save()
            return Response(serializer.data)
    elif request.metho=='DELETE':
        board.delete()
        return Response({'id':board_pk}, status=status=HTTP_204_NO_CONTENT)
    else:
		serializer =BoardSeriaizer(board)
        return Response(serializer.data)
    
        
```



---

## Comment CRUD

models.py

```python
class Comment(models.Model):
    board =models.ForeignKey(Board, on_delete=modeld.CASCADE)
	content=models.CharField(max_length=200)
    created_at = models.DateTimeField(auth_now_add=True)
    updated_at= models.DateTimeField(auto_now=True)
    
```

C

```python
@api_view(['POST'])
def comment_create(request, board_pk):
    board_data= get_object_or_404(Board, pk=board_pk)
    # 1. 어떤 데이터를 저자할지 받아와서 Seralizer 인스턴스를 생성
    serializer = CommentSerializer(data=request.data)
    # 2. 유효성 검사
    if serializer.is_valid(raise_exception=True):
    # 3. 통과하면 저장
    	serializer.save(board=board_data) 
        # 기존 form에서는 commit으로 했는데, drf에서는 키워드인자로 할당
        # 뒤에 이어서 추가할 수 있음
    # 4. Response에 정보를 담아섯 저장
    	return Response(serializer.data, status=status.HTTP_201_CREATED)
```



comment input정보(request 데이터)에는 board가 없어서 별도로 추가 저장해야함



![image-20201006103453034](C:\Users\OFFICE\AppData\Roaming\Typora\typora-user-images\image-20201006103453034.png)

```python
def comment_list(request):
	comments= Comment.objects.all()
    serializer = CommentSerializer(comment, many=True)
    return Response(serializer.data)
```



### comment  Detail update delete

```python
@api_view(['GET','PUT','DELETE'])
def comment_detail_update_delete(request, comment_pk):
    # 1. 정보를 가져온다
    comment = get_object_or_404(Comment, pk=comment_pk)
    if request.method == "PUT":
        #2.수정한 정보를 직렬화 한다
        serializer = CommentSerializer(instance=comment, data=request.data)
        #3. 유효성 검사후 저장
        if serializer.is_valid(raise_exception=True):
        	#4. 정보 리턴
            serializer.save()
            return Response(serializer.data)
   	elif request.method=="DELETE":
        #정보를 삭제한다
        comment.delete()
        # 삭제된 정보를 리턴한다
        return Response({'id':comment_pk}, status=status=HTTP_204_NO_CONTENT)
    else:
        # 2. 정보를 직렬화해서 인스턴스를 만든다
        serializer = CommentSerializer(comment)
        # 3. 정보를 리턴한다
        return Response(serializer.data)
        
```

