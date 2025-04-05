## 1. git log, git status   
- git log : 파일의 commit 기록을 최신 순으로 확인할 수 있다.   
    + **--oneline** 옵션을 붙이면 commit 기록을 한 줄로 요약하여 볼 수 있다.   
    > 사용법 : **git log --online**

    + commit id : commit의 고유번호(id)
    + HEAD : 현재 사용 중인(작업 중인) branch의 최신 commit
- git status : 작업 중인 파일의 상태를 확인한다.(untracked, modified... 등)

---
## 2. commit 수정하기 : amend, reset, revert
### amend 
가장 최근 commit을 **완전히 새로운 commit으로 수정하여** 변경한다. 그래서 해당 commit id도 바뀌게 된다.   

사용법은 다음과 같다.
1. **git commit --amend** : vim을 통한 commit message 수정   

terminal 창에 수정하고 싶은 commit id를 이용하여 amend 하자.
![](https://velog.velcdn.com/images/tss9752/post/6e5c7f42-828a-41d3-bed0-46002518afe9/image.png)
amend를 했더니, vim이 뜨면서 commit message를 쓸 수 있는 공간이 마련됐다. 맨 위 갈색 영역에서 적절한 commit message를 작성하면 된다.   
작성 후, 저장하기 위해서는 ```esc -> :키 -> w키 -> q키 -> enter``` 순으로 입력하면 commit message를 저장 후 vim 창을 닫을 수 있다.

![](https://velog.velcdn.com/images/tss9752/post/3752cbeb-6462-40ba-b038-7594beffb41f/image.png)
amend를 완료하고 git log를 봤더니 아까 작성한 commit message가 있는 log가 맨 위에 있다. 주목할 점은, amend 전 맨 위에 있었던 commit id인 **483f2b7**이 

2. **git commit --amend -m "\<commit message>"** : vim에 진입하지 않고 바로 commit message를 수정한다.   

3.  **git commit --amend --no edit** : commit message를 수정하지 않고 commit을 수정한다.
