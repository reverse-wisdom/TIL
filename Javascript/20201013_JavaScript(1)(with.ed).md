>### Javascript(1) 2020.10.13

### DOM 조작

- HTML을 JS로 조작
- selector를 이용해서 조작
  - `querySeletor`/ `querySelectorAll`
  - dir(선택된 엘리먼트를 가진 변수)
    - 사용할 수 있는 속성정보를 볼 수 있다.
    - mdn 문서(mdn + 찾으려는 속성정보)
- DOM 조작 정리
  1. 선택한다
  2. 수정 및 변경한다.

---

### 이벤트 리스너

- 이벤트 브라우저에서 벌어지는 일

- 특정 이벤트가 벌어지면 특정 행동을 한다 

  `~하면 ~한다`

  `이벤트 타겟.addEventListener.`

- preventDefault()
  - 기본 동작을 동작하지 않게 막을 수 있다.

---

### 식별자(indentifier)

- 변수명은 식별자라고도 불림

- 규칙

  1. 반드시 **문자**, **달라($)** 또는 밑줄(_)로 시작해야한다(숫자나, `-` 로 시작할 수 없다)

     ```
     const hi-hello (중간에 들어가도안됨)
     ```

     

  2. 대소문자를 구분한다.
  3. 예약어는 사용할 수 없다(const, function ,class, ...)

- 스타일

  - 카멜케이스(lowerCamelCase)
  - - 객체, 변수, 함수

  - 파스칼 케이스(UpperCamelCase)
    - 클래스 생성자
  - 대문자 스네이크 케이스(UPPER_CASE)
    - 상수: 변수나 변수의 속성이 변하지 않는 것

---

### Hoisting

- var로 선언된 변수는 선언 이전에 참조할 수 있는 현상

  ```
  console.log(name)
  var name='홍길동'
  ```

---

### String

- JS에서 문자열을 표현하는 방법

  ```javascript
  const str1= '홑따옴표'
  const str2= "쌍따옴표"
  str1 + str2
  "홑따옴표쌍따옴표"
  
  const str3 = '줄바꿈 
  은 허용되자 않는다'
  
  //escape sequence
  const str4 = '줄바꿈은 \n 이렇게 해야합니다'
  
  //template literal (ES6+)백틱 (` : 물결표 쉼표 없이)
  const str5= `안녕하세요.
  줄바꿈도 가능합니다.`
  cibst
  
  const num = 100
  const str7 =` $(num)-$(str1)`
  "100 - 홑 따옴표 사용."
  
  
  ```

  

- 리터럴
  - 리터럴이라는 단어는 값을 프로그램 안에서 직접 지정한다라는 의미
  - 리터럴은 값을 만드는 방법

---

### Switch

- break 꼭 있어야함 

```javascript
let name = 'admin'
switch(name)  {
    case 'admin': {
        console.log('관리자모드')
    	break
    }
    case 'manager': {
        console.log('매니저모드')
        break
    }
    default: {
        console.log(`${name}님 환영합니다.`)
    }
}
```



### for 문

```javascript

//1
for (let i = 0; i < 6; i++) {
    console.log(i)
}

//2
const numbers= [0, 1, 2, 3]
for (const number of numbers) {
    console.log(number)
}

//3
//에러발생
const obj = {a: 'apple', b:'banana'}
for (const o of obj) {
    console.log(o)
}
//VM169:2 Uncaught TypeError: obj is not iterable
    at <anonymous>:2:17


//4
const obj = {a: 'apple', b:'banana'}
for (const o in obj) {
    console.log(o)
    console.log(obj[o])
}

```

### 화살표 함수

```javascript
const arrow = function (nanme) {
    return `hello! ${name}!!`
}

// 1. function 키워드를 삭제하고 화살표를 추가한다
const arrow = (name) => {
	return `hello ${name}!!`
}

// 2. 매개변수가 하나일때는 괄호를 생략할 수 있다.
const arrow = name => {
	retrun `hello ${name}!!`
}

// 3. {} & return 생략 (body에 표현식이 1개인 경우)
const arrow = name => `hello, ${name}`
}


//연습코드
const exam = function () {
	return 'hello, world'
}

//1
const exam = () => (
    //console.log(name)
	return 'hell, world'
)
//2. skip

//2-1 그래도 적용하고싶다면 _를 사용
const exam = _ => {
    return 'hello, world'
}//언더바로 생략가능


//3.
const exam = () =>'hello, world'
or
const exam = _ =>'hello,world'



```





### funtion 키워드 호이스팅

```javascript
//선언식일때는 동작 -> 호이스팅 적용됨
add(2, 7)
function add (a, b){
    return a + b
}
//표현식 일때는? ->호이스팅 적용안됨(const)
sub(2, 7)
const sub = function (num1, num2) {
	return num1 - num2
}

// var는  함수일떄는 hoisting 적용안됨
sub(2, 7)
const sub = (num1, num2) {
	return num1 - num2
}
```



### 함수의 Object 축약형

```javascript
let obj = {
    name: 'ssafy',
    sayHi: function () {
        console.log('hello')
    } 
}
obj.sayHi() //'hello'

//ES6+
let obj2 = {
    name: 'ssafy',
    // 함수의 object 축약형.
    sayHi () {
        console.log('hello')
    } 
}
obj.sayHi() 'hi'
```



### JSON(JavaScript Object Notaion)

JavaScript Objecct 형태를 가지는 문자열

#### object -> JSON(string)

```javascript
const objData = {
    coffee: 'Americano',
    icecream: 'Bravo corn',
}
const jsonData = JSON.stringify(objData)
console.log(typeof(jsonData))
```

#### JSON -> object

```javascript
const objData2 = JSON.parse(jsonData)
console.log(typeof(objData2))

```

### forEach

- exercise

  ```javascript
  //배열 안에 있는 정보를 곱해서 그 넓이를 areas 배열에 저장
  const images = [
      {height:10, width:30},
      {height:20, width:90},
      {height:54, width:32},
  ]
  const areas=[]
  ```

  - 풀이코드

    ```javascript
    images.forEach(function (img) {
        areas.push(img.height * img.width) //{height: 10, widthL 30},
    })
    console.log('areas')
    ```

    

### map

- exercise

  ```javascript
  // 각 숫자들의 제곱근이 들어있는 새로운 배열을 만드세요
  
  const newNumbers= [4, 9, 16]
  ```

  - 풀이

  ```
  const newArray = newNumbers.map(function (num) {
  	return num **0.5}
  
  )
  //const newArray2 = newNumbers.mpa(Math, sqrt)
  ```

  ```javascript
  const areas2 = images.map(function (img) {
      return img.height =img.width
          
  })
  console.log(areas2)
  ```

  

### filter

```javascript
const products = [
    { name:'cucumber', type: 'vegetable'},
    { name:'banana', type: 'fruit'},
    { name:'carrot', type: 'vegetable'},
    { name:'apple', type: 'fruit'},
]

const fruits = products.filter(function (product) {
    return product.type ==='fruit'
}
console.log(fruits)
```

- exercise

  ```javascript
  // numbers 배열중 50보다 큰 값들만 모은 배열 filteedNumbers을 만드세요
  
  const numbers= [15, 25, 35, 45, 55, 65, 75, 85, 95]
  
  const filteredNumbers = numbers.filter(function (num) {
      return num > 50
  })
  ```

### some

```javascript
const products = [
    { name : 'cucumber', type : 'vegetable'},
    { name : 'banana', type : 'fruit'},
    { name : 'carrot', type : 'vegetable'},
    { name : 'apple', type : 'fruit'},   
]
// 베지터블이 있는지 확인
const someVegetable = products.some(function(product){
    return product.type === 'vegetable'
})
console.log(someVegetable) #true

const someWater = products.some(function(product){
    return product.type === 'water'
})
console.log(someWater) #false

const zeroList = []
const someZero = zeroList.some(function (zero) {
    return zero > 50
})
```

```javascript
//requests 배열에서 status가 pending의 요청이 있는지 확인하세요
const requests = [
  { url: '/photos', status: 'complete' },
  { url: '/albums', status: 'pending' },
  { url: '/users', status: 'failed' },
]

const checkPending = requests.some(function (requests) {
    return request.status === 'pending'
})
console.log(checkPending)
```

### every

```javascript

// users 배열에서 모두가 submited 인지 여부를 hasSubmitted에 저장하세요.
const users = [
    { id: 21, submmited: true },
    { id: 33, submmited: false },
    { id: 712, submmited: true},
]
const hasSubmitted = users.every(function (user) {
    return users.submitted
})
```

### reduce

```javascript
//const scores = [90, 90, 80, 77]
//const totalScore =scores.reduce(function (sum, score) {
//    return sum + score //sum=sum+score
//}, 10000)


// 주어진 baseUrl 문자열 뒤에 필수 요청 변수인 api의 key-value 값을 key=value의 형태로 더하여 요청 url을 만드세요. url에서 요청 변수는 & 문자로 구분합니다.

const baseUrl = 'http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?'

const api = {
  'key': 'API_KEY',
  'targetDt': '20200115'
}


const apiUrl = Object.entries(api).reduce(function(url,api) {
    return url + `${api[0]}=${api[1]}&`    
}, baseUrl)
console.log(apiUrl)

```

