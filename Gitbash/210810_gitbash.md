### Git bash 오류

- Remote에 변경사항이 있는데 Local에 update 하지 않고 그냥 push 하는 경우 오류 발생

  ```bash
  $ git push origin master
  To https://github.com/Junghyun-B/test.git
   ! [rejected]        master -> master (fetch first)
  error: failed to push some refs to 'https://github.com/Junghyun-B/test.git'
  ```

  

- Remote 작업 != Local 작업

  ```bash
  hint: Updates were rejected because the remote contains work that you do
  hint: not have locally. This is usually caused by another repository pushing
  hint: to the same ref
  ```

  

- push하기 전에 먼저 Remote 변경사항들을 통합하는 것을 원할 것

  ```bash
  You may want to first integrate the remote changes
  hint: (e.g., 'git pull ...') before pushing again.
  hint: See the 'Note about fast-forwards' in 'git push --help' for details.
  ```

  

- Remote에서 변경이 있을 경우 먼저 git pull을 할 것

  ```bash
  $ git pull origin master
  remote: Enumerating objects: 4, done.
  Unpacking objects: 100% (3/3), 683 bytes | 23.00 KiB/s, done.1/3)
  remote: Counting objects: 100% (4/4), done.
  remote: Compressing objects: 100% (2/2), done.
  remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
  From https://github.com/Junghyun-B/test
   * branch            master     -> FETCH_HEAD
     eb1044a..e6ee445  master     -> origin/master
  Merge made by the 'recursive' strategy.
   README.md | 1 +
   1 file changed, 1 insertion(+)
   create mode 100644 README.md
  ```

  

- Local에 update 됨 -> merge commit

  ```bash
  정현@□□□□-PC MINGW64 ~/Desktop/test (master)
  $ git log --oneline -3
  2c75020 (HEAD -> master) Merge branch 'master' of https://github.com/Junghyun-B/test
  3e10447 Update file
  e6ee445 (origin/master) Create README.md
  ```

  

- 이후에 git push

  ```bash
  정현@□□□□-PC MINGW64 ~/Desktop/test (master)
  $ git push origin master
  Enumerating objects: 6, done.
  Counting objects: 100% (6/6), done.
  Delta compression using up to 4 threads
  Compressing objects: 100% (4/4), done.
  Writing objects: 100% (4/4), 474 bytes | 47.00 KiB/s, done.
  Total 4 (delta 2), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (2/2), completed with 1 local object.
  To https://github.com/Junghyun-B/test.git
     e6ee445..2c75020  master -> master
  ```



### Git bash에서 vscode 연결 실행

- vscode 실행

  ```bash
  정현@□□□□-PC MINGW64 ~/Desktop
  $ code
  
  정현@□□□□-PC MINGW64 ~/Desktop
  $ git config --global core.editor "code --wait"
  
  정현@□□□□-PC MINGW64 ~/Desktop
  $ git config --global -l
  user.name=Junghyun Bang
  user.email=7304126@naver.com
  core.editor=code --wait
  ```

  

- 새로운 폴더창 열고 git bash 실행 후 git add

  ```bash
  정현@□□□□-PC MINGW64 ~/Desktop/test (master)
  $ touch test.txt
  
  정현@□□□□-PC MINGW64 ~/Desktop/test (master)
  $ git add .
  ```

  

- git commit 입력하면 vscode가 실행됨

  ```bash
  정현@□□□□-PC MINGW64 ~/Desktop/test (master)
  $ git commit
  [master 80786b6] Add Test feature
   1 file changed, 0 insertions(+), 0 deletions(-)
   create mode 100644 test.txt
  ```

  - vscode에서 commit 입력 후 저장하고 끄면 완료
    (별도의 특수문자 필요없이 커밋내용만 입력)



### 그 밖의 Git bash 명령어 (💥주의해서 사용할 것💥)

- add 취소 명령어

  ```bash
  $ git add .
  $ git restore --staged file.txt
  ```

  

- 복구하기

  ```bash
  $ git restore file.txt
  ```

  

- 커밋메시지 변경

  ```bash
  $ git commit --amend
  ```

  

- 커밋 삭제

  ```bash
  ($ git log --oneline)
  
  # 그냥 삭제해버림 기록이 안남음
  $ git reset --hard [커밋번호]
  
  # 되돌렸다는 커밋이 남아있음
  $ git revert [커밋번호]
  ```

  

- 모든 커밋 시점은 복원이 가능(되돌리기 가능)
  일반적으로 모든 작업을 할 때에는  커밋하면서 진행
  **간혹 작업 중 다른 것을 반영해야할 때**(stash)

  ```bash
  $ git stash
  ```

  **를 통해 임시공간에 보관 가능**
  이후 git pull을 통해 받아오고, 그 다음에 다시 **임시공간에서 꺼내서 작업 재진행**(stash pop)

  ```bash
  $ git pull origin master
  $ git stash pop
  ```

  

### ETC

- Shared : 내가 초대받은 깃허브
- Fork : 내가 초대받지 못한 깃허브 (-> Git clone -> Pull Request)

