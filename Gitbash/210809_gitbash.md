# 📌 Git Bash Orientation



## Command

| code                               | explanation               |
| ---------------------------------- | ------------------------- |
| ls<br />(list)                     | 파일의 목록을 확인        |
| pwd<br />(print working directory) | 현재 경로를 보여줌        |
| mkdir test<br />(make directory)   | test 디렉토리 생성        |
| cd                                 | 디렉토리 변경             |
| cd ..                              | 상위 디렉토리 이동        |
| cd .                               | 현재 디렉토리             |
| touch a.png                        | 0바이트의 a.png 파일 생성 |
| mv a.txt e.txt                     | a.txt를 e.txt로 변경      |



## Status

```bash
$ git status

On branch master

# 커밋이 될 변경사항들
# staging area에 있는 staged 상태의 파일들
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    b.txt

# staged(commit을 위한)가 아닌 변경사항들
# working directory에 있는 수정된 파일들 (기존에 커밋된 적이 있는 파일)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

# 트래킹 X 파일들
# 커밋이 된 적 없는 파일들
# working directory에 있음
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.docx
```

- untracked와 modified의 공통점 :  git add를 통해 staging area로 갈 수 있음


- untracked와 modified의 차이점 : commit이 된 적 있는가 (un~ : x / mo~ : o)




```bash
$ git add a.txt b.txt # 복수의 디렉토리
$ git add test_folder # 특정 폴더
$ git add c.txt #특정 파일
$ git add "*.txt" # 특정 확장자
```

- status : working directory와 staging area의 파일 상태를 볼 수 있음


- log : git directory(repository)의 버전 상태를 볼 수 있음




## Git 설정

- 사용자정보 : 커밋을 하기 위해 반드시 필요

  ```bash
  $ git config  --global -l
  user.name=Junghyun Bang
  user.email=7304126@naver.com
  ```



- **원격저장소 조회**

  ```bash
  $ git remote -v
  origin  https://github.com/Junghyun-B/test.git (fetch)
  origin  https://github.com/Junghyun-B/test.git (push)
  ```



- **원격저장소 추가**

  ```bash
  $ git remote add <원격저장소이름> <주소>
  $ git remote add origin https://github.com/<username>/<원격저장소이름>.git
  ```

  - 깃아, 원격저장소(`remote`)를 추가해줘(`add`).`origin`이라는 이름으로, `주소`를
  - 원격저장소가 이미 설정된 경우 설정이 되지 않음 (remote origin already exists)



- **원격저장소 삭제**

  ```bash
  $ git remote rm <원격저장소이름>
  ```



- **원격저장소 push**

  ```bash
  $ git push <원격저장소이름> master
  $ git push origin master
  Enumerating objects: 8, done.
  Counting objects: 100% (8/8), done.
  Delta compression using up to 4 threads
  Compressing objects: 100% (4/4), done.
  Writing objects: 100% (8/8), 658 bytes | 43.00 KiB/s, done.
  Total 8 (delta 0), reused 0 (delta 0), pack-reused 0
  To https://github.com/Junghyun-B/test.git
   * [new branch]      master -> master
  ```

  - git push origin에 master 브랜치를



- `-u` 옵션 : upstream 옵션
  - git push라고 명령을 하더라도 설정된 원격저장소에 브랜치를 push
  - git push -u origin master



## ETC

- README.md에서 b.png를 활용하기 위해서는?

  - 상대경로로 설정해두면 화질이 깨지지 않음

    ./images/markdown/b.png
