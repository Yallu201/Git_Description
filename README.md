# Git 사용규칙

### 작업을 할 때 지켜야할 서로 간의 약속

1. 작업을 시작하기 전에 JIRA 티켓을 생성합니다.
2. 하나의 티켓은 되도록 하나의 커밋으로 합니다.
3. 커밋 그래프는 최대한 단순하게 가져갑니다.
4. 서로 공유하는 브랜치의 커밋 그래프는 함부로 변경하지 않습니다.

---

### 커밋 단위

    커밋 하나는 하나의 의도와 의미만을 가져야 합니다.
    한번에 여러 파일을 수정하더라도 그 의도는 단 하나여야 한다는 것입니다.
    그것이 버그 수정이든 새로운 기능 추가든 말입니다.

    파일을 하나만 수정하더라도 두 개 이상의 의도가 있다면 하지 말하야 합니다.
    버그 수정과 새 기능 추가를 동시에 하지 않아야 합니다.

---

### 커밋 메시지 작성규칙

1. 제목과 본문을 한 줄 띄워 분리하기
2. 제목은 영문 기준 50자 이내로
3. 제목 끝에 `.` 금지
4. 제목은 `명령조`로
5. 본문은 영문 기준 72자마다 줄 바꾸기
6. 본문은 `어떻게`보다 `무엇을`, `왜`에 맞춰 작성하기
7. 커밋 메시지 앞에 JIRA 티켓번호 입력하기

> 자세한 내용은 아래 링크를 참조해주세요:D

---

### 커밋 메시지 예시

**권장 형식**

```
[JIRA Ticket Number] [Category] [Simple title]

[Detailed description]
```

**예시( OTC 내부문서 관련)**

```
OTC-000 [AA증권] XXX 모듈 수정

무슨이유로
~~~
~~~
~~~
~~~
~~~
을 수정했다.
```

> JIRA 티켓번호의 경우, Git Hook을 이용하면 Branch명을 통해 자동으로 입력이 가능합니다.
> ( 하단 링크 참조 )

---

### 출처

[우아한형제들 기술블로그]
https://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html

[프로젝트를 위한 협업 준비 규칙]
https://nomad-programmer.tistory.com/35

[좋은 git 커밋 메시지를 작성하기 위한 7가지 약속]
https://meetup.toast.com/posts/106

[이상한모임]
http://blog.weirdx.io/post/33832

[커밋 메세지에 JIRA 이슈번호 자동으로 넣어주기]
https://medium.com/prnd/github-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%84%B8%EC%A7%80%EC%97%90-jira-%EC%9D%B4%EC%8A%88%EB%B2%88%ED%98%B8-%EC%9E%90%EB%8F%99%EC%9C%BC%EB%A1%9C-%EB%84%A3%EC%96%B4%EC%A3%BC%EA%B8%B0-779048784037

[JIRA 에서 스마트 커밋(Smart commit) 사용하기]  
https://www.lesstif.com/jira/jira-smart-commit-51282248.html
