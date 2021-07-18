
# 1.memo

### Git Doc
```
file:///D:/program/Git/mingw64/share/doc/git-doc
```

### Github .gitignore
```
( https://github.com/github/gitignore/blob/master/Node.gitignore )

// 현재 Repository의 cache를 모두 삭제한다.
git rm -r --cached .

// [File Name]에 해당하는 파일을 원격 저장소에서 삭제한다.
// (로컬 저장소에 있는 파일은 삭제하지 않는다.)
git rm -r --cached [File Name]

// .gitignore에 넣은 파일 목록들을 제외하고 다른 모든 파일을 다시 track하도록 설정한다.
git add .

git commit -m "Fixed untracked files"

```

### Github .gitignore 자동
```
https://www.toptal.com/developers/gitignore
```

### Github Command
```
1. Remote del
git remote -v
git remote rm origin

2. Readme
echo "# android-template-2" >> README.md

3. push
git config --global user.name "jogilsang"
git config --global user.email jogilsang@gmail.com
git init
git status
git add -A
git commit -m "update"
git remote add origin [git address]
git push -f origin master

4. Modifyed
git add -A
git commit -m "update"
git push -f origin master

5. (Specify path or folder Download, 특정경로,특정폴더)
mkdir RecyclerViewKotlin
cd RecyclerViewKotlin
git init RecyclerViewKotlin
cd RecyclerViewKotlin
git config core.sparseCheckout true
git remote add -f origin https://github.com/android/views-widgets-samples.git
echo "RecyclerViewKotlin/" >> .git/info/sparse-checkout
git pull origin master

6. Download
git clone [git address]
git pull [git address]
```

<hr/>

### Github Commit message
```
Type: 제목(Title)

본문(Body)

꼬리말(Footer)
```
Example :   
docs: Edit README.md to include New Features Use-Cases  

1. Type
- feat: 새로운 기능을 추가할 경우  
- fix: 버그를 고친 경우  
- docs: 문서 수정한 경우  
- style: 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우  
- refactor: 프로덕션 코드 리팩터링  
- test: 테스트 추가, 테스트 리팩터링 (프로덕션 코드 변경 없음)  
- chore: 빌드 테스크 업데이트, 패키지 매니저 설정할 경우 (프로덕션 코드 변경 없음)  

2. Body
- 제목과 본문 사이에 한줄공백, 본문은 한줄에 72자 이내, 구분시 -(불렛)사용


### Github 내용정리
1. Git은 업데이트 이력이 남고, 동시에 여러 사람이 같은 파일을 덮어씌운다던가 하는 실수를 미연에 방지할수있는 훌륭한 통합시스템이다.  
Git에서 저장소는 repository 라고 한다. 로컬과 원격 repository로 나뉘게 되며, 로컬의 경우 컴퓨터  
원격의 경우 Git서버라고 보면되겠다. pull, push, clone 세가지 기능이 있다  
pull의 경우 최신이력이 반영된 프로젝트 내용을 받아서 업데이트 하는것, push의 경우 현재 내용을 넣는것이다.  
clone의 경우 최신이력이 반영된 프로젝트 파일 자체를 받는것이다  

1. 폴더를 작업트리(worktree)라고 하는대, Commit까지 세개의 절차가있다  
작업트리에서 Index로 등록하는 과정을 스테이징이라고하고, 그다음 인덱스에서 repository로 Commit하는것이다.  
따라서 중간에 Index 과정이 생략될수없으며, 원하는 파일만큼 Commit 하려고할떄 파일을 골라내는것이 스테이징이다.  

1. 브랜치는 독립적으로 어떤 작업을 진행하기 위한 개념으로, 여러작업을 동시에 진행할수있다.  
예를들면 릴리스 버전이력,기능 추가이력, 버그 수정이력 등이 있다.  
팀내에서 상의해야할부분은 어느 시점에서 브랜치들을 통합할지 여부, 브랜치 이름의 규칙, 어떤 상황에서 브랜치를 만들가이다  

1. 브랜치는 master, hotfix, release, develop, feature 다섯가지로 나뉜다.  
master 브랜치의 경우 안정적이며, 언제든지 배포가 가능한 상태이다. 또한 version0.1 같이 배포번호가 기록된다  
develop 브랜치가 대게 통합브런치 역활을 하며, 해당 브런치를 기반으로 개발된다.  
release 브랜치의 경우 모든 기능이 동작되는지 확인하는 브런치다. 배포하게 되는경우 해당내용을 반영해서 develop 브런치에도 반영한다.  
hotfix는 긴급하게 발생한 버그를 수정하기 위한 브런치로, 대게 master 브런치에서 가져오게되며 수정사항은 develop 브런치에도 반영한다.  
feature 브런치는 토픽브런치라고도 하며, 기능추가,버그수정 등 단위작업을 수행한다. 작업이 다 완료되면 통합브런치에 합치고, 관련사항을 공유한다. 피처브런치(토픽브런치)를 통합브런치에 합친다던가, 브런치  쓰이는 기능은 merge와 rebase 두가지가있다.  

1. 브랜치를 전환하는 작업의 command를 checkout이라고한다.   
해당 브런치의 최상단 케이스를 Head라고 하며, 그 이전 케이스들은 ^(캐럿), ~(틸드)를 head와 같이 기술하여 표현할수있다.  
stash는 임시저장소로 커밋하지않은 상태에서 브런치를 변경하게될때, 임시로 변경사항들을 저장한다음 변경된 브런치에서 커밋할떄 사용한다. 

<hr/>

### Github README.md 작성법
1. 라인피드(Linefeed)
- 줄에다가 스페이스+스페이스 를 넣는다
```
사람을 존경하라,  
그러면 그는 더 많은 일을 해 낼 것이다.
```
- 아무생각없이 엔터를 친다면, 아래와같이 
```
사람을 존경하라,

그러면 그는 더 많은 일을 해 낼 것이다.
```



2. 이미지 리사이즈(Image Resize)

- git 파일내부 
```
"![](/11.png)"

android : 375 x 667
```
![](/11.png)

- git 파일 리사이즈 1
```
<center><img src="/11.png" width="375" height="667"></center>
```
<center><img src="/11.png" width="375" height="667"></center>

- 웹 페이지 가져오기
```
![](https://blogpfthumb-phinf.pstatic.net/MjAxNzEyMDhfMTMy/MDAxNTEyNzA3MTc0ODA3.rbnlwP_k8OCxoan813kT-Q0DVAxw8Vgb0co6Ivpcg1Yg.QdHiNjmkf1OVkzCy8ZIyyy1cjDe2947sLVuj9vynVpQg.PNG.jogilsang/JS.png?type=w161)
```
![](https://blogpfthumb-phinf.pstatic.net/MjAxNzEyMDhfMTMy/MDAxNTEyNzA3MTc0ODA3.rbnlwP_k8OCxoan813kT-Q0DVAxw8Vgb0co6Ivpcg1Yg.QdHiNjmkf1OVkzCy8ZIyyy1cjDe2947sLVuj9vynVpQg.PNG.jogilsang/JS.png?type=w161)
 
 <hr/>
 

<hr/>

### Github 개요
```
Project title
A little info about your project and/ or overview that explains what the project is about.

Motivation
A short description of the motivation behind the creation and maintenance of the project. 
This should explain why the project exists.

Build status
Build status of continus integration i.e. travis, appveyor etc. Ex. -

Code Style
If you're using any code style like xo, standard etc. 
That will help others while contributing to your project. Ex. -

Screenshots
Include logo/demo screenshot etc.

Tech/framework used
Ex. -
Built with
Electron

Features
What makes your project stand out?

Code Example
Show what the library does as concisely as possible, 
developers should be able to figure out how your project solves their problem by looking at the code example. 
Make sure the API you are showing off is obvious, and that your code is short and concise.

Installation
Provide step by step series of examples and explanations about how to get a development env running.

API Reference
Depending on the size of the project, 
if it is small and simple enough the reference docs can be added to the README. 
For medium size to larger projects it is important to at least provide a link to where the API reference docs live.

Tests
Describe and show how to run the tests with code examples.

How to use?
If people like your project they’ll want to learn how they can use it. 
To do so include step by step guide to use your project.

Contribute
Let people know how they can contribute into your project. A contributing guideline will be a big plus.

Credits
Give proper credits. This could be a link to any repo which inspired you to build this project, 
any blogposts or links to people who contrbuted in this project.
Anything else that seems useful

License
A short snippet describing the license (MIT, Apache etc)
MIT © Yourname
```

### test
  #### test1
