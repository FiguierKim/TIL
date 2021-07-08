# gitignore

> git으로 관리하고 싶지 않은 파일들의 리스트를 작성하여, 특정 파일들이 git에서 버전 관리를 하지 않도록 하는 것이다.

- 일반적으로 개인정보 및 특정 사람에게만 적용되는 환경들(개인 개발환경 관련)이 이 파일에 작성하여 관리된다.
- 개발환경 관련 파일들(.idea 등)은 버전관리가 될 필요도 없고 개인정보는 올려서는 안된다.

- `.gitignore` 파일을 만들어서 관리한다. (위치는 `.git` 파일과 동일한 곳)

- https://gitignore.io/
  - 본인 개발 환경에 대한 내용을 넣고 생성하면, 일반적으로 개발자들이 많이 쓰는 gitignore 문서를 제공

> 일반적으로 `git init` 후 첫 `add` 전 작성할 것

<br>

# branch command

* 브랜치 생성

  ```bash
  $ git branch 브랜치명
  ```

* 브랜치 목록

  ```bash
  $ git branch
  ```

* 브랜치 이동

  ```bash
  $ git checkout 브랜치명
  (브랜치명) $
  ```

* 브랜치 생성 + 이동

  ```bash
  $ git checkout -b 브랜치명
  ```

* 브랜치 병합

  ```bash
  (master) $ git merge 브랜치명
  ```

  > 반드시 `master` 브랜치에 `브랜치` 를 병합

* 브랜치 삭제

  ```bash
  $ git branch -d 브랜치명
  ```

- 브랜치 강제 삭제

  ```bash
  $ git branch -D 브랜치명
  ```

  > merge가 되지 않은 브랜치는 강제로 삭제해야 함
  >
  > ```bash
  > error: The branch 'hotfix' is not fully merged.
  > If you are sure you want to delete it, run 'git branch -D hotfix'.
  > ```

# reset vs revert

## reset

> https://git-scm.com/docs/git-reset
>
> "시계를 마치 과거로 돌리는 듯한 행위"
>
> 특정 커밋으로 되돌아가며 되돌아간 특정 커밋 이후의 커밋들은 모두 사라지며,
>
> 파일 상태는 옵션을 통해 결정한다.

<br>

**3가지 옵션**

1. `--soft`

   - 돌아가려는 커밋으로 되돌아가고,

   - 이후의 commit된 파일들을 `staging area`로 돌려놓음 (commit 하기 전 상태)
   - 즉, 다시 커밋할 수 있는 상태가 된다.

2. `--mixed`
   - 돌아가려는 커밋으로 되돌아가고,

   - 이후의 commit된 파일들을 `working directory`로 돌려놓음 (add 하기 전 상태)
   - 즉, unstage 된 상태로 남아있게 된다.
   - 기본값

3. `--hard`

- 돌아가려는 커밋으로 되돌아가고,
  - 이후의 commit된 파일들(`tracked 파일들`)은 모두 working directory에서 삭제한다.

- 단, Untracked 파일은 Untracked로 남는다.

```bash
# --hard 예시

$ git log --oneline
d56a232 (HEAD -> master) hello
7f6c24c foo & bar
006dc87 rename commit message
3551584 asdasd
71ccbf1 first


$ git reset --hard 3551584
HEAD is now at 3551584 asdasd


$ git log --oneline
3551584 (HEAD -> master) asdasd
71ccbf1 first


$ git status
On branch master
nothing to commit, working tree clean
```

- `reset`은 과거로 돌아가게 되면 돌아간 커밋 이후의 커밋은 모두 히스토리에서 사라진다.
- 커밋 히스토리가 바뀌기 때문에 다른 사람과  공유하는 브랜치에서 사용 시 충돌이 발생한다.
- 공유하는 브랜치에서 이전 커밋을 수정하고 싶을 때는 `git revert` 사용하기

<br>

---

<br>

## revert

> https://git-scm.com/docs/git-revert
>
> "특정 사건을 없었던 일로 만드는 행위"
>
> **이전 커밋 내역을 그대로 남겨둔 채 새로운 커밋을 생성**
>
> **커밋 히스토리 변경 없이 해당 커밋 내용만을 삭제한 상태의 새로운 커밋을 생성**

```bash
$ git log --oneline
7f6c24c (HEAD -> master) foo & bar
006dc87 rename commit message
3551584 asdasd
71ccbf1 first

# revert commit 편집기 실행
$ git revert 71ccbf1
Removing foo.txt
Removing bar.txt
[master 3b55051] Revert "first"
 2 files changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 bar.txt
 delete mode 100644 foo.txt

$ git log --oneline
3b55051 (HEAD -> master) Revert "foo & bar"
7f6c24c foo & bar # 히스토리는 남아있음
006dc87 rename commit message
3551584 asdasd
71ccbf1 first 
```

- 다른 사람과 공유하는 브랜치에서 이전 커밋을 수정하고 싶을 때 사용

- 커밋 히스토리가 바뀌지 않기 때문에 충돌이 발생하지 않음

<br>

---

![git-revert-vs-reset](/Users/hg/00_Inedit/05_Class/05_MultiCampus_K-digital/2_Git/TIL/02_gitignore.assets/git-revert-vs-reset.svg)