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
  - `https://github.com/RiverDuck/TIL-practice.git`주소를 가진 원격 저장소를 origin이라 부르고, 해당 저장소를 즐겨찾기 함