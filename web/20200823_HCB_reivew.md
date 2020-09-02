> ## 과목평가 HTML/CSS/Bootstrap 정리



> ### Homework, Workshop ###

#### ★0810

**HTML(Hyper Text Markup Language)**

**CSS(Cascading Style Sheets)**



### # HTML/CSS 진위여부

HTML과 CSS는 각자 문법을 갖는 별개의 언어이다.

웹브라우저는 내장 기본 스타일이 있어 CSS 가없어도 작동한다

id 값은 유일해야하므로 중복되어서는 안된다 .



### #구조선택자

![image-20200823152619133](20200823_HCB_reivew.assets/image-20200823152619133.png)

---



### **<CSS 우선순위>**

```html
 !important > Inline style > id 선택자 > class 선택자 > 요소 선택자 > 소스 순서
```



**적용 우선순위**

1. `!important`

   - 다른 사람들의 코드에서 발견할 때 그 의미를 알 수 있는 것은 좋다.
   - 하지만 반드시 필요한 경우가 아니면 절대 사용하지 않는 것이 좋다.,

   `!important` 는 cascading이 정상적으로 작동하는 방식을 변경하므로, CSS 스타일 문제를 해결하기가 어렵습니다.

 2. `inline style`

 3. `id 선택자`

    - id는 대부분의 다른 선택자보다 우선순위가 높기 때문에 다루기가 어려워 질 수 있다.
    - 대부분의 경우 id 보다는 모두  class 선택자로 작성하는 것이 좋다.
    - 만약 문서 내 링크 이동이나 for를 사용하는 특별한 경우에만 아이디를 사용한다.

4. lass 선택자
5. 요소 선택자
6. 소스 순서





## **★0813**

**row**: flex-row

**column**: flex-column

**row-reverse**: flex-row-reverse

**column-reverse**: flex-column-reverse



**row**: 주 축을 좌에서 우로 설정

**column**: 주 축을 위에서 아래로 설정

**row-reverse** :주 축을 우에서 좌로 설정

**coloumn-reverse** : 주 축을 아래에서 위로 설정



align-items속성의 4가지 값과 각각의 특징을 작성하시오

- strech: 부모속성의 높이에 맞게 최대 높이로 늘여서 맞춤

- center: 수직축의 가운데 정렬

- start: 수직축의 시작점부터 정렬

- end: 수직축의 끝점부터 정렬

  

**flex-flow**

(1)flex-direction, flex-wrap





![image-20200824045726166](20200823_HCB_reivew.assets/image-20200824045726166.png)

----

container/row/ break point(sm, md, lg, xl)-화면의 크기에 따라서 적용되는 클래스를 다르기 하기위해 사용,

12이하 정수: 12개로 나우어진 공간에서 몇칸을 차지하는 표시** 

### **<시맨틱태그>**

- HTML5에서 의미론적 요소를 담은 태그의 등장 

- 태그 종류
  - header: 문서전체나 섹션의 헤더(머릿말 부분)
  - nav: 내비게이션
  - aside: 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠
  - section: 문서의 일반적인 구분, 컨텐츠의 그룹을 표현
  - article: 문서, 페이지, 사이트안에서 독립적으로 구분되는 영역
  - footer: 문서 전체나 섹션으 푸터(마지막부분)

- 개발자 및 사용자 뿐만 아니라 검색엔진 등에 의미있는 정보의 그룹을 테그로 표현
- 단순히 구역을 나누는 것 뿐만 아니라 의미를 가지는 태그들을 활용하기 위해 노력
- Non sementic 요소는 div, span 등이 있으며, h1 , table 태그 들더 시맨틱 태그로 볼 수 있음
- 검색엔진최적화(SEP)를 위해서 메타택, 시맨틱 태그등을 통한 마크업을 효과적으로 할 필요가 있다

---



### **<Block & Inline>**

##### block: 한 요소가 페이지 끝까지 차지하고 다음요소가 다음문단으로 옴

- **div, h, p, 목록태그, 테이블태그, form태그**

	- 쌓이는 박스
	- 요소는 블록 요소 상자를 생성하여 일반 흐름에서 요소 앞뒤에 줄 바꿈을 생성한다.
	- 블록 레벨 요소안에 인라인 레벨 요소가 들어갈 수 있다.

```css
display: block;
-줄바꿈이 일어나는 요소
-화면 크기 전체의 가로 폭을 차지한다.
블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음
```

**inline: **

- **span, a, input, 글자형식**

- 한 요소가 콘텐츠만큼 자리 차지 (tag: span, div)
- 줄바꿈이 일어나지 않는 행의 일부 요소

- width, height, margin-top, margin-bottom을 지정할 수 없음

- 상하 여백은 line-height로 지정 

```css
display: inline;
-줄바꿈이 일어나지 않는 행의 일부 요소
-content너비만큼 가로 폭을 차지한다.
-width, height, margin-top, margin-bottom을 지정할 수 없다.
-상하 여백은 line-height로 지정한다
```

#### **속성에 따른 수평정렬**

![image-20200823135122692](20200823_HCB_reivew.assets/image-20200823135122692.png)

**inline-block**

- inline처럼 텍스트 흐름대로 나열, block 처럼 박스 형테이기 때문에 block속성 사용가능

```css
display: inline-block;
- block과 inline 레벨 요소의 특징을 모두 갖는다.
- inline처럼 한 줄에 표시가능하며,
- block처럼 width, height, margin 속성을 모두 지정할 수 있다
```

**none**

- 해당 요소를 화면에서 사라지게 하며 요소의 공간조차 사라지게 한다.

- visibility: hidden;은 해당 요소를 화면에서 사라지게는 하나 공간은 사라지지 않는다.

```css
display: none;
- 해당 요소를 화면에 표시하지 않는다. (공간조차 사라진다.)
- 이와 비슷한 visibility: hidden;은 해당요소가 공간을 차지하나 화면에 표시만 하지 않는다.
```





**<예시>**

![image-20200823133822277](20200823_HCB_reivew.assets/image-20200823133822277.png)

---



### **<HTML 태그 종류>**

**그룹**: hr, p

**텍스트태그** : b-strong(시맨틱: 스크린리더읽을때 강조해서 읽음), i-em(시맨틱), span, br, img

**form**: 서버에서 처리될 데이터를 제공하는 역할

- 속성: 
  - action: 엔터를 눌렀을 때 어디로 보낼지
  - method: GET, POST

- input : 다양한 타입의 가지는 입력 데이터 필드

  속성: name, placeholder, required, autofocus

  

- label: 서식입력 요소의 캡션

---

내부참조/외부참조/인라인

외부참조/내부참조 다 헤드안에 들어감

내부참조: style

외부참조:  link~ href: 파일명

###  < CSS seletor>

선택자는 스타일을 지정할 웹 페이지의 HTML 요소를 대상으로 하는 데 사용

**클래스(class) 선택자** 

- 클래스 선택자는 마침표( .) 문자로 시작 하며 해당 클래스가 적용된 문서의 모든 항목을 선택

**아이디(id) 선택자** 

- 아이디 선택자는 # 문자로 시작하며 기본적으로 클래스 선택자와 같은 방식으로 사용
- 그러나 아이디는 문서 당 한 번만 사용할 수 있으며 요소에는 단일 id값만 적용 할 수 있다
- 문서에서 동일한 아이디를 여러 번 사용해도 동작하나 그렇게 하면 안된다.

**복합 선택자**

- 자손(하위의 모든 요소) : 셀렉터a  공백 셀렉터b
- 자식(바로 아래의 요소) : 셀렉터a > 셀렉터b

### <CSS단위>

**기본폰트 16px**

**px**(상대크기)

- 모니터 해상도의 한 화소인 '픽셀'을 기준
- 픽셀의 크기는 변하지 않기 때문에 고정적인 단위

**%**

- 백분율 단위
- 가변적인 레이아웃에서 자주 사용

**em**

- em은 상속의 영향 받음, rem은 최상위 요소(html)를 기준으로 결정됨.
- 상황에 따라 각기 다른 값을 가질 수 있다.
- 요소에 지정된 사이즈에 상대적인 사이즈를 가짐

**rem**

- 최상위 요소인 html(ro  ot em)을  절대 단위를 기준으로 삼음. 상속의 영향을 받지 않음.
- 상속에 영향을 받지 않기 때문에 대부분의 경우 rem 을 많이 사용한다.

**viewport**

- (스크롤을 내리지 않은 상태에서) 웹 페이지를 방문한 유저에게 현재 보이는 웹 컨텐츠의 영역
  viewport를 기준으로한 상대적인 사이즈

- 주로 스마트폰이나 테블릿 디바이스의 화면을 일컫는 용어로 사용된다.
- vw, vh, vmin, vmax

### < CSS: Box Model >

### 구성

![image-20200823130250794](20200823_HCB_reivew.assets/image-20200823130250794.png)



### **표현법**

![image-20200823130448804](20200823_HCB_reivew.assets/image-20200823130448804.png)



### **box-sizing**

- 전체 선택자로 border-box로 지정해주는편

  ```css
      * {
        box-sizing: border-box;
      }
  ```

  

- 기본적으로 모든 요소의 box-sizing은 content-box
  - Padding을 제외한 순수 contents 영역만을 box로 지정

- 다만, 우리가 일반적으로 영역을 볼 때는 border까지의 너비를 100px 보는것을 원함
  - 그 경우 `box-sizing`을 `border-box`으로 설정

```html
    .box-sizing {
      box-sizing: border-box;
	
    }
```



```html
    .box-sizing {
      box-sizing: border-box;
    }
```



<img src="20200823_HCB_reivew.assets/image-20200823131039003.png" alt="image-20200823131039003" style="zoom:80%;" />

- **마진상쇄**

```css
#마진상쇄: 마진이 겹치면 더해지는게 아니라 가장큰 값으로 덮어 씌워짐
```

---



### < CSS: Position>

**박스의 위치 속성 & 값**

- position
  - static / absolute / relative / fixed
  - z-index



**기본 개념**

 1. static (기본 위치)

    - 기본적인 요소의 배치 순서에 따름(좌측 상단)
    - 부모 요소 내에서 배치될 때는 부모 요소의 위치를 기준으로 배치된다

    - 모든 태그의 기본

    - 태그의 default 값

---

아래 좌표 프로퍼티(top, bottom, left, right)ㄹ를 사용하여 이동이 가능하다(음수값도 가능)

2. relative (상대 위치)
   - 기본 위치(static)를 기준으로 좌표 속성을 사용해 위치 이동 

![image-20200823142452056](20200823_HCB_reivew.assets/image-20200823142452056.png)



3. absolute (절대 위치)

   - static 이 아닌 부모/조상 요소를 기준으로 좌표 속성 만큼 이동
   - 부모 요소를 찾아가고 나아가 없다면 body에 붙는다.

   

4. fixed (고정 위치)

   - 부모/조상 요소와 관계없이 브라우저의 viewport(브라우저)를 기준으로 좌표 속성 만큼 이동
   - 스크롤을 내리거나 올려도 화면에서 사라지지 않고 항상 같은 곳에 위치



**absolute**

- absolute는 원래 위치해 있었던 과거 위치에 있던 공간은 더 이상 존재하지 않는다는 점이 특징이다.

- 즉, 다른 모든 것과는 별개로 독자적인 곳에 놓이게 된다.

- 언제 쓸까?

  - 페이지의 다른 요소의 위치와 간섭하지 않는 격리된 사용자 인터페이스 기능을 만들 수 있다.

  - 팝업 정보 상자 및 제어 메뉴, 롤오버 패널, 페이지 어느 곳에서나 끌어서 놓기할 수 있는 유저 인터페이스 페이지 등

- <img src="20200823_HCB_reivew.assets/image-20200823180506695.png" alt="image-20200823180506695" style="zoom:67%;" />



![image-20200823145203859](20200823_HCB_reivew.assets/image-20200823145203859.png)   

---



### < CSS 상속 >

CSS는 상속을 통해 요소의 속성을 자식에게 상속한다

- 속성(프로퍼티)중에는 상속이 되는 것과 되지 않는 것들이 있다.
- 상속 되는 것
  - Text관련요소(font, color, text-align, opacity, visibility)

- 상속되지 않는 것 예시
  - Box model 관련요소(width, height, margin padding, border, box-sizing, display)
  - positon 관련 요소(position, top/right/botton/left, z-index)

**예시**

![image-20200823132305895](20200823_HCB_reivew.assets/image-20200823132305895.png)





### **<선택자 종류>**

![image-20200823165400496](20200823_HCB_reivew.assets/image-20200823165400496.png)



### **input 태그**

- `label`  `for` = `input` `id` 랑 같아야함

  ​	placeholder 

- button, radio checkbox 



### **button 종류**

```html
<!-- 일반 버튼은 눌리는 버튼 역할 -->
<input type="button" value="로그인">
<!-- 서브밋 버튼은 눌리면 form 태그에 설정된 action 으로 값을 보내줌. -->
<input type="submit" value="서브밋">
<!-- 얘도 서브밋 역할 -->
<button>버튼</button>
```





### float



![image-20200823225135691](20200823_HCB_reivew.assets/image-20200823225135691.png)

```css
    .clearfix::after {
      content: "";
      display: block;
      clear: both;
```





`

### **자손선택자, 자식선택자 차이점**



자손과 자식은 자손은 선택된 요소 안의 지정된 모든 하위 태그를 말하는 것이고 자식 선택은 요소 안의 바로 아래태그를 가르친다



## **flexbox**

- 부모 요소에 `display:flex` 혹은 `inline-flex`를 작성하는것부터 시작한다

- 일명 flexbox라 불리는 Flexible Box module은 flexbox 인터페이스 내의 아이템 간 공간 배분과 강력한 정렬 기능을 제공하기 위한 1차원 레이아웃 모델로 설계되었다.

  웹페이지의 컨테이너에 아이템의 폭과 높이 또는 순서를 변경해서 웹페이지의 사용 가능한 공간을 최대한 채우고 이를 디바이스 종류에 따라 유연하게 반영하도록 하는 개념

```css
.flex-container {
    display; flex:
}
```

<img width="947" alt="Screen Shot 2020-08-12 at 4 53 25 PM" src="https://user-images.githubusercontent.com/18046097/89989904-8b76c300-dcbc-11ea-8427-051cce03807c.png">

**핵심 개념**

- 요소
  - flex container
  - flex items
- 축
  - maix axis (주축)
  - cros axis (교차축)

```html
justify - main axis
align - cross axis

content - 여러 줄
items - 한 줄
self - 개별 요소

justify-content: 메인축 기준 여러줄 정렬
align-items: 교차축 기준 한 줄 정렬
align-self: 교차축 기준 선택한 요소 하나 정렬
```





#### **Flex에 적용하는 속성**



**justify** 가 들어가면 메인축, **align** 이면 교차축 

- 배치 방향설정: `flex-direction`   좌우->상하로도 바꿀 수 있음

  - main-axis 방향만 바뀐다.

  - flexbox는 단방향 레이아웃이기 떄문이다

    - row/row-reverse/column/column-reverse

    ![image-20200823231107636](20200823_HCB_reivew.assets/image-20200823231107636.png)

- 메인축 방향 정렬: `justify-content`

- 교차축 방향 정렬 : `aline-items`, `align-self`, `align-content`

- 기타: `flex-wrap`, `flex-flow`. `flex-grow`, `order`, `flex-shrink`



### **content & items & self**

- content: 여러줄
- items: 한줄
- self: flex item 개별요소
- 예시:
  - justify- content: 메인축 기준 여러줄 정렬
  - align-items: 교차축 기준 한 줄 정렬
  - align-self: 교차축 기준 선택한 요소하나 정렬

---

**< justify-content >**

- flex-start, flex-end,  center,  space-between, space-around, space-evenly

**< align-items >**

- flex-start, flex-end, center, stretch, baseline

**< align-content >**

- flex-start, flex-end, center, stretch, space-between, space-around

**< align-self >**

- auto, flex-start, flex-end, center, baseline, stretch

---

**기본형식**

```css
.flex-container {
	display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}
```



**1. 부모 container에 flex 선언시**

​	1) item은 행으로 나열된다.9

​	2) item은 메인축의 시작선에서 시작한다.

​	3) item은 크로스축의 크기를 채우기 위해 늘어난다.

​	**※flex-direction은 디폴트값이 row이다**

​	**※ self는 개별요소라, 전체 컨테이너에 넣는게 아니라 각 요소에 지정해준다**

- `display: inline-flex;`  일 경우 컨텐츠만큼 채워짐

- `flex-wrap:wrap;` 넘치는 컨텐츠는 줄바꿈해서 채워진다.
- `flex-wrap:nowrap;`모든 아이템들 한 줄에 나타내려고 함 (그래서 자리가 없어도 튀어나옴) , 기본값
- `flex-wrap:wrpa-reverse;`  넘치면 그 윗줄로 (역순)
- `flex-direction: row-reverse;`

![image-20200823235551096](20200823_HCB_reivew.assets/image-20200823235551096.png)

- `flex-direction: column;`

![image-20200823235715345](20200823_HCB_reivew.assets/image-20200823235715345.png)

- `flex-direction: column-reverse;`

![image-20200823235829539](20200823_HCB_reivew.assets/image-20200823235829539.png)

- `flex-flow: column wrap;`  ▶ flex-direction + flex-wrap의 축약 (축, 랩설정)
- `justify-content: flex-end; `**★flex-direction: row-reverse와 혼동하지 말것!!**

![image-20200824000217418](20200823_HCB_reivew.assets/image-20200824000217418.png)

- `justify-content: center;`

![image-20200824000345603](20200823_HCB_reivew.assets/image-20200824000345603.png)

- `justify-content: space-between;` 처음과 긑을 가장자리에 두고 나머지는 일정한 간격으로 배치됨

![image-20200824000858546](20200823_HCB_reivew.assets/image-20200824000858546.png)

- `justify-content: space-around` : 내부 요소의 여백이 외곽요소의 2배임

![image-20200824001007324](20200823_HCB_reivew.assets/image-20200824001007324.png)

- `justify-content: space-evenly;` 내부요소여백과 외부요서여백이 같음

![image-20200824001637914](20200823_HCB_reivew.assets/image-20200824001637914.png)

---

**크로스축 정렬**

- `align-items`: `flex-start;` items는 한줄

![image-20200824002334066](20200823_HCB_reivew.assets/image-20200824002334066.png)



- `align-items`: `flex-end;` 

![image-20200824002434804](20200823_HCB_reivew.assets/image-20200824002434804.png)

- `align-items: center;`

![image-20200824002650504](20200823_HCB_reivew.assets/image-20200824002650504.png)





메인축/ 보조축 중앙정렬 : justify-cont: center; , align-items: center;

- `align-items: baseline;`  각 요소가 글자크기 다를때 글자 밑에 여백이 동일함, item 내부의 text에 기준선을 맞춤

![image-20200824003208806](20200823_HCB_reivew.assets/image-20200824003208806.png)

---

**self**

< flex-direction:row >

![image-20200824003847478](20200823_HCB_reivew.assets/image-20200824003847478.png)

< flex-direction:column >

![image-20200824004256561](20200823_HCB_reivew.assets/image-20200824004256561.png)

- `align-self: stretch;` 부모 컨테이너에 자동으로 맞춰서 늘어난다.

![image-20200824004021119](20200823_HCB_reivew.assets/image-20200824004021119.png)

---

**기타**

**order** 기본값은 0, 작은 숫자 일수록 앞(왼쪽)으로 이동. 음수사용 가능

![image-20200824004615966](20200823_HCB_reivew.assets/image-20200824004615966.png)

**flex-grow** 남은 공간을 어떻게 분배할것인지, 음수사용불가

![image-20200824005538275](20200823_HCB_reivew.assets/image-20200824005538275.png)

- 남은 공간을  1+2+3 등분해서 item1에 1, item2에 2, item3에 3을 준다는 의미, 비율아님!!

![image-20200824010015030](20200823_HCB_reivew.assets/image-20200824010015030.png)





---

> ## Bootstrap

### Spacing

![image-20200824015458373](20200823_HCB_reivew.assets/image-20200824015458373.png)



`.mx-auto` : 수평중앙정렬

`.py-0` = padding-top: 0;, padding-bottom: 0;



### **fixed-top 과 sticky-top 비교**

fixed-top: 브라우저에서 계속 고정

stick-top:  다음 stick-top 만날때까지 고정이다가 다음 sticky-top 만나면 가려지고 마지막에 적은 stick-top만 보이게됨 





### **Breakpoints**

-상단 숫자봐야함!!!

![image-20200824024147600](20200823_HCB_reivew.assets/image-20200824024147600.png)

### ![image-20200824024118549](20200823_HCB_reivew.assets/image-20200824024118549.png

![image-20200824023005184](20200823_HCB_reivew.assets/image-20200824023005184.png)

- 기존 문법이랑 다름

  justify-content-start -> justify-content: flex-start;

  d-flex -> display=flex; 



---

> ## **Grid System**

![image-20200824023458862](20200823_HCB_reivew.assets/image-20200824023458862.png)

- container로 감싸야함



**12개넘어가면 다음행으로 넘어감**

![image-20200824024922458](20200823_HCB_reivew.assets/image-20200824024922458.png)



div class="w-100" 하면 부모요소의 너비를 상속받는 투명한 요소를 만들어 12/34 문단나눔가능





![image-20200824025017316](20200823_HCB_reivew.assets/image-20200824025017316.png)



---

### **Components**

navbar

pagination

---

![image-20200824055353766](20200823_HCB_reivew.assets/image-20200824055353766.png)





![image-20200824055936141](20200823_HCB_reivew.assets/image-20200824055936141.png)



![image-20200824060228647](20200823_HCB_reivew.assets/image-20200824060228647.png)

flex-direction: row-reverse;
justify-content: flex-end;



![image-20200824060526059](20200823_HCB_reivew.assets/image-20200824060526059.png)

flex-direction: column;
justify-content: flex-end



![image-20200824060754641](20200823_HCB_reivew.assets/image-20200824060754641.png)



flex-direction:row-reverse;
justify-content:center;
align-items:flex-end



![image-20200824061104101](20200823_HCB_reivew.assets/image-20200824061104101.png)

align-self: flex-end;
order:1

![image-20200824061308792](20200823_HCB_reivew.assets/image-20200824061308792.png)

flex-direction: column;
flex-wrap:wrap;



![image-20200824061512053](20200823_HCB_reivew.assets/image-20200824061512053.png)



![image-20200824061651467](20200823_HCB_reivew.assets/image-20200824061651467.png)



flex-direction:column-reverse;
align-content:center



![image-20200824062446218](20200823_HCB_reivew.assets/image-20200824062446218.png)



flex-flow: column-reverse wrap-reverse;
justify-content:center;
align-content: space-between;