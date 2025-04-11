## 브랜치 전략
브랜치 관리의 필요성 : 서로의 작업에 영향을 주지 않기 위해 브랜치의 구분 필요
각 브랜치가 어떤 작업을 위해 존재하는지 구분 필요
main 브랜치(배포를 위한 브랜치)의 안전한 관리 필요 -> 브랜치 보호 규칙 : 승인 없이 pr이나 push 가능자를 제한할 수 있음
결론 : 충돌을 방지하자

---
1. git flow
브랜치의 종류를 main branch(main - 상용화용 브랜치, develop - 개발 서버용 브랜치), supporting branches(feature, release, hotfix)로 나눔

 - main : 프로젝트 생성 시 기본으로 생성되는 브랜치. 절대 지우면 안 됨 (그래서 브랜치 보호 규칙 적용 가능함)
 - develop : main과 같이 영원히 존재하는 두번째 브랜치 (feature 브랜치를 병합시키거나 새로 만들 때 사용하는 브랜치임)
 - feature : develop 브랜치에서 분기시켜 작업하는 곳. 개발 완료 후 pr과 코드 리뷰와 머지를 거쳐 develop으로.
 - release : 배포를 준비하는 브랜치. 딱히 쓸 일이 없다? 자잘한 버그를 수정하고 QA 작업.
 - hotfix : 즉각적 수정이 필요할 때 사용. main 브랜치에서 분기시킨다. main과 develop 모두에 병합시켜야 한다.

문제점 : main으로 들어오는 과정이 너무 길다. merge 가 너무 잦다는 지적.
-> 대안 : github flow를 쓰자.

---
2. github flow
수시로 배포되는 상황이 git flow(시간이 너무 오래 걸리는 방법)과 안 어울린다는 지적 속에서 나온 전략. main과 feature만 쓴다.
 - feature : 여기서 모든 작업이 이루어짐. 작업 후 다시 main으로 바로 병합함. 브랜치 naming과 코드 리뷰가 더 중요해짐

> github flow vs git flow ? -> 각각의 장단점이 있다. 적재적소에 사용.

---
## 개발자로서의 Attitude

- convention을 만들어 사용하자. : 프로젝트의 질을 높일 수 있다. (최대한 자세하게)
- 코드에 대한 주인 의식을 갖자 : 코드를 최대한 잘 설계하도록 노력하자.