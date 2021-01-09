> ### CSS Grid 핵심정리 
>
> - grid-template-columns, grid-template-rows

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>CSS Grid</title>
	<link rel="stylesheet" href="default.css">
	<style>
		.grid-container {
			display: grid;
			grid-template-columns: 100px 300px 200px;
			grid-template-columns: 1fr 2fr 1fr; 
			grid-template-columns: 1fr 500px 1fr;
			grid-template-columns: repeat(3, 1fr);
			grid-template-columns: repeat(3, 1fr 2fr 1fr);

			grid-template-rows:  200px 200px 200px;
			grid-template-rows:  200px 200px;
			height: 80vh;
		}
	</style>
</head>
<body>
	<div class="grid-container"></div>
		<div class="grid-item">A</div>
		<div class="grid-item">B</div>
		<div class="grid-item">C</div>
		<div class="grid-item">D</div>
		<div class="grid-item">E</div>
		<div class="grid-item">F</div>
		<div class="grid-item">G</div>
		<div class="grid-item">H</div>
		<div class="grid-item">I</div>
</body>
```

```
display: grid;
grid-template-columns: 100px 300px 200px; 고정비율
grid-template-columns: 1fr 2fr 1fr; 상대비율
grid-template-columns: 1fr 500px 1fr; 반응형
grid-template-columns: repeat(3, 1fr);반복횟수지정
grid-template-columns: repeat(3, 1fr 2fr 1fr); 9개 컬럼 지정하는 방법

grid-template-rows:  200px 200px 200px;
grid-template-rows:  200px 200px;

폭을 늘이려면 height: 숫자vh;
```

