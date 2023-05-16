정말 강의제목 그대로 지옥관리자인 git.
git 스터디에서 협업을 위해 지금까지 배운 내용을 정리해 github에 업로드하려 한다~!

# 0. Git 역사 및 배경지식
## 역사
유닉스: 대형 컴퓨터를 위한 OS
🔻
'리눅스 토발즈'가 유닉스를 개인용 컴퓨터의 OS로 발전시킴 👉 **리눅스**라 부름!
🔻
리눅스 특징 = 누구에게나 공개해야 함!(공개 소프트웨어 프로젝트)
🔻
이러한 리눅스 개발에 여러명의 개발자 필요
🔻
여러 개발자가 본인의 코드를 쉽게 합치기 위해 GIT 탄생⚡🎉

## 배경지식
📍 hub = 중심
📍 Git hub = 개발자의 중심!

⚡ **Git** vs **Github**
- Git : 분산 버전 관리 시스템, 코드 변경 이력 관리 도구
- Github: Git 저장소 공유 및 협업 관련 웹서비스

---
# 1. 깃 실행 원리
git bash에서 사용하는 코드를 기반으로 작성하였다.

우선 git bash 환경으로 들어가야 한다.
원하는 폴더 안에서 shift + 우측 마우스 클릭 -> Git Bash Here
![](https://velog.velcdn.com/images/ofohj/post/22f03109-cdb4-4e50-a7d7-f17a7393489c/image.png)

주요 원리는 아래 세 코드로 돌아간다.
```python
# 현재 위치에 지역 저장소를 만들게요
$ git init

# 변경 사항을 인덱스에 올릴래요
$ git add .

# 영구적으로 기록할래요
$ git commit -m "영구 기록"
```

위 코드를 바탕으로 아래와 같이 작성할 수 있다.
>🔻 프로젝트 생성 및 저장 코드
```python
$ git init
$ touch 파일명.txt
$ git add .
$ git commit -m "1. 파일 생성완료"
$ git log
```

알아야 할 개념이 있다!
📍 branch
git 초기화를 하면 master라는 branch가 생긴다.
이 branch에 차례로 commit한 기록이 저장된다.

- 새로운 branch 생성 코드
`git checkpoint -b [새 브랜치명]`

- 존재하는 branch 확인 코드
`git branch`

- branch 위치 변경
`git checkout [이동하고싶은 브랜치명]`


---
# 2. git merge
깃 수업을 들으면서 제일 많이 들었던 단어 "머지"
깃의 제일 핵심 기능이라고 생각한다!

merge에는 두 가지 방법이 있다.
- three-way merge : 형상이 다른 브랜치를 merge
- fast-forward merge : 형상이 같은 브랜치를 merge

merge는 아래 번호순대로 이루어진다.
![](https://velog.velcdn.com/images/ofohj/post/b98260ba-b548-4fd1-96e4-add3fcaa30d2/image.png)

*main branch = mb, topic branch = tb

1. mb에 '회원가입'이 커밋

2. tb에 '로그인'이 커밋

3. ⚡first-forward merge로 mb에 tb의 내용이 추가됨
```python
	# code
    git checkout master
    git merge topic # ff merge는 로그를 남기지 않고 merge됨
    # git merge --no-ff dev # 로그를 남기고싶다면 이 코드 사용
```

4. tb에 '아이디 중복 완료'가 커밋

5. mb에서 merge가 일어나지 않고 '글쓰기'를 새롭게 커밋

6. 이제 merge를 하고싶음. 단, 이 경우 3번과 다른 three-way merge!

7. merge시 tb의 내용이 그림과 같이 mb쪽으로 합쳐짐
```python
	# code
	git checkout master
    git merge topic
```

---
# 3. git push & pull
## push
- 개념: 로컬 저장소에서 작업 완료 후 원격 저장소에서 변경사항을 업로드할 때 사용됨
- 역할: uplode + merge
- 예시 상황: 개인 노트북에서 작업을 마치고 회사 컴퓨터에 업로드하고 싶을 때
- 핵심 코드: `git pull`
- 전체 코드
```python
	$ git init
    $ git add . commit
    
    #원격 저장소와 연결
    $ git remote add origin ["http 주소"]
    $ git remote -v # 연결 확인 코드
    
    $ git push origin master
```

## pull
- 개념: 원격 저장소에 새로운 커밋이 푸시되었을 경우, 해당 변경사항을 로컬로 가져올 때 사용
- 예시 상황: 팀원이 브랜치에 새로운 기능을 푸시해 이를 가져오고 싶을 때
- 핵심 코드: `git push`
- 전체 코드
```python
	$ git init
    $ git remote add origin ["http 주소"]
    $ git pull origin master
```

---
# 4. git clone
클론은~
✅ git init
✅ git remote
✅ git pull
위 모든 기능을 합한 기능이다!

- 전체 코드
```python
$ git clone [http 주소]
$ git checkout -b dev origin/master
$ git fetch origin
$ git checkout -b topic origin/master
$ git checkout master
$ git merge --squash topic
```

---
기본! 깃 사용법에 대해 정리해보았다.
이 외에도 깃으로 개인 블로그 만들기, 오픈소스 프로젝트에 기여하기 등등 있지만
그건 다음에 알아보도록 하자 🛌

---
[강의] https://inf.run/baVv