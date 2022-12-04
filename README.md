# TIL(Today I Learned)
 
## 2022-11-29
- HEAD : 현재 체크아웃한 브랜치의 가장 최신 커밋을 가리키는 포인터

## 2022-11-30
- 저장소 : 소프트웨어 개발을 위해 필요한 파일들이 모여있는 공간
  - `.git` 디렉터리가 있으면 저장소이고, 그렇지 않으면 일반 디렉터리이다.
- 브랜치 : A branch in Git is simply a lightweight movable pointer to one of these commits.
  - 브랜치는 어떤 ‘특정한 목표’를 가지고 코드를 수정하기 시작할 때 만든다.
  - 브랜치 생성 : `git branch 브랜치이름`
  - 생성된 브랜치 확인 : `git branch`
  - 해당 브랜치로 전환 : `git checkout 브랜치이름` or `git switch 브랜치이름`
  - 브랜치 생성과 전환 동시에 하기 : `git checkout -b 브랜치이름` or `git switch -b 브랜치이름`
  - 브랜치 병합 : `git merge 브랜치이름` <-- 현재 체크아웃하고있는 브랜치에 해당 브랜치가 병합됨
- 원격 저장소 즐겨찾기
  - git remote add origin https://github.com/RiverDuck/TIL-practice.git
  - `https://github.com/RiverDuck/TIL-practice.git`주소를 가진 원격 저장소를 origin 이라 부르고, 해당 저장소를 즐겨찾기 함

## 2022-12-04
- GitHub의 issue 관리하기

  - 목차
    1. 새로운 이슈 열기
    2. 로컬 저장소에 이슈 이름으로 브랜치 생성
    3. 이슈 해결
    4. 수정 사항 커밋 (GitHub가 해당 commit이 이슈와 관련있다는 것을 알도록 commit message안에 이슈번호를 적어야 한다.)
    5. master에 merge
    6. 이슈 닫기, 프로젝트 done, 브랜치 삭제
  
  - 새로운 이슈 열기
    - 깃헙 - issue - New issue 클릭
    - title과 상세 정보 기입한다.
    - Projects - github의 Projects를 만들었다면 Projects에서 불러온다.
    - Labels - Labels은 bug, docu 등 디폴스된 태그가 있으며, 커스텀으로 만들 수 있다.
    - milestone - 사전에 issue 탭에서 milestone를 만들고 반영합니다.
    - Submit new issue를 눌러 이슈를 만다.
  
  - 로컬 저장소에 이슈 이름으로 브랜치 생성
    - 이슈 생성시 나온 번호를 기반으로 브랜치를 생성한다.
    `git checkout -b 이슈번호`
  
  - 이슈 해결
    - 작업을 완료한다.
  
  - 수정 사항 커밋 & 푸시
    `git add .`
    `git commit`
    작성 시작 : 터미널 창이 뜨면 `i`를 누르고 - [이슈번호] 이슈 이름 - 뭐라뭐라 이슈를 했다1 - 뭐라뭐라 이슈를 했다2
    작성 종료 : 작성이 종료되면 `esc` - `:wq!`로 저장 및 vim 종료
    `git push origin 이슈번호`
  
    - GitHub에서 조금 전 만든 issue에 올린 commit message가 추적되었는지 확인한다.
  
  - pull request를 올리거나, master에 병합
    - 상황에 따라 pr(pull request)을 올리거나, master에 병합한다.
    `git checkout master` or `git switch master`
    `git merge 이슈번호`
    `git push origin master`

  - 이슈 닫기, 프로젝트 done, 브랜치 삭제
    - 이슈가 완료되었다면, `Close issue`로 닫는다.
    - Projects로 들어가서 만든 이슈를 `done`으로 바꾼다.
    - 완료된 리모트 브랜치, 로컬 브랜치를 삭제한다.
    `git push origin -d 이슈번호` && `git branch -d 이슈번호`

- Git commit message 수정
  - 목차
    1. 아직 커밋이 local에 있을 경우
    2. 이미 커밋을 push해, remote에 올린 상황인 경우

  - 아직 커밋이 local에 있는 경우
   아직 로컬에서 commit을 하고 push는 하지 않아 remote에 올라가지 않은 상태일 경우 다음과 같이 진행하면 된다.
    - 가장 최근의 commit 수정
     `git commit --amend`
     위와 같이 `amend`를 이용하면 가장 마지막에 commit한 내용을 수정할 수 있다.
     `git commit --amend`를 사용하고 커밋을 수정할 수 있는 창이 뜨면, 수정을 완료한 후 `esc` -> `:wq!`(저장 + 창 닫기)를 해주면 된다.
    - 더 오래된 commit 수정 or 한 번에 여러 commit 수정
     커맨드 라인에 `git log`를 입력한다.
     로그에서 여태 자신이 한 커밋을 쭉 확인 후, 어떤 커밋을 수정할 것인지 정한다.
      - 만일 위에서부터 세 번째 커밋을 수정해야 한다면
       `git rebase -i HEAD~3`
       위 커맨드를 사용하면 현재 작업 중인 브랜치의 가장 최근 commit 3개를 보여주게 된다.
       (3이 들어간 자리에 원하는 commit의 개수를 입력하면 된다.)
     이후 vim에서와 같은 방식으로 파일을 수정한 뒤, `esc` -> `:wq!`를 통해 커밋을 저장한다.
      - 수정이 잘 되었는지 `git log`를 통해 확인한다.
      
  - 이미 커밋을 push해, remote에 올린 상황인 경우
   커밋이 이미 remote에 적용된 상황이라면, `force`를 통해 수정된 커밋을 강제로 `push` 해주어야 한다.
    - GitHub의 공식 문서에 따르면 force pushing을 최대한 사용하지 않아야 한다고 한다.
    - 이는 push된 커밋의 로그를 갖고 있던 다른 팀원들이 로그를 수동으로 수정해줘야 하기 때문이다.
    - 따라서 commit을 할 때도 중요하지만, remote에 push하기 전에는 꼭 재확인할 필요가 있다.
   방법 자체는 간단하다.
   local에서 commit 메시지를 수정한 후, 아래 커맨드를 실행하면 된다.
   `git push --force 브랜치이름`