## README

> project01을 진행하면서 새롭게 배운것들, 에러를 해결한 것들을 정리합니다.  



**새롭게 배운것**

- open()
  - filename: 내가 열고싶은 파일의 이름을 적는다.
  - mode: `r` 읽기모드, `w`쓰기모드, 아무것도 적지 않으면 기본적으로 읽기모드로 적용된다.
  - encoding: 한글떄문에 파일이 정상적으로 dict로 변환이 안된경우 `UTF8`을 적용하여 해결했다.

```python
open(filename, mode)
```



- json
  - 아직은 뭔지 잘 모르지만 dict라고 생각하자. (jpg, pmg=> 목적은 같지만 형식다름)

```python
import json
#json 데이터를 python에서 사용할 수 있는 dic데이터로 변환
dict_dat = json.load(json_data)
```

- 함수



> **GIT**

- working dir
  - 실제 작업공간
- staging area
  - add 명렁어를 입력했을 때 임시로 저장이 되는 공간
- local repo(.git)
  - commit 명령어를 입력했을 떄 버전이 기록되는 공간

> **명렁어** 

- `git init`
  - `.git` 폴더를 만들어 주는 명령어
  - 최초 한번만 실행한다.

- `git add`
  - 뒤에 staging area로 올리고 싶은 파일을 적어준다.
  - `.`을 입력하면 전체 파일이 추가된다.

- `git commit`
  - 버전을 생성
  - `-m` 옵션을 일반적으로 추가해준다.

- `git remote add`
  - 원격 저장소의 주소를 등록
  - origin이라는 이름을 기본값으로 사용
  - 최초 한번만 실행한다

- `git push`

  - 등록된 원격 저장소로 커밋 기록을 업로드

    