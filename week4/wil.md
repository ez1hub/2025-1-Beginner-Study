## Branch Strategy
당연하지만 프로젝트를 하면서 쓰는 Git 내에서 branch 관리가 잘 되어야 할 것이다.   
가령 웹 페이지를 만드는 프로젝트에서 로그인 기능을 구현하는 작업 공간과 검색 기능을 구현하는 작업 공간이 같은 곳에 있다고 하자. 물론 작업 자체가 불가능한 것은 아니지만, 매우 혼란스러울 것이다. 그리고 내 작업이 다른 사람의 작업에 영향을 줄 수 있다는 우려도 있다.    
그래서 서로의 작업에 영향을 주지 않기 위해, 그리고 각 branch가 어떤 작업을 위해 존재하는지 구분하기 위해 branch를 나누는 전략이 필요하다.   

이번 글에서는 branch의 전략 중 **git flow**와 **github flow**에 대해서 알아볼 것이다.

---
1. **git flow**   
브랜치의 종류를 main branch(main - 상용화용 브랜치, develop - 개발 서버용 브랜치), supporting branches(feature, release, hotfix)로 나누는 전략이다.   

 - **main** : 프로젝트 생성 시(repository 생성 시) 기본으로 생성되는 브랜치이다.    
 보통 main branch는 실 사용자들이 쓰는 버전을 제공하는 branch이기 때문에, main이 삭제되면... ~~이 이상의 설명은 생략한다.~~    
 그래서 main branch 경우의 안전한 관리를 위해 **branch 보호 규칙**을 적용하여 승인 없이 PR이나 push 가능자를 제한할 수 있다.

 - **develop** : main과 같이 영원히 존재하는 두번째 브랜치이다.    
 feature 브랜치를 병합시키거나 새로 만들 때 사용하는 브랜치이다.   

 - **feature** : develop branch에서 분기시켜 작업하는 곳이다.    
 우리가 코드를 짤 때 사용하는 진짜 공간이라고 생각하면 된다. feature에서 개발 완료 후 PR과 코드 리뷰와 Merge를 거쳐 develop branch로 간다.   

 - **release** : 배포를 준비하는 branch이다.    
 자잘한 버그를 수정하고 QA 작업을 할 때 쓴다.   

 - **hotfix** : 즉각적 수정이 필요할 때 사용하는 branch다.   
 develop이나 feature과 달리 main 브랜치에서 분기시킨다. 개발 후에는 main과 develop 모두에 병합시켜야 한다.

![](https://velog.velcdn.com/images/tss9752/post/938a3cc6-9672-4cb9-b324-079d34d41ef8/image.png)
(git flow를 표현하는 사진)   

단점이 있다. main으로 들어오는 과정이 너무 길다는 것이다. 최초 main부터 시작해서 다시 main으로 들어오기까지 적어도 5번(```main → develop → feature → develop → release → main)이 걸린다. 여기에 develop으로 다시 넘어간다면 더 늘어난다. 이를 개선해보자는 목소리가 나오기 시작했고, 그 대안이 github flow이다.

---
2. **github flow**   
수시로 배포되는 요즘 application 시장이 git flow와 안 어울린다는 지적 속에서 나온 전략이다. git flow와 달리 main과 feature branch만 쓴다.   
 - **feature** : git flow와 달리 여기서 모든 작업이 이루어진다. 작업 후 다시 main으로 바로 병합한다. 그래서 git flow보다 branch naming과 코드 리뷰가 더 중요하다.   

![](https://velog.velcdn.com/images/tss9752/post/4d5976f9-f3de-460d-9358-f3b49f45f24b/image.png)    
(git flow를 표현하는 사진)   

하지만 그렇다고 해서 github flow가 git flow보다 우월하다는 것은 아니다. 각각의 장단점이 있으니, 적재적소에 사용하면 된다.

---
## + 개발자로서의 Attitude

1. convention을 만들어 사용하자    
앞선 글에서 commit message를 작성하는 거나 branch naming을 할 때, 가독성이 높고 직관적인 이름을 지어야 한다고 했다. 이는 프로젝트의 완성도를 높일 수 있을 뿐만 아니라 나중에 버전을 확인하거나 수정해야 할 때 원활하게 할 수 있도록 한다. 최대한 자세하게, 직관적인 이름을 짓다.    

2. 코드에 대한 주인 의식을 갖자    
public repository(하물며 내가 지금 쓰는 이 글도) 결국에 나를 타인에게 보여주는 얼굴이다. 단순히 돌아가기만 하는 코드가 아닌, 정말 완성도가 높은 코드를 짜려는 자세를 가지자.

---
출처   

<https://medium.com/daangn/%EB%A7%A4%EC%9D%BC-%EB%B0%B0%ED%8F%AC%ED%95%98%EB%8A%94-%ED%8C%80%EC%9D%B4-%EB%90%98%EB%8A%94-%EC%97%AC%EC%A0%95-1-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%A0%84%EB%9E%B5-%EA%B0%9C%EC%84%A0%ED%95%98%EA%B8%B0-1a1df85b2cff>