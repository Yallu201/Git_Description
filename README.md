# Branch 와 Git-Flow

## **Git Branch**

모든 버전 관리 시스템은 브랜치를 지원합니다. 개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생깁니다. 코드를 통째로 복사하고 나서 원래 코드와는 상관없이 독립적으로 개발을 진행할 수 있는데, 이렇게 독립적으로 개발하는 것이 브랜치입니다.

예시 이미지1)
![git-branches-merge.png](./git-branches-merge.png)

예시 이미지1에서 원형 노드들은 각 브랜치에서의 `Commit` 혹은 `Merge` 포인트입니다. `Master`브랜치에서 뻗어나온 `Your Work`브랜치와 `Someone Else's Work`브랜치에서 각각 독립적으로 개발 후 `Master`브랜치로 다시 `Merge`하는 과정을 보이고 있습니다.

예시 이미지2)
![git_branch_merge.png](./git_branch_merge.png)

예시 이미지2에서 `master`, `new_feature`는 브랜치이름이며, 독립적으로 개발하기위한 분기명령을 `branch`라고도 합니다.

---

## **Git-Flow**

Git을 활용한 개발에서 `branch`를 효과적으로 사용하기 위한 방법중 하나로 `Git-Flow`가 있습니다.

Git-flow에는 5가지 종류의 브랜치가 존재합니다. 항상 유지되는 메인 브랜치들(`master`, `develop`)과 일정 기간 동안만 유지되는 보조 브랜치들(`feature`, `release`, `hotfix`)이 있습니다.

`master` : 제품으로 출시될 수 있는 브랜치  
`develop` : 다음 출시 버전을 개발하는 브랜치  
`feature` : 기능을 개발하는 브랜치  
`release` : 이번 출시 버전을 준비하는 브랜치  
`hotfix` : 출시 버전에서 발생한 버그를 수정 하는 브랜치

![git-flow_overall_graph.png](./git-flow_overall_graph.png)

### master 와 devleop브랜치

가장 중심이 되는 브랜치이며, 이 두 개 브랜치는 무조건 있어야 합니다.  
이름은 바뀔 수 있다만 웬만해서는 변경하지 않고 진행하도록 합니다.

<U>이 두 개의 브랜치는 삭제하면 안됩니다.</U>

### **master브랜치**

`release`브랜치에서 테스트가 끝나면 드디어 배포가되는 브랜치입니다.
가장검증이되고, 가장깨끗한 버전입니다.

브랜치 나오는 곳 : `없음`  
브랜치가 들어가는 곳 : `develop(최초1회)`, `hotfix`  
이름 지정 : `master`

출시된 `master`브랜치에는 버전`tag`를 추가합니다.

### **develop브랜치**

`develop`브랜치에는 상시로 버그를 수정한 커밋들이 추가되게 됩니다.
새로운 기능을 추가하는 경우 `develope` 브랜치에서 시작하는 `feature`브랜치를 생성합니다

브랜치 나오는 곳 : `master(최초 1회)`  
브랜치가 들어가는 곳 : `feature`, `release`  
이름 지정 : `develop`

### **feature브랜치**

새로운 기능을 추가하는 브랜치입니다.

브랜치 나오는 곳 : `develop`  
브랜치가 들어가는 곳 : `develop`  
이름 지정 : `master`, `develop`, `release-*`, `hotfix-*`를 제외한 어떤 것이든 가능.

기능 추가 작업이 완료되었다면, `feature`브랜치는 `develop` 브랜치로 `merge` 합니다. 여기서 머지를 할 때, `--no-ff` 옵션을 이용하여 브랜치에서 `merge`가 되었음을 git 기록에 남겨두도록 합니다.

`feature`브랜치는 `원격저장소`에는 반영하지 않고, <U>개발자의 `로컬저장소`에만 존재하도록 합니다.</U>

머지가 완료된 `feature`브랜치는 삭제하도록 합니다.

### **release 브랜치**

새로운 Production 릴리즈를 위한 브랜치입니다.  
`develop`브랜치에 이번 버전에 포함하는 모든 기능이 `merge`되었다면, QA를 위해 `develop`브랜치에서 `release`브랜치를 생성합니다.
QA를 무사히 통과하게되면 `relase`브랜치를 `master`와 `develop`브랜치로 `merge` 합니다.

QA를 진행하면서 발생한 버그들은 모두 `release`브랜치에서 수정합니다.
마지막으로 출시된 `master` 브랜치에는 버전 태그를 추가합니다.

브랜치 나오는 곳 : `develop`  
브랜치가 들어가는 곳 : `develop`, `master`  
이름 지정 : `release-*`

`release` 브랜치에서는 버그 픽스에 대한 부분만 커밋하고, 릴리즈가 준비되었다고 생각하면 `master`로 머지를 진행합니다. (이때도 `--no-ff` 옵션을 이용하여 머지하였음을 남깁니다.)

`master`로 머지 후 `tag`명령을 이용하여 릴리즈 버전에 대해 명시를 하고, `-s` 나 `-u` <key> 옵션을 이용하여 머지한 사람의 정보를 남겨두도록 합니다. 그런 뒤 `develop` 브랜치로 머지하여, `release` 브랜치에서 수정된 내용을 `develop` 브랜치에 반영합니다.

머지가 완료된 `release`브랜치는 삭제하도록 합니다.

### **hotfix 브랜치**

브랜치 나오는 곳 : `master`  
브랜치가 들어가는 곳 : `develop`, `master`  
이름 지정 : `hotfix-*`

Production에서 발생한 버그들은 전부 여기에서 수정합니다.  
수정이 끝나면, `develop`, `master` 브랜치에 반영하고, `master`브랜치에 `tag`를 추가합니다.  
만약 `release` 브랜치가 존재한다면, `release` 브랜치에 `hotfix` 브랜치를 머지하여 릴리즈 될 때 반영이 될 수 있도록 합니다.

머지가 완료된 `hotfix`브랜치는 삭제하도록 합니다.

---

### 장점

1. 명령어가 나와있다.
2. 웬만한 에디터와 IDE에는 플러그인으로 존재한다.

---

### 단점

1. 브런치가 많아 복잡하다.
2. 안 쓰는 브런치가 있다. 그리고 몇몇 브런치는 애매한 포지션이다.

---

### 출처

[우아한 형제들 기술블로그]  
https://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html

[잘 밤에 쓸데없는 생각하기... 블로그]  
https://ujuc.github.io/2015/12/16/git-flow-github-flow-gitlab-flow/
