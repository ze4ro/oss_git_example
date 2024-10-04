# **오픈소스SW개발론**

### Introduction

-------------
### Week1-1 강의 개요 (강의계획서)
* 담당교수 : 최광훈
* 강의시간 : **화1목1**
* 강의실 : **AI융합-106**
* 수업방법 : 플립러닝

* 교과요목
  1. 오픈소스 소프트웨어 개발을 위한 기본 개념과 도구, 특히 소스 코드 버전 컨트롤과 패키지 관리, 프로젝트 빌드를 중점으로 배운다.
  2. 애자일 기반 소프트웨어 개발 방법인 짝프로그래밍, 테스트 주도 개발, 행위 주도 개발, 클라우드 기반 데브옵스를 공부한다.
  3. 새로운/낯선 소프트웨어 개발 환경 및 도구를 스스로 배우는 태도를 배우는 것을 목적으로 한다. 새로운 추세의 컴퓨팅 환경에 빠르게 적응하여 협력적인 소프트웨어 개발을 주도할 수 있는 능력을 배운다.

* 수업목표 
  * **컴퓨팅사고** : 함수형 프로그래밍언어 스타일을 익힌다.
  * **융합** : LLM/ChatGPT를 새로운 프로그래밍을 배우는데 활용한다.
  * **글로컬** : Git/Github를 통해 협업하는 방식을 배운다. 영어 학습 자료를 공부함으로써 영어 활용 기회를 늘린다.
  * **소프트웨어 응용 문제해결 능력** : Basic concepts and tools for open-source software development _(오픈소스 소프트웨어 기본 개념과 도구)_, Attitude to self-learn new SW tools and environments _(새로운/낯선 소프트웨어 개발 환경 및 도구를 스스로 배우는 태도)_, Basic functional programming, Haskell _(기초 함수형 프로그래밍, 하스켈)_

-------------
### Week1-2 오픈소스소프트웨어 개요
* The State of Open Source Software (OSS)  
2023년 오픈소스 소프트웨어 동향 (Git)  
[Octoverse at Github (2023)](https://octoverse.github.com/)
    
* What is Open Source Software?  
오픈소스 소프트웨어 : 소프트웨어 저작권 소유자가 모든 사람에게 소스 코드를 게시, 사용, 복사, 수정 및 배포할 권리를 부여한 소프트웨어
    
1. 상용화 관점  
* Commercial SW (E.g. Windows)
  * Individual License(EULA: End-User License Agreement) **(개별 이용 허락)**
  * Royalty **(로열티 지급)**
  * Binary only **(실행 바이너리만 제공)**
  * No reproduction, distribution, and modification **(복제, 배포, 수정 불가)**
  * Limited terms and purposes **(사용 기간과 목적 제한)**
  * Protected by Intellectual Property Rights **(지적재산권에 의해 보호)**

* Open Source SW
  * Open Source Lincense **(일괄 사전 이용 허락)**
  * No Royalty **(로열티 없음)**
  * Source code **(소스 코드 제공**
  * Reproduction, distribution, and modification are permitted **(복제, 배포, 수정 허용)**
  * No limitation on terms and purposes **(사용 기간/목적 제한 없음)**
  * Protected by Intellectual Property Rights **(지적재산권에 의해 보호)**
  
  
2. 철학적 관점  
![OSS에 대한 철학적 관점](https://ibb.co/jRB7b89)  
_Free Software = 자유 소프트웨어 **(not 공짜 소프트웨어)**_


* Open Source Software License  
OSS라이선스 : 오픈소스 소프트웨어의 사용, 복제, 수정, 배포 권한의 범위를 지정  
  * GPL (GNU General Public License)
  * LGPL (GNU Lesser General Public License)
  * MIT License
  * BSD License
  * Apache License
  * MPL (Mozilla Public License)

* 오픈소스 소프트웨어 공통 주제
  * 협업  
    도구 : Git, Github  
    공동 개발 규칙, 코드 리뷰, 회고

    
  * 빌드 시스템 (+ 패키지 관리 시스템)  
    개인 환경에 공개된 소스코드를 빌드(컴파일)&설치하기 어려운 경우가 빈번  
    pip, npm, stack, make, CMake, gradle, ant, maven, …

-------------
### Week2-1 버전 관리 개요
* Version Control System (VCS)  
이전 작업 버전으로 쉽게 돌아갈 수 있도록 **_시간 경과에 따른 파일을 기록하고 추적_** 할 수 있도록 하는 시스템
    
    * VCS software  
        CVS (Concurrent Version System)  
        SVN (Subversion)  
        Mercurial  
        Darcs  
        **Git**
        
    * Repository (저장소) - **Repo**
    
* General Actions in VCS
  * Checkin  
    : 로컬 저장소(Trunk in SVN, Branch in Git)에 파일 올리기  
    : check in (in SVN) | commit (in Git)
        
  * Checkout and editing  
    : 로컬 저장소에서 파일 가져오기 및 수정  
    : check out (in SVN) | fetch/pull (in Git)
        
  * Diffs  
    : 파일의 변경 내용 확인 및 비교
        
  * Branching  
    : 나뭇가지처럼 분기된 코드
        
  * Merging  
    : 두 branch 병합하기
        
  * Conflicts  
    : 두 branch 사이 서로 다른 변경사항이 있어 합쳐지지 않는 경우 (충돌) 
        
  * Tagging  
    : 특정 commit에 대해 라벨을 지정하여 버전을 가리키는 기능. 로그와는 다르다.
        

* Two Main Types of VCS
  * Centralized VCS (중앙 집중식 버전 관리)  
    : 많은 사용자가 있는 하나의 중앙 저장소  
    : 서버가 별도로 존재하며, 클라이언트가 중앙 서버에서 파일을 받아서 사용(Checkout)  
    : CVS, SVN, Darcs  
        
  * Decentralized (Distributed) VCS (분산 버전 관리 시스템)  
    : 모든 사용자는 자신의 로컬 저장소를 소유  
    : 별도의 원격(중앙) 저장소 (때로는 두 개 이상의 원격(중앙) 저장소)  
    : Git, Mercurial

-------------
### Week2-2 Git
* Introduction  
Git : 개발과정, 소스파일 등을 관리하는 도구  
개발되어온 과정, 역사를 볼 수 있고, 특정시점으로 복구가 가능

  * A distributed version control system (분산 버전 관리 시스템)  
    **Workspace** : files you are working with  
    **Index** : (staged) files to be considered in the next commit  
    **Local repository** : files committed to the local repo  
    **Remote repository** : files pushed to the remote repo
        
  * 명령어
    * git clone : 원격 저장소에 있는 것을 자신의 로컬 저장소로 복제
    * git add : 파일을 commit할 목록에 추가
    * git commit : 현재 작업물을 하나의 버전으로 기록(history의 한 단위)
    * git push : 현재까지 한 commits을 원격 저장소(Github)에 밀어넣기
    * git fetch : 원격 저장소에 있는 것을 현재 로컬 저장소로 가져오기 (이때, 원격 저장소에서 변경된 내용을 가져오지만 이러한 변경 사항이 로컬 저장소에 있는 작업물과 통합되지는 않는다.)
    * git merge : 두 개의 branch를 하나로 합치기
    * git pull : 원격 저장소에 있는 것을 현재 로컬 저장소의 디렉토리에 가져오고(fetch) 병합(merge)
    
  * Git **상태확인** 명령어
    * git show : 현재 branch의 최신 버전 확인
    * git log : 생성한 버전(commit) 내용 확인
    * git shortlog : git log 출력 요약 (각 commit은 작성자와 제목별로 그룹화)
    * git diff : 파일의 수정 내용 확인
    * git status : 현재 작업 중인 파일 상태 확인

* Workflow  
![git workflow](https://ibb.co/hXgZfRX)

-------------
### Week2-3 Github, fork, pull request
* Github  
: Git 도구를 응용한 사이트  
: 각종 Remote repository (원격 저장소) 들의 집합소


> Git과 Github의 차이는 무엇인가?  
> ⇒ Git은 각 컴퓨터(local)에 설치되어 소스코드관리가 가능한 프로그램이다. Github는 remote 저장소가 있는 외부서버를 지칭한다.
    

* fork  
: 상대방 Repository(저장소)를 복사해 자신의 Repository로 가져오는 기능  
: fork한 저장소는 내 소유이므로 마음대로 Source를 수정할 수 있다. _(이때, fork 저장소의 내용을 아무리 수정해도 원본 저장소에는 영향을 주지 않는다.)_  
    
* pull request  
: 내가 수정한 commit들을 원본 Repository에 반영(Pull)해줄 것을 요청(Reguest)하는 작업  
: 상대방 프로젝트를 복사(folk)해서 내 계정에서 관리되는 프로젝트로 새롭게 만들어 두고, 그 folk한 github 프로젝트를 토대로 새롭게 commit한 내용들을 pull-request 할 수 있다.
    

* Workflow  
![git workflow2](https://ibb.co/b6Yy685)
-------------
### Week3     Markdown
* Italics and Bold
    
    Italics : _ this _  (실제로는 띄워쓰기 없이 this와 _ 붙여야 한다.) |   _this_
    
    Bold : ** this **  (실제로는 띄워쓰기 없이 this와 * 붙여야 한다.)  |   **this**
    
    Italics + Bold : ** _ this _ **  (실제로는 띄워쓰기 없이 this와 _와 **을 붙여야 한다.) |   **_this_**
    
* Headers
    
    #this
    
    ##this
    
    ###this
    
    ####this
    
    #####this
    
    ######this
    
* Links
    
    인라인 링크 : [링크할 텍스트](링크할 주소)
    
    참조 링크 : [태그][참조 링크] ([참조 링크]: 링크 주소)
    
* Images
    
    인라인 이미지 링크 : ![링크할 텍스트](이미지 링크)
    
    참조 이미지 링크 : ![태그][참조 링크] ([참조 링크]: 이미지 링크)
    
* Blockquotes
    
    ">" : 인용구 앞에 ">"를 붙이면 된다.
    
* Lists
    
    "*, 1." : * 혹은 1. + 띄워쓰기(스페이스) 한 번 한 뒤에 문장을 적으면 된다.
    
* Paragraphs
    
    this   : 문장 뒤에 **스페이스를 두 번** 넣으면, 줄바꿈이 이뤄진다.
    

* Markdown tutorial  
![markdown](https://www.markdowntutorial.com/)
