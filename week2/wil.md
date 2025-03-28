## Fork, Star
+ Fork : 다른 사용자의 Repository를 복사해서 내 계정에 저장하는 기능이다.   
복사한 파일을 내가 수정해서, 그 수정한 버전을 남들에게 건의하려 할 때 사용한다.   
   
+ Star : 일종의 **북마크**다. 관심 있는 Repository나 프로젝트에 Star를 달면 두고두고 꺼내 볼 수 있다.   
   
-----
## Issue부터 Merge까지   
   
   + Issue : Repository에서 수정해야 하거나 추가해야 하는 기능을 추적 및 공유할 때 사용한다. Github에서 Issue 사항을 올려두면, 팀원들이 해당 Issue에 대한 조치를 진행한다.   
   
   + Branch : 큰 프로젝트에서 별도로 분기시켜 생성한 작업 공간을 의미한다. 우리가 Github에서 처음 Repository를 만들 때, 명령어에 있던 **main**도 Branch의 일종이다. Branch를 나무에 비유하자면, main은 나무의 기둥에 해당하고, main으로부터 별도로 분기시켜 생성한 작업 공간인 Branch는 나뭇가지에 해당한다.   
   Branch로 분기시켜 작업한 뒤, 나중에 Merge를 통해 그 나뭇가지를 큰 나무 기둥\(main)에 합병시킬 것이다.   

      - Branch Naming Convention : Branch의 이름을 짓는 것이다. commit message도 의미 있게 적어야 하듯이, Branch도 너무 막 지으면 남들이 한 눈에 알아보기 힘들다. 직관적이고 가독성 있는 이름을 짓자.   

         > 형식   
         >    
         > **type/\<issue 번호> - \<설명>**

   + Pull Request : 분기된 Branch를 다시 병합하기 위한 절차로, 이 과정에서 코드 리뷰를 통해 자신이 만든 작업물에 대한 검토가 이루어진다.   
   혹여나 자신의 작업물에 문제가 생겼는데 이를 발견하지 못하고 바로 상위 Branch에 Merge하면 문제가 발생할 수 있으므로, Pull Request와 코드 리뷰를 통해 검토하는 과정을 거친다.   
      - 코드 리뷰 : Branch로 분기시켜 수정한 코드를 다른 팀원들이 리뷰하는 것을 의미한다. 팀원들은 코드 리뷰를 통해 새로운 변경을 제안할 수 있다.   
+ Merge : Branch를 합병하는 과정이다. 총 3가지 옵션이 존재한다.   
    1. Merge Commit : 상위 Branch와 신규 Branch를 공통 부모로 갖는 새로운 commit을 만드는 것이다.   
          
    2. Sqush and Merge : 신규 Branch에서 나온 commit들을 몽땅 하나의 commit으로 통합시켜 상위 Branch에 생성한다.

    3. ~~Rebase and Merge~~ : 신규 Branch에서 나온 commit들의 base를 바꿔, 이 commit들을 모두 상위 commit에 올리는 것이다. 이 경우 바뀌는 commit들의 commit hash가 변경되고, 오류가 발생할 우려가 높아 잘 사용하지 않는다.   
---
## 실습
1. Repository - Issue에 들어간다.
![](https://velog.velcdn.com/images/tss9752/post/9da200c8-34e5-440f-b383-c856f8d38436/image.png)

2. **New Issue**를 눌러 새로운 Issue를 만든다. 적절히 제목과 내용을 정한 뒤 **Create** 버튼을 눌러 Issue를 생성한다.
![](https://velog.velcdn.com/images/tss9752/post/a67865f7-adac-4513-8d4f-a4e6b51018d9/image.png)


3. branch를 만든다. VScode에 들어가 terminal - Git bash 창에 다음을 입력한다.   
   + branch 생성 : **git branch "\<branch 이름>"**
      ![](https://velog.velcdn.com/images/tss9752/post/252ffe8a-912c-4959-bf6f-506a83af35be/image.png)
   \+  branch 확인하기, 삭제하기
      + 현재 branch 확인 : **git branch**   
      + 전체 branch 확인 : **git branch -a**  
      + branch 삭제 : **git branch "<브랜치 이름>"**

4. 만든 branch로 이동한다.
   + branch로 이동하기 : **git branch "<브랜치 이름>"**
   + branch 생성 후 이동하기 : **git checkout -b "<브랜치 이름>"**
   ![](https://velog.velcdn.com/images/tss9752/post/bb418c23-7f1e-4469-af03-b279049aac64/image.png)

5. branch에서 작업하기
   ![](https://velog.velcdn.com/images/tss9752/post/2e95eb43-20ea-4d2b-8a2c-29b756f5a368/image.png)
6. commit & push하기
    + 마지막 push할 때, git push origin main이 아닌
    **git push origin "<브랜치 이름>"** 으로 적어야 함을 기억하자. 
    ![](https://velog.velcdn.com/images/tss9752/post/b1ee5d40-2499-4c93-90ba-85f5ca4859d5/image.png)
   (중간에 오타나서 에러가 떴다.)
7. Pull Request 하기
   - 7-1. Repository로 돌아가면 다음과 같이 **Compare & pull request** 창이 뜬다. 클릭하면 된다.
   ![](https://velog.velcdn.com/images/tss9752/post/2030c097-343e-49de-9a55-040e553e96d0/image.png)   

   - 7-2. **Open a pull request** 창이 뜬다. Pull Request의 적절한 제목과 내용을 적자. 다 하면 **Create pull request**를 누른다.
   ![](https://velog.velcdn.com/images/tss9752/post/71bcd2fd-049a-4bb6-a099-1254e7b53576/image.png)

   - 7-3. 다음과 같이 pull request 창이 뜨면서, branch에서의 commit들과 코드 리뷰를 할 수 있는 댓글창이 생성된다.
   ![](https://velog.velcdn.com/images/tss9752/post/6441be6d-9895-439a-95a9-d6efe28ba7fb/image.png)
   ![](https://velog.velcdn.com/images/tss9752/post/e5212caa-86f6-4d1b-b4c7-3a8a5c23176b/image.png)
   (나 혼자 실습하다가 꼬여서 잡다한 commit이 추가됐는데, 그냥 무시하면 된다.)

8. Merge 하기   
   + **Merge pull request** 를 눌러 Merge한다. 
      ![](https://velog.velcdn.com/images/tss9752/post/5a88b708-e9fd-4326-844c-4ae57779cda3/image.png)
      이렇게 옵션이 3개가 뜰 건데, 나는 Sqush and merge로 했다.

      ![](https://velog.velcdn.com/images/tss9752/post/a70d6319-293a-4306-82fd-462f9037adf2/image.png)
      merge에 대한 commit message를 알맞게 적는다.

      ![](https://velog.velcdn.com/images/tss9752/post/4f85fb93-d699-4807-b175-a95e3e5daf03/image.png)
      완성!! 보라색으로 변하면서 무사히 상위 branch에 merge 됐다.   

      ❗ 다 쓴 branch는 방치하면 오류가 발생할 우려가 있으니, **Delete branch**를 눌러 삭제하자.
      ![](https://velog.velcdn.com/images/tss9752/post/1a899dde-9397-4732-9890-ee92afcaad53/image.png)

      Repository를 보면 무사히 test.md가 main branch에 들어간 것이 보인다.
      ![](https://velog.velcdn.com/images/tss9752/post/bcefc171-6495-4a77-846e-85de3887d04a/image.png)

--- 
(GDGoC 실습 확인용 링크)   
https://github.com/ez1hub/2025-1-Beginner-Study/pull/2

