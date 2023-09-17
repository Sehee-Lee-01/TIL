# Code Review

> Code Review 관련 개념, 프로세스를 알아보기 위한 글

## Code Review란?

- 다른 개발자가 작성한 코드를 검토하는 것

## Code Review 왜 해야하는가?

- 코드의 일관성
- 로직 더블 체크
- 코드 중복 체크
  - 통일or 추상화
  - 복잡도 감소
- 함께 성장
  - 상향 평준화
  - 책임 공유

## 원활한 Code Review를 위한 태도

### 리뷰를 받는 사람

- 리뷰해야할 코드 양
  - 리뷰어가 리뷰해야할 코드 양을 고려하자.
  - 팀 내에서 **최소/최대 리뷰 단위**를 정하는 것도 좋을 것 같다.
- 가독성
  - 리뷰어가 코드를 읽기 쉽게 작성하자.
  - 코드 리뷰 **템플릿** 같은 것을 도입해도 괜찮을 것 같다.
- 테스트 플랜
  - 리뷰해야할 부분에서 어떤 테스트를 미리 해놓았는지 알려주자.
- ETC
  - 리뷰 비용을 줄이기 위해 PR 올리기 전에 최대한 고칠 것을 고치고 확인하고 올리자.
    - 커밋 컨벤션, 코드 스타일은 툴을 사용해서 쉽게 하도록 하고 PR에 올리기 전에 확인하자.
    - ESLint, Prettier 등
    - 커밋 메시지 템플릿
  - Context를 고려하여 명확하게 글을 올리자.

### 리뷰를 하는 사람

- Soft Skill
  - 리뷰를 받는 사람의 입장에서 생각하며 소프트하게 말하자.
  - 리뷰 툴로, 글로만 소통하게 되면 오해의 여지가 생길 수 있다.
- 정확하게, 명확하게 말하고, 이유를 함께 설명하자
  - 리뷰를 받는 사람이 이해하기 쉽게 설명하자.
- 남겨야할 것만 남기자
  - 너무 많은 피드백 보다는 **핵심적인 피드백**을 남기자.

### 모든 팀원

- 서로 공감, 존중하는 태도
  - 피드백이 편안한 분위기를 만들도록 노력해보기
  - 완벽한 코드는 없다. 목적에 따라 더 나은 코드가 있을 뿐이다.
- 적극적으로 리뷰에 참여하기
  - 서로의 코드에 책임감 가지기
  - 리뷰를 통해 서로 지식을 공유하고 성장하기
- 그라운드 룰 정하기
  - 커밋 컨벤션, 코드 스타일
  - 코드리뷰 시간, 날짜 정하기
  - 리뷰 중요도 표시, 리뷰어 지정 등
- 편한 작업을 위해 자동화 툴 도입도 고려해보기
  - 슬랙 알림과 깃허브 연동 등
  - **좋은 방법이라고 생각하는 방식을 무조건적으로 도입하는 것 보다는 서로의 상황에 맞는 방법 찾아가고 정하기**

## 용어 정리

- Pn 규칙

  - 커뮤니케이션을 줄이기 위한 규칙
  - 리뷰어가 코멘트를 강조하고 싶은 정도를 표시하는 방법
  - 예시
    - P1: 꼭 반영(Request changes)
    - P2: 적극적 고려(Request changes)
    - P3: 웬만하면 반영(Coment)
    - P4: 반영하거나 넘어가거나 Ok(Approve)
    - P5: 사소한 의견(Approve)

- D-n 규칙

  - 코드 리뷰의 우선순위를 표시하는 방법
  - 보통 MR(Merge Request) 제목에 표시하거나 라벨 등을 사용
  - 라벨을 자동화 하는 방법도 있다.
    - [Gitlab에서 D-n 규칙을 사용하는 방법](https://docs.gitlab.com/ee/user/project/merge_requests/merge_request_approvals.html#approvals-before-merging)
  - 예시
    - D-0: 반드시 리뷰해야하는 사항
    - D-1: 반드시 리뷰해야하는 사항
    - D-2: 리뷰해야하는 사항
    - D-3: 리뷰해도 되는 사항
    - D-4: 리뷰하지 않아도 되는 사항
    - D-x: 적당한 기간 내에 리뷰해도 되는 사항

- Code Coverage

  - 테스트 코드가 얼마나 코드를 커버하는지를 나타내는 지표

    - 테스트 코드가 커버하는 코드의 비율
    - 테스트 코드를 작성할 때, 테스트 코드가 얼마나 많은 코드를 커버하는지를 확인할 수 있다.

  - 측정 기준

    - 함수(Function): 각각의 함수가 얼마나 실행되는지
      - ex) 테스트 진행시 4개 중 함수가 3개 실행되었다면 75%의 커버리지
    - 구문(Line): 구문 중 몇 줄이 실행되는지
      - ex) 테스트 진행시 10줄 중 8줄이 실행되었다면 80%의 커버리지
    - 결정(Descision): if, switch 등의 조건문에서 각각의 조건이 얼마나 실행되는지
      - ex) 테스트 진행시 조건문의 전체 조건식이 True가 최소 1번, False가 최소 1번 실행되었다면 기준 만족
    - 조건(Condition): 전체 조건식이 아닌 개별 조건식을 기준으로 판단
      - 개별 조건식이 모두 True, False가 최소 1번 실행되었다면 기준 만족
      - ex) 테스트 진행시 조건문(`if (x>0 && y<0)`)에서 `x>0`, `y<0`이 각각 True가 최소 1번, False가 최소 1번 실행되었다면 기준 만족
    - 조건/결정(Condition/Decision): 조건 커버리지와 결정커버리지 모두를 만족할 때 충족

- Code Smell

  - 더 깊은 문제를 나타낼 수 있는 프로그램 소스 코드 의 특성

- Git Branch 전략

  - Git 브랜치를 효과적으로 관리하기 위한 워크플로우
  - 예시
    - Git Flow
      - Master, Develop, Supporting(Feature, Release, Hotfix) 브랜치를 사용
      - 브랜치 용도
        - Master, Develop: 영구적인 브랜치
          - Master: 배포 가능한 상태의 코드만 유지
          - Develop: 개발 중인 코드만 유지
        - Supporting: 일정 기간 동안만 유지되는 브랜치
          - 병렬적 업무 가능
          - Feature: 새로운 기능 개발
          - Release: 배포 준비
          - Hotfix: 긴급한 버그 수정
      - 한계
        - 웹 애플리케이션에는 그다지 적합하지 않다.
          - 명시적으로 버전관리가 필요한 어플리케이션, 오픈소스 라이브러리/프레임워크에 더 적합하다.
          - 웹은 특성상 항상 최신의 단일 버전만을 사용하게 된다.(단일 릴리즈 버전)
            - 자유롭게 몇번씩 릴리즈 될 수 있다.
    - Github Flow(간단 버전)
      -Git Flow의 단점을 보완하기 위해 나온 더 간단한 전략
      - 웹 개발에 더 적합하다.
      - CI/CD를 실천하기 적합한 브랜치 전략
      - 브랜치 용도
        - Master: 배포 가능한 상태의 코드만 유지
        - Topic: 새로운 기능 개발
          - 명확한 네이밍이 중요하다.
          - 별도로 Hotfix 브랜치를 만들지 않고 Topic 브랜치에서 진행

- 저 문맥(Low Context) 커뮤니케이션
  - 상대방이 내가 아는 것을 알고 있을 것이라 가정하지 않고 충분한 문맥 전달하는 것.
- 코딩 스타일(컨벤션)
  - 코드 작성 가이드라인
  - 예시: [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
- CI/CD
  - CI(Continuous Integration): 지속적인 통합
    - 빌드, 테스트, 병합 등의 과정을 자동화
    - ex) Github Action
  - CD(Continuous Delivery & Continuous Deployment): 지속적인 서비스 제공/ 배포
    - Continuous Delivery: 공유 레포지토리에 자동 Release
    - Continuous Deployment: Production 레벨까지 자동 deploy
  - 예시
    - Jenkins
      - 파이프라인을 통해 CI/CD를 구현할 수 있다.
- TDD(Test Driven Development, 테스트 주도 개발)
  - 개발 전 테스트 코드를 먼저 작성하는 방법
    - 테스트가 성공할 수 있을 만큼의 기능만을 개발하는 방법
    - 그 후 리팩토링을 통해 코드를 개선하는 방법
  - 장점
    - 요구사항을 점검할 수 있다.
    - 사용자 관점에서 코드를 작성할 수 있다.
    - 시스템의 설계를 도와준다.
    - 개발 집중도를 높여준다.
  - 테스트란? 코드가 예상한대로 정상적으로 동작하는지 확인하는 것
- 유닛 테스트
  - 개별 기능이 의도된 대로 동작하는지 확인하는 테스트
  - 장점
    - 원하는 부분만 빠르게 테스트할 수 있다.
    - 리팩토링이 안정적이다.
    - 코드의 문제점을 빠르게 찾을 수 있다.
  - `@ParameterizedTest`를 사용하면 테스트 코드를 간결하게 작성할 수 있다.
  - FIRST 원칙
    - Fast: 빠르게 진행되어야 한다.
    - Independent: 독립적으로 동작해야한다.
    - Repeatable: 어떤 상황이던 예상한 대로 결과가 나온다.
    - Self-Validating: 테스트 자체적으로 결과가 나와야한다.(출력x, 로그x)
    - Timely: 적시에 테스트를 철저하게 작성해야한다.

## Github에서 코드 리뷰를 하는 방법(영상)

- [Github으로 팀 프로젝트 하기 1편 | Pull request 코드리뷰 개발자](https://www.youtube.com/watch?v=9FZaYz0s8s4)
- [github을 기반으로한 온라인 코드 리뷰 방법](https://www.youtube.com/watch?v=a5c9ku-_fok)
- [깃허브로 그룹프로젝트 하는 법 | 그냥 이거보고 따라하면 됨 | 브랜치 전략, 충돌해결, 코드리뷰 싹다 알려드림](https://www.youtube.com/watch?v=tkkbYCajCjM)

## 참고 자료

### 참고 글

- [코드 리뷰 프로세스를 도입/개선하고자 하는데 어떻게 해야할까요](https://medium.com/elecle-bike/코드-리뷰프로세스를-도입-개선하고자-하는데-어떻게-해야할까요-1e5df5f8949b)
- [효과적인 코드 리뷰를 위해서 - LINE](https://engineering.linecorp.com/ko/blog/effective-codereview#linting-code-style-check)
- [코드 리뷰 in 뱅크샐러드 개발 문화 - BankSalad](https://blog.banksalad.com/tech/banksalad-code-review-culture/)
- [코드 리뷰는 어떻게 하나요?](http://sv-story.blogspot.com/2013/04/blog-post_28.html)
- [글로벌기업은 코드 리뷰를 어떻게 할까요? - SamsungSDS](https://www.samsungsds.com/kr/insights/global_code_review.html)
- [Code Review Developer Guide - Google](https://google.github.io/eng-practices/review/)
- [Google Java Style Guide - Google](https://google.github.io/styleguide/javaguide.html)
- [공통시스템개발팀 코드 리뷰 문화 개선 이야기 - 우아한기술블로그](https://techblog.woowahan.com/7152/)
- [코드 커버리지(Code Coverage)란?](https://hudi.blog/code-coverage/)
- [코드 냄새 - wikipedia](https://en.wikipedia.org/wiki/Code_smell)
- [Git 브랜치 전략 (feat. Git Flow, Github Flow)](https://hudi.blog/git-branch-strategy/)
- [코딩스타일 (Coding Style)이란? 코딩 스타일 알아보기](https://digiconfactory.tistory.com/entry/%EC%BD%94%EB%94%A9%EC%8A%A4%ED%83%80%EC%9D%BC-Coding-Style%EC%9D%B4%EB%9E%80-%EC%BD%94%EB%94%A9-%EC%8A%A4%ED%83%80%EC%9D%BC-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0)
- [CI/CD란 무엇인가 (Feat. DevOps 엔지니어)](https://artist-developer.tistory.com/24)

### 참고 영상

- [코드 리뷰 잘 하는법 (ft. 개발자랑 일 잘하는 치트키)](https://youtu.be/VaaRvs8YU1M?si=lpPn7xVYJUFNdVqy)
- [Github으로 팀 프로젝트 하기 2편 | conflict 해결 개발자](https://www.youtube.com/watch?v=FmLzvXyFKIE)
- [우리 팀의 코드리뷰 문화, 이렇게 조금씩 발전했어요! #우아콘2022 #Day3\_함께하고성장하는우리](https://www.youtube.com/watch?v=PBFUwGPp8DY)
- [코드 리뷰의 또 다른 접근 방법: Pull Requests vs. Stacked Changes | 인프콘 2022](https://www.youtube.com/watch?v=XRZPkYnWa48)
- [CI/CD 5분 개념 정리 (현업에서 쓰는 개발 프로세스)](https://www.youtube.com/watch?v=0Emq5FypiMM)
- [제발 깃허브 액션🔥 모르는 개발자 없게해 주세요 🙏](https://www.youtube.com/watch?v=iLqGzEkusIw&t=14s)
- [What Is Jenkins? | What Is Jenkins And How It Works? | Jenkins Tutorial For Beginners | Simplilearn](https://www.youtube.com/watch?v=LFDrDnKPOTg)
- [테스트 코드와 TDD 🧪(feat. 프론트엔드, 백엔드를 위한 테스트 코드)](https://www.youtube.com/watch?v=Npi21gLIEZM)
- [[10분 테코톡] 제이의 단위 테스트](https://www.youtube.com/watch?v=mIO4Rbe_M74)
