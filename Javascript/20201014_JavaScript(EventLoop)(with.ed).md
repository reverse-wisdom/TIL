# Event Loop 동작 방법

```javascript
function func1 () {
    console.log('Hello')
    func2()
}

function func2 () {
    setTimeout(function () {
	    console.log('Ssafy!')        
    }, 0)
	func3()
}

function func3 () {
    console.log('Bye')
}


func1()
```

![image-20201014135751500](image-20201014135751500.png)

