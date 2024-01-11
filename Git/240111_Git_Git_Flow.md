## Git 브랜치 전략

- 여러 개발자가 하나의 저장소를 사용하는 환경에서 저장소를 효과적으로 활용하기 위한 work-flow
- branch 생성에 규칙을 만들어서 협업을 유연하게 하는 방법론
- branch를 활용한 변경 이력 관리 전략

## Git Flow 전략

- feature > develop > release > hotfix > master
- 정기 배포, 버저닝이 필요한 애플리케이션에 적합함
  <img src='./assets/git_flow.png'>

### 구조

- master : 라이브 서버에 제품으로 출시되는 브랜치
- develop : 다음 출시 버전을 대비하여 개발하는 브랜치
- feature : 추가 기능 개발 브랜치. develop 브랜치에 들어감
- release : 다음 버전 출시를 준비하는 브랜치. develop 브랜치를 release 브랜치로 옮긴 후 QA, 테스트를 진행하고 master 브랜치로 합침
- hotfix : master 브랜치에서 발생한 버그를 수정

### 메인 브랜치 (필수)

- `master` : 배포 가능한 상태 만을 관리하는 브랜치
- `develop` : 다음에 배포할 것을 개발하는 브랜치
  - 통합 브랜치의 역할을 하며, 평소에는 이 브랜치를 기반으로 개발 진행

### 보조 브랜치

- 새로운 기능을 추가할 때 주로 사용하는 가지
- develop 브랜치로부터 가지가 뻗어나오고, 다시 합쳐짐
  - develop : 기존에 잘 작동하는 개발 코드
  - 보조 브랜치 : 새로 변경될 개발코드를 분리하고 각각 보존

### 릴리즈 브랜치 `release-*`

- 배포를 위한 최종적인 버그 수정 등의 개발 수행
- 새로운 제품을 배포하고자 할 때 사용
- 배포 가능한 상태가 되면 master 브랜치로 병합시키고, 출시된 master 브랜치에 버전 태그를 추가함
- 해결 후 develop에도 머지 필요

### 핫픽스 브랜치 `hotfix-*`

- 배포한 버전에서 긴급하게 수정할 필요가 있을 때 master 브랜치에서 분리
- 해결 후 develop에도 머지 필요

## Git Flow 흐름

<aside>
☑️ Point

- 대부분의 작업은 develop에서 취합
- master가 아닌 가지들은 master의 변동사항 꾸준히 주시 필요
</aside>

1. 신규 기능 개발
   1. 개발 전 : develop → feature
   2. 개발 후 : feature → develop
2. 라이브 서버로 배포
   1. QA : develop → release
   2. 오류 확인 : release에서 수정
   3. 테스트 완료 : release → master
3. 배포 후 관리
   1. 라이브 서버 버그 발생 : master → hofix
   2. 종료된 버그 픽스 동기화 : hofix → master, develop

---

### 참고 자료

1. [https://inpa.tistory.com/entry/GIT-⚡️-github-flow-git-flow-📈-브랜치-전략?category=890999](https://inpa.tistory.com/entry/GIT-%E2%9A%A1%EF%B8%8F-github-flow-git-flow-%F0%9F%93%88-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%A0%84%EB%9E%B5?category=890999)
2. https://techblog.woowahan.com/2553/
3. https://blog.hwahae.co.kr/all/tech/9507
