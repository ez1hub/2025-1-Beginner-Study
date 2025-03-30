## 1. git의 정의와 github을 사용하는 이유   
예를 들어, 게임 업데이트를 한다고 하자.

- RPG v1 : 게임 출시!
- RPG v2 : 자잘한 버그가 수정되었습니다...
- RPG v3 : 여름 이벤트가 시작됩니다!
- RPG v4 : 여름 이벤트가 종료됩니다...
- RPG v5 : 대규모 업데이트가 시작됩니다!
.....

이 상황에서, 만약에 대규모 업데이트를 한 v5에 큰 버그가 생겨서 이전 버전으로(v4) 되돌아 가야 하는 상황이 벌어졌다고 하자. 만약 git이 없다면, v4 버전처럼 코드를 다시 일일이 복원하거나, 기존에 저장해놨던 v4 파일을 다시 찾아서 실행시키면 될 것이다.
문제는, 게임 제작 측면에서 이런 자잘한 버그 수정, 업데이트 내역은 수십개, 아니 수백개가 있을 것이다. 우리는 이 파일들을 좀 더 효율적으로 관리해야 할 필요가 있다. 만약 저 예시에서, v5 버전에 문제가 생기면 바로 v4 버전으로 돌아갈 수 있도록 돕는 파일 관리 시스템이 필요하다는 것이다.

그것을 가능하게 하는 것이 바로 git이다. 

* git이란? : **버전 관리를 위해 사용하는 오픈소스 소프트웨어**  

우리가 컴퓨터를 쓸 때도 [Ctrl + z]를 누르면 뒤로 되돌아 가듯이, 코딩 파일 관리 측면에 있어서도 그런 기능이 필요하다. 그리고 git은 그걸 가능하게 한다.

우리가 git을 사용하면...
* 잔뜩 쌓인 파일들을 효율적으로 관리할 수 있다.  
* 결과물의 버전 관리에 용이하다.  
* 코드의 수정을 관리하는 데에 용이하다.
    - 이슈 트래킹 : 올린 코드에 있는 에러, 이슈를 확인할 수 있다. 

근데 우리는 혼자 개발하지 않는다. 개발은 일반적으로 **협업**을 전제로 깐다고 할 정도다. 그렇다면 이 git을 다른 사람들과 공유하면서 사용할 수 있게끔 하면 어떨까? 그것이 바로 github다.

* github란? : **git으로 관리하는 프로젝트를 다른 사람들과 공유할 수 있는 사이트**

추가로 github을 사용한다면...
* 협업하여 프로젝트를 진행하는 데에 용이하다.   
    - Github actions : 코드 수정 내역을 기록한다.
    - Github projects : 프로젝트 관련 일정 등을 관리한다.   
--------------------------------------------------
## 2. github에 올릴 파일의 상태  
![](https://velog.velcdn.com/images/tss9752/post/4cb42422-fd3f-4964-9bf2-767445d83328/image.png)
단계를 차근차근 설명해 보겠다.

**1. untracked : 파일이 추적되지 않는 상태 (git에 올리지 않은 상태)**
우리가 코드를 짠다. 그러면 그 코드는 우리의 라이브러리에 저장되고, git에서 관리되고 있지 않다. 쉽게 말해서 코드만 짠 상태다.
이름이 untracked인 이유는, git에서 관리되지 않아서, 즉 **추적되지 않아서**다.

**2. tracked : 파일이 추적되는 상태 (modified, unmodified, staged)**
이제 우리는 코드를 git에 올려 관리해야 한다. 특정 명령어를 통해 우리가 1번에서 짠 코드 파일을 git에 등록하면 untracked 파일이 tracked, 즉 **추적 중인** 상태로 바뀐다. tracked는 modified, unmodified, staged 상태로 나뉘어서 설명할 수 있다.

+ unmodified : 파일이 수정되지 않은 상태 

+ modified : 파일이 작성, 수정된 상태  
우리가 git이나 github에 올린 파일에 수정사항이 생기면, 특정 명령어를 통해 이를 우리의 폴더 쪽으로 가져온다. 그리고 수정하여 다시 git에 올린다. 이때, 가져온 코드 파일이 아직 미수정 상태라면 unmodified, 수정되면 modified 상태가 된다.

+ staged : 파일이 repository(local repo)로 올라가기를 대기 중인 상태   
여기서 local repo는 **'내 컴퓨터에 있는 나만의 git'**이라고 생각하면 된다. 

추가로 관련 용어를 설명해 보겠다.
![](https://velog.velcdn.com/images/tss9752/post/9e461652-f6a6-45d0-8bc5-8dcca0c4f9fb/image.png)
+ Working directory : 업무 환경. 우리가 코드를 짜는 곳이다. 

+ Staging area : local repo(repository)에 가기 전에 파일을 대기시켜 놓는 공간이다.

+ local repo(repository) : 나만 쓸 수 있는 git이다.

+ remote repo : 쉽게 말해서 얘가 github다. remote repo란 남들에게 내 파일을 공유할 수 있도록 만들어 놓은 원격 가상 저장소이다. 그래서 github는 google drive과 같은 부류이기도 하다. 나중에 local repo(내 전용 git)에서 특정 명령어를 통해 remote repo(github)로 옮기면 내 파일을 공유할 수 있게 된다. 
--------------------------------------------------
## 3. github에 파일을 올리는 방법  
github 계정, VScode, git 파일을 준비한다.
1. 라이브러리에 **자신의 github 이름과 같은 이름의 폴더**를 만든다.
![](https://velog.velcdn.com/images/tss9752/post/f8493891-04b7-4bf8-af8d-a14ad891955f/image.png)

2. VScode에서 git 최초 설정을 해준다.
	2-1. new terminal 생성하기
    ![](https://velog.velcdn.com/images/tss9752/post/13856bca-f4b4-411f-a403-33eec0789f60/image.png)
	2-2. git bash하기
    ![](https://velog.velcdn.com/images/tss9752/post/9dc53892-1496-4031-9e9d-8811f2684d56/image.png)
    2-3. **.git 폴더**를 만들어 local repo를 만든다.
    (.git 폴더가 local repo다.)
    - 이는 git init이라는 명령어를 사용한다.
    - terminal 창에 git init을 입력한다.
    ![](https://velog.velcdn.com/images/tss9752/post/7f60fe44-d6bd-48d8-8820-8723ffb469e1/image.png)
	2-4. terminal 창에 다음을 입력한다.
    - git config --global user.name "<깃허브 이름>"
    - git config --global user.email “<깃허브 이메일>"
![](https://velog.velcdn.com/images/tss9752/post/1b8b47d0-8596-423d-8154-460b84ea5edd/image.png)
3. 1번에서 만든 폴더를 연다.
![](https://velog.velcdn.com/images/tss9752/post/1c1d2751-63fd-443d-9760-c18d69e13ff9/image.png)
4. 그 폴더 밑에 우리가 만들 새 파일을 생성한다.
![](https://velog.velcdn.com/images/tss9752/post/88ef03d0-91f6-4856-89ef-2406dffcd49b/image.png)

5. Working directory(작업을 하는 곳, 즉 일반 폴더)에서 코드를 짜거나 마크다운 문법을 이용해서 이것저것 한다.

자, 여기까지가 untracked 상태다. 이제 파일을 github에 올리자.
   ***  
6. git add 명령어를 terminal창에 입력해서 짠 코드를 staging area에 등록한다.
    + git add . 입력 : 모든 파일 한 번에 등록   
    + git add <파일명> : 파일 하나씩 등록   
    + git rm --cached < file > : unstaged로 파일 되돌리기
    ![](https://velog.velcdn.com/images/tss9752/post/bfe3afd0-1639-458b-acba-6ef810dc0b0e/image.png)

7. git commit을 통해 Local repo로 파일을 옮긴다.     
    + git commit -m "커밋 메세지"   
    + '커밋 메세지'(commit message)는 다른 사람들이 내가 올린 코드를 쉽게 알아볼 수 있도록 하는 일종의 제목이다. 
    예를 들어, A기능에서 발생한 에러를 수정했다고 하면, commit message를 
    **fix : A기능 에러 수정** 이라고 쓸 수 있겠다.
    ![](https://velog.velcdn.com/images/tss9752/post/a3d071f0-2f37-472c-b762-7349a9d20df3/image.png)
8. github에서 remote repo를 만든다. 자신의 github 계정에 들어가 repository를 만들면 된다.
![](https://velog.velcdn.com/images/tss9752/post/3a174aa9-ab94-46e3-a698-d43f818c7726/image.png)
    - 공개 범위에서 Public은 전체 공개, Private는 일부 공개다.
9. 아마 이런 창이 뜰 거다.
![](https://velog.velcdn.com/images/tss9752/post/1c668cd5-cc5c-4909-968c-5867846261b3/image.png)
여기서 아래에 있는 **…or push an existing repository from the command line**에 있는 명령어들을 복사한다.   
10. VScode terminal 창에 붙여넣기 한다.   
![](https://velog.velcdn.com/images/tss9752/post/8dac47c2-b832-42ed-ba33-9ff50d4d2715/image.png)
![](https://velog.velcdn.com/images/tss9752/post/c848e4b9-ef7d-4b2a-aae3-fd8ac463aa8b/image.png)

--------------------------------------------------    
    
출처 : 
<https://www.hanbit.co.kr/channel/category/category_view.html?cms_code=CMS2036561776>

<https://seonkyukim.github.io/git-tutorial/git-status/>


<https://vcloud-lab.com/entries/devops/-part-3-git-clone-version-control-integration-in-visual-studio-code>

<https://vcloud-lab.com/entries/devops/-part-3-git-clone-version-control-integration-in-visual-studio-code>

<https://vcloud-lab.com/entries/devops/-part-3-git-clone-version-control-integration-in-visual-studio-code>

