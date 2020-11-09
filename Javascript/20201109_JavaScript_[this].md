> ## JavaScript 에서 this 의 의미 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <h1>this 란??</h1>
  <script>
    // 1. 기본 함수에서 this
    function myFunc() {
      console.log(this)  // window
      console.log(this === window)
    }

    // 2. 메소드에서 this
    const myObj = {
      myFunc: function () {
        console.log(this)
        console.log(this === myObj)
      }
    }

    // 3. 메소드 안에 다시 콜백 함수를 실행했을 때 this
    const myObj1 = {
      myFunc: function () {
        console.log(같은지,this === myObj1)
        setTimeout(function () {
          console.log('setTime: ',this)  // window
          console.log(this === myObj1)
        })
      }
    }
    // 결론
    // obj.function() 메소드로 호출 될 때 => this === obj
    // 그 외 모든 상황 => this === window

  </script>
</body>
</html>
```

