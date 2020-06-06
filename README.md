# Git 과 SVN

**Git & SVN**

`Git`과 `SVN`은 모두 버전관리를 위한 프로그램입니다.
다만, 소스코드 및 이력관리의 체계가 조금 다릅니다.

`SVN`은 중앙서버에서만 소스코드와 히스토리가 관리됩니다.  
`Git`은 개발자 개인PC에서도 따로 소스코드및 히스토리관리가 가능합니다.  
또한 `GitHub`, `GitLab`등 원격저장소를 지원하는 서비스를 이용하여
개발자들 사이의 협업이 가능합니다.

---

**Client**

`Git`과 `SVN`모두 CLI 명령어를 입력하여 모든 기능을 실행할 수 있습니다.  
 그러나 좀더 편하게 이용하기위한 클라이언트들이 존재합니다.

`SVN`은 현재 `TortoiseSVN`을 이용하고 있습니다.  
`Git`은 `SourceTree`가 있으며, `GitBash`, `git-gui`등 다양한 클라이언트가 존재합니다.  
(작성자는 직접 명령어를 입력하는 `GitBash`를 사용합니다. )

---

**Command**

`SVN`사용자가 `Git`으로 넘어오는데 어려운 가장 큰 이유는  
`명령어`의 `의미`가 조금씩 다르기 때문입니다.

`SVN`의 `Checkout`은 중앙서버에서 저장소를 복제하는 명령입니다.  
`Git`의 `Checkout`은 브랜치 전환 명령입니다.

`SVN`의 `Commit`은 중앙서버로 소스코드를 반영하는 명령입니다.  
`Git`의 `Commit`은 개인PC 저장소에 변경이력을 만드는 명령입니다.

아래는 `Git`과 `SVN` 명령어를 비교한 테이블입니다.

| 조작                            |           Git            |   Subversion    |
| :------------------------------ | :----------------------: | :-------------: |
| 저장소의 복제                   |        git clone         |  svn checkout   |
| 커밋                            |        git commit        |   svn commit    |
| 커밋의 상세내용을 확인하고 싶다 |         git show         |     svn cat     |
| 상태 확인                       |        git status        |   svn status    |
| 변경 내용 확인                  |         git diff         |    svn diff     |
| 로그 확인                       |         git log          |     svn log     |
| 추가                            |         git add          |     svn add     |
| 이동                            |          git mv          |     svn mv      |
| 삭제                            |          git rm          |     svn rm      |
| 변경 취소                       | git checkout / git reset | svn revert (※1) |
| 브랜치 작성                     |        git branch        |  svn copy (※2)  |
| 브랜치의 전환                   |       git checkout       |   svn switch    |
| 병합                            |        git merge         |    svn merge    |
| 태그 작성                       |         git tag          |  svn copy (※2)  |
| 변경 사항 업데이트              |   git pull / git fetch   |   svn update    |
| 원격 저장소에 반영              |         git push         | svn commit (※3) |
| 무시할 파일 목록                |        .gitignore        |   .svnignore    |

※1. SVN의 revert는 변경 취소이지만 Git의 revert는 삭제 용 커밋으로서 같은 명령어라도 의미가 서로 다르다.

※2. SVN에서는 브랜치와 태그는 구조상 동일하지만 Git에서는 그 의미가 서로 다르다.

※3. SVN에서는 로컬 저장소/원격 저장소라는 개념이 없기 때문에 커밋하면 즉시 원격으로 반영되지만, Git에서는 로컬 저장소에 반영(commit) 및 원격 저장소에 반영(push) 방법이 다르다.

( 출처: https://backlog.com/git-tutorial/kr/reference/git-svn.html )
