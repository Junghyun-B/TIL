# ๐ Git Bash Orientation



## Command

| code                               | explanation               |
| ---------------------------------- | ------------------------- |
| ls<br />(list)                     | ํ์ผ์ ๋ชฉ๋ก์ ํ์ธ        |
| pwd<br />(print working directory) | ํ์ฌ ๊ฒฝ๋ก๋ฅผ ๋ณด์ฌ์ค        |
| mkdir test<br />(make directory)   | test ๋๋ ํ ๋ฆฌ ์์ฑ        |
| cd                                 | ๋๋ ํ ๋ฆฌ ๋ณ๊ฒฝ             |
| cd ..                              | ์์ ๋๋ ํ ๋ฆฌ ์ด๋        |
| cd .                               | ํ์ฌ ๋๋ ํ ๋ฆฌ             |
| touch a.png                        | 0๋ฐ์ดํธ์ a.png ํ์ผ ์์ฑ |
| mv a.txt e.txt                     | a.txt๋ฅผ e.txt๋ก ๋ณ๊ฒฝ      |



## Status

```bash
$ git status

On branch master

# ์ปค๋ฐ์ด ๋  ๋ณ๊ฒฝ์ฌํญ๋ค
# staging area์ ์๋ staged ์ํ์ ํ์ผ๋ค
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    b.txt

# staged(commit์ ์ํ)๊ฐ ์๋ ๋ณ๊ฒฝ์ฌํญ๋ค
# working directory์ ์๋ ์์ ๋ ํ์ผ๋ค (๊ธฐ์กด์ ์ปค๋ฐ๋ ์ ์ด ์๋ ํ์ผ)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   a.txt

# ํธ๋ํน X ํ์ผ๋ค
# ์ปค๋ฐ์ด ๋ ์  ์๋ ํ์ผ๋ค
# working directory์ ์์
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        b.docx
```

- untracked์ modified์ ๊ณตํต์  :  git add๋ฅผ ํตํด staging area๋ก ๊ฐ ์ ์์


- untracked์ modified์ ์ฐจ์ด์  : commit์ด ๋ ์  ์๋๊ฐ (un~ : x / mo~ : o)




```bash
$ git add a.txt b.txt # ๋ณต์์ ๋๋ ํ ๋ฆฌ
$ git add test_folder # ํน์  ํด๋
$ git add c.txt #ํน์  ํ์ผ
$ git add "*.txt" # ํน์  ํ์ฅ์
```

- status : working directory์ staging area์ ํ์ผ ์ํ๋ฅผ ๋ณผ ์ ์์


- log : git directory(repository)์ ๋ฒ์  ์ํ๋ฅผ ๋ณผ ์ ์์




## Git ์ค์ 

- ์ฌ์ฉ์์ ๋ณด : ์ปค๋ฐ์ ํ๊ธฐ ์ํด ๋ฐ๋์ ํ์

  ```bash
  $ git config  --global -l
  user.name=Junghyun Bang
  user.email=7304126@naver.com
  ```



- **์๊ฒฉ์ ์ฅ์ ์กฐํ**

  ```bash
  $ git remote -v
  origin  https://github.com/Junghyun-B/test.git (fetch)
  origin  https://github.com/Junghyun-B/test.git (push)
  ```



- **์๊ฒฉ์ ์ฅ์ ์ถ๊ฐ**

  ```bash
  $ git remote add <์๊ฒฉ์ ์ฅ์์ด๋ฆ> <์ฃผ์>
  $ git remote add origin https://github.com/<username>/<์๊ฒฉ์ ์ฅ์์ด๋ฆ>.git
  ```

  - ๊น์, ์๊ฒฉ์ ์ฅ์(`remote`)๋ฅผ ์ถ๊ฐํด์ค(`add`).`origin`์ด๋ผ๋ ์ด๋ฆ์ผ๋ก, `์ฃผ์`๋ฅผ
  - ์๊ฒฉ์ ์ฅ์๊ฐ ์ด๋ฏธ ์ค์ ๋ ๊ฒฝ์ฐ ์ค์ ์ด ๋์ง ์์ (remote origin already exists)



- **์๊ฒฉ์ ์ฅ์ ์ญ์ **

  ```bash
  $ git remote rm <์๊ฒฉ์ ์ฅ์์ด๋ฆ>
  ```



- **์๊ฒฉ์ ์ฅ์ push**

  ```bash
  $ git push <์๊ฒฉ์ ์ฅ์์ด๋ฆ> master
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

  - git push origin์ master ๋ธ๋์น๋ฅผ



- `-u` ์ต์ : upstream ์ต์
  - git push๋ผ๊ณ  ๋ช๋ น์ ํ๋๋ผ๋ ์ค์ ๋ ์๊ฒฉ์ ์ฅ์์ ๋ธ๋์น๋ฅผ push
  - git push -u origin master



## ETC

- README.md์์ b.png๋ฅผ ํ์ฉํ๊ธฐ ์ํด์๋?

  - ์๋๊ฒฝ๋ก๋ก ์ค์ ํด๋๋ฉด ํ์ง์ด ๊นจ์ง์ง ์์

    ./images/markdown/b.png
