> ### 201007. < PJT05 > README

---

### [진행과정]

지난 프로젝트에서는 현준이가 메인으로  진행해서 이번에는 내가 세미 아바타가 되어 메인역할을 진행했다. 그전처럼 중간에 우여곡절이 많았지만 현준이가 네비게이션 역할을 톡톡히 해줘서 초중반까지는 무리없이 잘진행되었다.하지만 후반부로 오면서 리뷰 수정 부분과 base.html 이 원하는대로 구현되지 않아 애를 먹었으나. edwin님의 스스로 고민하고 해결할 수 있게하는 발전적이 힌트와, 이전 정규 수업때 진행했던 코드를 살짝 참고해서 마지막에는 기능상에는 문제(?) 없도록 구현하였다. 

### [어려웠던점 및 후기]

1) 정규수업때는 form 과  관련한 페이지를 렌더링할때 , 중복코드를 없애고자할때 resolver를 쓰면 효율적이고 컴팩트한 코드를 구현할 수 있다고 배웠는데 처음배울때 한번 구현하고 안써서 처음에 명세서를 봤을때 form.html 하나로 어떻게 create, update 구현시킬지 막막했다. 이번 프로젝트로 한번더 resolver의 막강한 힘을 느낄 수 있었고,  이번 프로젝트가 계기가 되어 복습된 것 같아 좋은 경험이었다.

2) views.py 에서 review_ update 함수의  form 부분에서 분기문이 중첩되어있어서 항상 할때마다 헷갈리는것 같다.인증된 사용자일 떄, 아닐때,  POST 방식일때 아닐때  , 실제 내가 클라이언트 일 때를 생각해서 어떤 페이지를 넘기고 구현할지 잘 되새겨봐야겠다

3) base.html 네비게이션 바에서  인증된 유저일때, 아닐때 보여지는 부분을 각기 달리 구현할때 block 안에

코드를 구현해야하는 줄 알았는데 잘못 알고 있어서 여기서 시간이 많이 지체된것 같다!

### [후기]

9월 한달동안 여러번 진행했던 부분이었지만 ,이번에 resovler과 update 부분에서 분기문이 중첩되어있을때form 구현한 부분들 등 부족한점이 아직 많구나 라는 생각이 든 프로젝트였다

### [코드구현]

```python
#1.전체 리뷰를 볼 수 있는 페이지를 렌더링 해줌(최근작성순으로)
def review_list(request):
    reviews = Review.objects.order_by('-pk')
    context = {
        'reviews': reviews,
    }
    return render(request, 'community/review_list.html', context)

#2. 라뷰작성하는 폼
@login_required
@require_http_methods(['GET', 'POST'])
def review_create(request):
    if request.method == 'POST': #폼을 작성해서 클라이언트가 요청하면
        form = ReviewForm(request.POST) # form양식에 요청데이터를 넣음
        if form.is_valid(): #데이터 유효성 검사
            review = form.save(commit=False) #임시저장한 데이터를 새로은 Review db만듬
            review.user = request.user # 리뷰작성한유저를 Review모델에 있는 user로 할당
            review.save() #저장
            return redirect('community:review_detail', review.pk)
        	#다 작성하면 새로운 pk가 생겨나고 해당 pk값을 가지는 상세페이지로 넘겨줌
    else: #POST가 아닐떄 = 보통 조회할때
        form = ReviewForm() #입력폼을 보여줌
    context = {
        'form': form,
    }
    return render(request, 'community/form.html', context)

#3. 리뷰상세페이지조회
def review_detail(request, review_pk):
    review = get_object_or_404(Review, pk=review_pk) #보고싶은리뷰pk로 서버에 요청함
    comment_form = CommentForm() #각 게시물에 댓글폼도 보여줘야함
    comments = review.comment_set.all() # 이글에 달린 댓글(역참조)
    #보여줄 것들, 리뷰상세항목,댓글폼,작성된댓글
    context = {
        'review': review,
        'comment_form': comment_form,
        'comments': comments,
    }
    return render(request, 'community/review_detail.html', context)
#4.리뷰 수정관련
@login_required
@require_http_methods(['GET', 'POST'])
def review_update(request, review_pk):
    review = get_object_or_404(Review, pk=review_pk) #어떤게시글을 수정할건지 pk로 요청
    if request.user == review.user: #요청한 유저가 리뷰작성한 유저
        if request.method == 'POST':  #요청이 POST일때(수정요청했을때)
            #기존에 작성된폼에서 수정한 내용이 담긴 폼으로 지정
            form = ReviewForm(request.POST, instance=review) 
            if form.is_valid(): #데이터 유효성검사
                form.save()#저장
                #수정이 완료된 상세페이지로 넘겨줌
                return redirect('community:review_detail', review.pk)
        else: #요청이 POST가 아닐때, 조회할떄 이전 데이터가 담긴 폼을 들고옴
            form = ReviewForm(instance=review)
    else:#요청한 유저가 리뷰작성한 유저가 아닐때 수정권한이 없음,상세페이지로 넘김
        return redirect('community:review_detail', review.pk)
    #POST가 아닐때,어떻게 렌더할건지 보여주기위해서 context 만듬
    context = {
    'form': form,
    'review': review,
        }                                                                               #POST 방식아니면 요청한pk를 가지고 있는 데이터가 담긴 폼을 보여줌                      
    return render(request, 'community/form.html', context)

  


#5. 리뷰삭제
@require_POST
def review_delete(request, review_pk):
    if request.user.is_authenticated:
        review = get_object_or_404(Review, pk=review_pk)
        if request.user == review.user: #리뷰작성한유저랑 삭제요청한유저랑 같으면
            review.delete()#삭제함
            return redirect('community:review_list') #삭제반영된 전체리뷰조회
    return redirect('community:review_detail', review.pk)


#6.댓글작성
@require_POST
def comments_create(request, review_pk):
    #인증된유저이면
    if request.user.is_authenticated:
        review = get_object_or_404(Review, pk=review_pk) 
        #어떤글에 대한 댓글인지의 어떤글 불러오기
        comment_form = CommentForm(request.POST)#댓글창
        if comment_form.is_valid(): #유효성검사
            comment = comment_form.save(commit=False) # 작성한 댓글 임시저장
            comment.review =review #Comment 모델의 review에 상단에 정의한 review에 할당
            #어떤글에대한댓글인지
            comment.user = request.user#누가작성한댓글인지
            comment.save()
            return redirect('community:review_detail', review.pk)
        context = {
            'comment_form': comment_form,
            'review': review,
        }
        # POST방식아니면 상세페이지로 넘겨줌
        return render(request, 'community/review_detail.html', context)
    #인증된유저아니면 로그인페이지로 넘어감
    return redirect('accounts:login')


```

