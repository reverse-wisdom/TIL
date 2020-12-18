>  ## 자바스크립트 프론트엔드 프로젝트 가이드
>
> ### [ Chapter03. 평균값 계산기 ]

---

#### Number() vs parseInt()

```javascript
parseInt('4')
//4
Number('2px')
//NaN
parseInt('2px')
//2
Number('tow')
//NaN
parseInt('two')
//NaN

//parseInt의 원하는 진수로 변환할 수 있는 기능
parse('100', 8)
//64

```

- 인자로 '2px' 를 넣어 보면 Number()에서는 숫자가 아니라 **NaN(Not-a-Number)** 이 리턴되는 반면 parseInt()가 입력 받은 문자열 중 첫번째 문자가 숫자로 변환 가능할 경우, 숫자가 아닌 부분이 나올때까지 변환을 해주기 때문이다. 따라서 아예 숫자로 변환할 수 없는 문자열 일 경우여야 동일한 결과가 나옴
- parseInt()에 두번째 인자로 원하는 진수를 넣어주면 원하는 진수로 바뀌어서 값을 리턴해줌, 두번째의 인자를 생략했을 경우에는  10진수로 처리

---

#### typeof 변수나 값의 타입을 알아내기 위한 키워드

```javascript
typeof 'hello'
//"string"

var value=123
typeof value
//"number"

```

---

#### 연산자 합치기

- **숫자+문자열**  또는 **문자열+숫자** 의 경우 문자열로 바뀌어서 합쳐짐 

```javascript
var pi = 3.14
console.log('PI의 값은'+ pi + '입니다.')
//pi의 값은 3.14입니다

console.log('합': ' + (2+3))
//합: 5
```



