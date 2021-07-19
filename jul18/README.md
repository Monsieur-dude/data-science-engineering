## 혼자서 하는 연습용 문서
click [내 깃헙 주소](https://github.com/Monsieur-dude/myrepo4)

|Header|description|onemore|
|--:|--|:--:|
|cell1|cell2|cell+|
|cell3|cell4|cell++|

`git remote add origin (url)`


``` 
git remote add origin (url) 
git add file.exe, file.txt etc..
git commit -m "description"
git status
git push origin master
git pull origin master
```
## additionally I'm gonna add some lines to see if I can push and pull it well
## and I just added one more line at home. So let's push it pull it back
___

## Jul 18 
___
## 용어정리

`git commit -am "message"` 현재까지 변경사항을 모두 add 된 채로 commit 함

`git branch name` name의 브랜치를 생성함

`git branch -d name` name의 브랜치를 삭제함


`git checkout name` name브랜치로 전환함 
* 브랜치로 전환 시 작업상태는 그 브랜치의 마지막 상태로 이동함

`git add .` 현재 모든 파일을 index (working stage)로 올림

`git commit --amend` (커밋된 상태라도) 커밋 메시지 변경 가능

`git reset --hard version number` version number 상태로 되돌아(리셋)감

___


## Conflict
* 두 개의 서로 다른 **branch**가 동일한 이름의 파일 내에 있는 동일한 부분을 수정하고 그것을 병합(**merge**)할 때 발생하는 경고 혹은 기능





```
# Title
content
<<<<<<< HEAD
master
=======
o2
>>>>>>> o2
# Title
content 
```

### 위 코드에서...


| Sign | 뜻 |
|:--:|:--:|
| <<<<<<<<<< HEAD | **branch** 이름 |
| ====== | 구분자 (**delimiter** 혹은 **separator**)|
| >>>>>>>>>> o2 | **branch** 이름|

